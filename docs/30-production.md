# Production

Below are the paths of our well-known endpoints for the production environment.

Our production authorisation server uses the strict profile defined above and testable in the Sandbox.

## Onboarding
We do not currently support Dynamic Client Registration.

Please contact our Open Banking support team to be onboarded.

Contact email: openbanking-support@zopa.com

We will also retain your contact details so that you can be informed in the event of any outages or changes to our API specification, as well as to contact you regarding any technical issues. We recommend using a team email address over an individual contact.

## Authorisation Server URLs
- OIDC Well Known endpoint: `https://auth1.openbanking.zopa.com/.well-known/openid-configuration`
- baseUrl: `https://auth1.openbanking.zopa.com/`
- Authorisation URL (app only): `zopa://consent-access-request?client_id={{ the client ID }}&response_type=code&scope=openid%20accounts&request={{the JWT token}}`

## Resource Server URLs
- Account Information Services API: https://rs1.openbanking.zopa.com/open-banking/v4.0/aisp/**

## Tokens
Our refresh tokens last one year, after this TPPs will need to generate a new consent in order to get a new refresh token.