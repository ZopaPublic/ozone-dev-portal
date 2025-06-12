# Account Information Services API Overview

Please note, currently only the **Zopa Credit Card** and **Zopa bank account (current account)** support access via AIS.

## Base URL
The base URL for all AIS APIs is: `https://rs1.openbanking.zopa.com/open-banking/v4.0/aisp/**`

## Account Access Consents
[Account Access Consents API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Account_Access)

## Accounts
[Accounts API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Accounts)

Provides details of accounts the customer has consented to share. Please note, currently only the **Zopa Credit Card** and **Zopa bank account (current account)** support access via AIS, and so any other Zopa accounts a customer may hold (such as Savings accounts) cannot be shared this way.

## Balances
[Balances API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Balances)

Balances shown in this endpoint provide the Interim Available (`ITAV`) balance type, as well as the Credit Limit for Zopa Credit Cards.

The Interim Available balance is the value displayed to our customers within the Zopa app.

## Transactions
[Transactions API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Transactions)

Pagination is supported on `GET /accounts/{AccountId}/transactions` end point with a page size of 100 transactions.

##### Proprietary Bank Transaction Codes
The proprietary bank transaction codes returned vary between Zopa products. Details of these can be found [here](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=docs/API%20Overview/pbtc.md)

## Offers
[Offers API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Offers)

Please note - this endpoint is only supported by the **Zopa Credit Card**.


## Party
[Party API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Party)


## Statements
[Statements API](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=swagger/account-info-openapi.yaml#operations-tag-Statements)

Please note - this endpoint is only supported by the **Zopa Credit Card**.