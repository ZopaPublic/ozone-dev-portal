# AISP API Overview

Please note, currently only **Zopa Credit Card** accounts support access via AIS.

## Base URL
The base URL for all AIS APIs is: `https://rs1.openbanking.zopa.com/open-banking/v3.1/aisp/**`

## Account Access Consents
[Account Access Consents API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Account_Access)

## Accounts
[Accounts API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Accounts)

Please note, currently only **Zopa Credit Card** accounts support access via AIS.

## Balances
[Balances API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Balances)

Balances shown in this endpoint provide the `InterimAvailable` value.

`InterimAvailable` balance is the value displayed to our members within the Zopa apps.

## Transactions
[Transactions API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Transactions)

Pagination is supported on GET /accounts/{AccountId}/transactions end point with a page size of 100 transactions.


## Offers
[Offers API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Offers)


## Parties
[Parties API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Parties)


## Statements
[Statements API](/perry/developer/documentation?resource=dev-ui-portal&document=swagger/account-info-openapi.yaml#operations-tag-Statements)

