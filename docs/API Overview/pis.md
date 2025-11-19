# Payment Initiation Services API Overview

## Base URL
The base URL for all PIS APIs is: `https://rs1.openbanking.zopa.com/open-banking/v4.0/pisp/**`

### Auth URL
We currently only support redirect via a deeplink to the Zopa mobile app - this deeplink is different depending on the type of consents (AIS or PIS) and needs to be constructed as follows: 

- PIS Authorisation URL: `zopa://open-banking/pis-single-payment-consent?client_id={{ the client ID }}&response_type=code&scope=openid%20payments&request={{the JWT token}}`

## Supported Payment Types
The Zopa API currently only supports:
- Domestic Payments
- Domestic Standing Orders

These endpoints are only supported for users who have a Zopa Bank Account (Current Account).

The Zopa API __does not__ currently support:
- Domestic Scheduled Payments (however you can use the Domestic Standing Orders API with the frequency set to `ADHO` to achieve a simlar goal)
- International payments
- File & Bulk payments
- `payment-details` end-points

The swagger for our PIS API can be found [here](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/payment-initiation-openapi.yaml)


# Supported Parameters

## Domestic Payments
### Amount Limits
The payment amount is set using the `InstructedAmount/Amount` field.

Payments have the following limits which are aligned with the limits applied in the Zopa app:
- Payments to Zopa Smart Saver or to a Verified Self Owned Account (aka Nominated Bank Account) - £250,000 daily limit
- Payments to any other account - £10,000 daily limit, £30,000 weekly limit

These limits apply across all outbound transactions (not just payments initiated via PIS). Zopa suggest PISPs notify the PSU that the same limits apply as in their Zopa app. It is possible from time to time that `domestic-payment-consents` is authorised, but the payment initiation fails due to account limits.

### Currency
- `InstructedAmount/Currency` must be `GBP`

### Payment References
The payment reference is specified using `RemittanceInformation/Structured/CreditorReferenceInformation/Reference`. This field is **mandatory**.

The reference **must** also:
- Be 18 characters or less
- Match the regex: `^[a-zA-Z0-9\\/\\-?:().,’+\\s#=!\"%&*<>;{@\\r\\n]*\$`
- Not contain a PAN (a 16 digit number passing a LUHN check)

Payment requests with references which do not conform to the above will be rejected. The PISP may also opt to populate reference field on behalf of the PSU.

### Local Instrument
The only `LocalInstrument` supported is Faster Payment scheme. This field, if specified, must have the value `UK.OBIE.FPS`. If anything other than this is sent by PISP in consent payload then an error will be returned.

However, this field is not mandatory so we suggest PISP simply not include this field and Zopa will stage consent as a Faster Payment.

### Scheme Name
The only supported `Account.SchemeName` is `UK.OBIE.SortCodeAccountNumber` for both `DebtorAccount` and `CreditorAccount`. Any other enum provided will return error.

## Standing Orders
### Currency
- `InstructedAmount/Currency` must be `GBP`

### Payment References
The payment reference is specified using `RemittanceInformation/Structured/CreditorReferenceInformation/Reference`. This field is **mandatory**.

The reference **must** also:
- Be 18 characters or less
- Match the regex: `^[a-zA-Z0-9\\/\\-?:().,’+\\s#=!\"%&*<>;{@\\r\\n]*\$`
- Not contain a PAN (a 16 digit number passing a LUHN check)

Payment requests with references which do not conform to the above will be rejected. The PISP may also opt to populate reference field on behalf of the PSU.

### Scheme Name
The only supported `Account.SchemeName` is `UK.OBIE.SortCodeAccountNumber` for both `DebtorAccount` and `CreditorAccount`. Any other enum provided will return error.

### First and Final Payment Amounts
We only support Standing Orders with a *single fixed amount*. Consents where the amounts in `FirstPaymentAmount`, `FinalPaymentAmount` and `RecurringPaymentAmount` differ will be rejected.

### Frequency
We only support Standing Orders with the following Frequencies:
- `ADHO` (Adhoc)
- `DAIL` (Daily)
- `WEEK` (Weekly)
- `FRTN` (Fortnightly)
- `MNTH` (Monthly)
- `YEAR` (Yearly)
Attempts to initiate a mandate with a different frequency will fail.

### Execution Notes
If a monthly mandate is scheduled to occur on e.g. 31st of each month, in months where this day does not occur, the payment will be made the preceding day (i.e. the 30th). If a Standing Order is scheduled with a date that does not exist (e.g. 30th February) the request will error.

## JWS Usage Guidance

All payment initiation requests to Zopa must be protected using a detached JSON Web Signature (JWS) as per the Open Banking standard. This ensures the integrity and authenticity of the payment payload.

**Key requirements:**
- The JWS must be generated using the signing key registered with Zopa.
- The required algorithm is `PS256` (RSASSA-PSS using SHA-256). Ensure your signing library supports this algorithm.
- The `x-jws-signature` header must be included in all relevant API requests, containing the detached JWS for the request body.
- The payload must not be altered after signing; any modification (including whitespace or key order) will result in signature validation failure.
- Canonicalise the JSON payload before signing (remove extra spaces, ensure consistent key ordering if required by your library).
- The JWS must be detached: do not include the payload in the JWS itself—sign the payload and send only the signature in the `x-jws-signature` header.
- Set the `Content-Type` header to `application/json`.
- Double-check that the payload sent in the request matches exactly what was signed.
- If you receive a signature validation error, compare the raw payload you sent with what you signed—any difference will cause failure.
- If the JWS is invalid or missing, the request will be rejected with an error.
