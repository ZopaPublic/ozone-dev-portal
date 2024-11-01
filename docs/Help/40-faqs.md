# FAQs

## General

### What is Open Banking?

Open Banking is a reform, which mandates Zopa to enable the secure sharing of customer account data and initiate payments with registered third party providers (TPPs) provided the customer has given their consent.

Please find more information at [Open Banking](https://www.openbanking.org.uk/)


### What are our Open Banking APIs?

#### Account & Transactions
These read/write APIs provide the ability for approved/authorised account information service providers (AISPs) to access a customer’s (payment service user's) account and transaction information for domestic payment accounts (for Zopa this includes the Zopa Credit Card), only when the PSU grants consent. This API is developed according to the Open Banking Read/Write API Specifications, see [https://www.openbanking.org.uk/](https://www.openbanking.org.uk/)


### What are the roles a TPP can perform?

A TPP, Third Party Provider, can perform the following roles once they are registered with their National Competent Authority (NCA):

Account Information Service Provider (AISP)

Payment Initiation Service Provider (PISP)

Technical Service Provider (TSP)

Card Based Payment Instrument Issuer (CBPII)



## Read/Write APIs


### How can I access Zopa's Read/Write APIs?
As a TPP, in order to access our Read/Write APIs, you need to be enrolled with Open Banking (Enrolling Onto Open Banking Guide) and registered with the Financial Conduct Authority (FCA) as an AISP.

This will then enable you to access our APIs through the Zopa Developer Portal

### As a Third Party Provider, is there somewhere I can test prototype Open Banking Solutions?
 Yes, Zopa has a test facility [../40-sandbox.md](Sandbox) available through our Developer Portal.

Check out our [../20-getting-started.md](Get Started) guide for a step by step guide on how to start testing with our Sandbox APIs.


### Where are the specifications you have used to build your current APIs?
There are full specifications provided by OBL available on their [https://openbankinguk.github.io/read-write-api-site3/v4.0/](Developer Zone) from which we’ve built our APIs.

## Response Codes

### I am getting a 401 unauthorized response when invoking /token endpoints
(1) Make sure you have registered your SSA in Zopa Developer Portal and the subscription of the Accounts Service Provider API and/or Payments Service Provider API is approved by Zopa

(2) Make sure you are following client_secret_post for the OIDC calls

(3) Make sure you are sending client_id & client_secret as part of x-www-form-urlencoded body parameter

### I am getting an SSL Handshake Error when trying to invoke /token or resource endpoints.
Check that you are using the correct network certificate signed by Open Banking to establish the TLS MA connection