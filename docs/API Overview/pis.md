# Payment Initiation Services API Overview

## Base URL
The base URL for all AIS APIs is: `https://rs1.openbanking.zopa.com/open-banking/v4.0/pisp/**`

## Supported Payment Types
The Zopa API currently only supports:
- Domestic Payments

The Zopa API __does not__ currently support:
- Domestic Scheduled Payments
- Domestic Standing Orders
- International payments
- File & Bulk payments
- `payment-details` end-points

The swagger for our PIS API can be found [here](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/payment-initiation-openapi.yaml)

## Supported Parameters
The following apply to all domestic payment consents:

### Amount Limits
The payment amount is set using the `InstructedAmount/Amount` field.

Payments have the following limits which are aligned with the limits applied in the Zopa app:
- Payments to Zopa Smart Saver or to a Verified Self Owned Account (aka Nominated Bank Account) - £250,000 daily limit
- Payments to any other account - £10,000 daily limit, £20,000 weekly limit

Zopa suggest PISPs notify the PSU that the same limits apply as in their Zopa app. It is possible from time to time that `domestic-payment-consents` is authorised, but the payment initiation fails due to account limits.

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