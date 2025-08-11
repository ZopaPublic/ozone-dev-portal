# FAQs
## General

### What is Open Banking?

Open Banking is a reform, which mandates Zopa to enable the secure sharing of customer account data and initiate payments with registered third party providers (TPPs) provided the customer has given their consent.

Please find more information at [Open Banking](https://www.openbanking.org.uk/)


### What are our Open Banking APIs?

#### Account & Transactions
These read/write APIs provide the ability for approved/authorised account information service providers (AISPs) to access a customer’s (payment service user's) account and transaction information for domestic payment accounts (for Zopa this includes the Zopa Credit Card and Zopa bank account), only when the user grants consent. This API is developed according to the Open Banking Read/Write API Specifications, see: [https://www.openbanking.org.uk/](https://www.openbanking.org.uk/)

### Payment Initiation

These read/write APIs provide the ability for authorised payment initiation service providers (PISPs) to initiate domestic payments only when the PSU grants consent. This API is developed according to the Open Banking Read/Write API Specifications, see [https://www.openbanking.org.uk/](https://www.openbanking.org.uk/)


### What are the roles a TPP can perform?

A TPP, Third Party Provider, can perform the following roles once they are registered with their National Competent Authority (NCA):

- Account Information Service Provider (AISP)
- Payment Initiation Service Provider (PISP)
- Technical Service Provider (TSP)
- Card Based Payment Instrument Issuer (CBPII)


## Read/Write APIs

### How can I access Zopa's Read/Write APIs?
As a TPP, in order to access our Read/Write APIs, you need to be enrolled with Open Banking and registered with the Financial Conduct Authority (FCA) as an AISP. This will then enable you to access our APIs.

### As a Third Party Provider, is there somewhere I can test prototype Open Banking Solutions?
 Yes, Zopa has a test facility [Sandbox](../40-sandbox.md) available through our Developer Portal.

Check out our [Get Started](../20-getting-started.md) guide for a step by step guide on how to start testing with our Sandbox APIs.


### Where are the specifications you have used to build your current APIs?
There are full specifications provided by OBL available on their [website](https://openbankinguk.github.io/read-write-api-site3/v4.0/) from which we’ve built our APIs.

## Response Codes

### I am getting a 401 unauthorised response when invoking /token endpoints
(1) Make sure you have your SSA is registered and the subscription of the Accounts Service Provider API and/or Payments Service Provider API is approved by Zopa. To do this please contact openbanking-support@zopa.com

(2) Make sure you are following client_secret_post for the OIDC calls

(3) Make sure you are sending client_id & client_secret as part of x-www-form-urlencoded body parameter

### I am getting an SSL Handshake Error when trying to invoke /token or resource endpoints.
Check that you are using the correct network certificate signed by Open Banking to establish the TLS MA connection