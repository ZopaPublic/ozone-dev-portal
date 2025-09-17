## Planned updates and outages
| Date        | Summary        | Endpoints        | Duration |
|-------------|----------------|------------------|----------|
|             |                |                  |          |


## Known Issues and Resolutions
| Issue Identified | Summary                                                                                                                                      | Endpoints                                 | Start Date | Resolution Date |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|------------|-----------------|
| 17/09/2025       | We became aware of an issue affecting our AIS API. Specifically, credit card transaction data has been truncated to only return the most recent 200 transactions. | GET /accounts/{AccountId}/transactions    | 04/12/2024 |                 |

## Change Logs

| Date       | Changes                                                                                  |
|------------|------------------------------------------------------------------------------------------|
|04/12/2024  |Added AIS support for the Zopa credit card.   |
|06/06/2025  |Added support for Accounts, Balance, and Transactions endpoints for Zopa bank accounts.   |
|24/06/2025  |Added support for Direct Debit, Standing Order and Beneficiaries AIS endpoints for Zopa bank accounts.<br>Added support for Single Domestic Payments via PIS.
|11/08/2025  |Added support for registration via DCR.
|05/09/2025  |Added support for Domestic Standing Order initiation via PIS.
