# Account Information Services API Overview

Please note, only the **Zopa Credit Card** and **Zopa bank account** (Current Account) support access via AIS.

### Base URL
The base URL for all AIS APIs is: `https://rs1.openbanking.zopa.com/open-banking/v4.0/aisp/**`

### Auth URL
We currently only support redirect via a deeplink to the Zopa mobile app - this deeplink is different depending on the type of consents (AIS or PIS) and needs to be constructed as follows: 

- AIS Authorisation URL: `zopa://consent-access-request?client_id={{ the client ID }}&response_type=code&scope=openid%20accounts&request={{the JWT token}}`

### Usage
According to [Article 36 of the UK-RTS](https://www.handbook.fca.org.uk/techstandards/PS/2021/2021_01/chapter-v/section-2/040.html), TPPs are entitled to access information via AIS whenever the payment service user is actively requesting this data; otherwise, this should be no more than four times in a 24-hour period.

Further to this, when the customer is not present (i.e. without SCA), TPPs may access only the endpoints exempt under UK-RTS [Article 10a](https://www.handbook.fca.org.uk/techstandards/PS/2021/2021_01/chapter-iii/10A.html), that is:
- GET /accounts
- GET /accounts/{AccountId}
- GET /accounts/{AccountId}/balances
- GET /accounts/{AccountId}/transactions - 90 days without SCA, unlimited with SCA.

### Account Access Consents
[Account Access Consents API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Account_Access)

### Accounts
[Accounts API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Accounts)

Provides details of accounts the customer has consented to share. Please note, currently only the **Zopa Credit Card** and **Zopa bank account** (Current Account) support access via AIS, and so any other Zopa accounts a customer may hold (such as Savings accounts) cannot be shared this way.

### Balances
[Balances API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Balances)

Balances shown in this endpoint provide the Interim Available (`ITAV`) balance type, as well as the Credit Limit for Zopa Credit Cards.

The Interim Available balance is the value displayed to our customers within the Zopa app.

### Transactions
[Transactions API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Transactions)

Pagination is supported on `GET /accounts/{AccountId}/transactions` end point with a page size of 100 transactions.

##### Proprietary Bank Transaction Codes
The proprietary bank transaction codes returned vary between Zopa products. Details of these can be found [here](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=docs/API%20Overview/pbtc.md)

### Beneficiaries
[Beneficiaries API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Beneficiaries)

Please note - this endpoint will only return data for the **Zopa bank account** (Current Account). If this endpoint is called for the **Zopa Credit Card** then you will receive a `200` status code with no data. This indicates that the request was successful, but there is no applicable data for the requested product.

### Direct Debits
[Direct Debits API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Direct_Debits)

Please note - this endpoint will only return data for the **Zopa bank account** (Current Account). If this endpoint is called for the **Zopa Credit Card** then you will receive a `200` status code with no data. This indicates that the request was successful, but there is no applicable data for the requested product.

### Standing Orders
[Standing Orders API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Standing_Orders)

Please note - this endpoint will only return data for the **Zopa bank account** (Current Account). If this endpoint is called for the **Zopa Credit Card** then you will receive a `200` status code with no data. This indicates that the request was successful, but there is no applicable data for the requested product.

### Offers
[Offers API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Offers)

Please note - this endpoint will only return data for the **Zopa Credit Card**. If this endpoint is called for the **Zopa bank account** (Current Account) then you will receive a `200` status code with no data. This indicates that the request was successful, but there is no applicable data for the requested product.

### Party
[Party API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Party)

### Statements
[Statements API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Statements)

Please note - this endpoint will only return data for the **Zopa Credit Card**, if this endpoint is called for the **Zopa bank account** (Current Account) then you will receive a `200` status code with no data. This indicates that the request was successful, but there is no applicable data for the requested product.