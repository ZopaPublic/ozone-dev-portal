# Getting started

## Onboarding
We do not currently support Dynamic Client Registration.

Please contact our Open Banking support team to be onboarded.

Contact email: openbanking-support@zopa.com

We will also retain your contact details so that you can be informed in the event of any outages or changes to our API specification, as well as to contact you regarding any technical issues. We recommend using a team email address over an individual contact.

## Production security profile

As defined further in the Zopa Open Banking API Specification

- ID Token Signing Algorithm: `PS256`
- Response Types: `code id_token`
- Request Object Signing Algorithms: `PS256`
- Token Endpoint Auth Singing Algorithms: `PS256`
- Token Endpoint Auth Methods: `private_key_jwt`, `tls_client_auth`

>For private_key_jwt - the `aud` claim is the url of the token endpoint as specified in OIDC client authentication.

> The request object used in OIDC flows the aud claim is the issuer url from the Zopa ASPSP .wellknown endpoint: https://auth1.openbanking.zopa.com/.well-known/openid-configuration

> Note: Our Sandbox API also offers less strict profiles to assist with integration testing. See below for more details.

## Certificate Support

### OB Transport & OB Signing Certificates

We recommend that TPPs use OB Transport and OB Signing certificates where possible. TPPs can use their QWACs and QSeals to onboard to the OBL directory and generate these certificates.

### OB WAC & OB Seal

We support the use of OBWAC and OBSeal on our production and sandbox environments. TPPs can use their QWACs and QSeals to onboard to the OBL directory and generate these certificates.

### QWACs

We support the use of QWACs, but this is not our recommended approach. TPPs facing issues onboarding with QWACs should contact our support desk. Please attach a pem file of the certificate to your support ticket.

### QSeal

We support the use of QSeals that have been attached to your software statement in the OB Directory.
