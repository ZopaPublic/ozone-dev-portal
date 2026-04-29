# Production

## Authorisation Server URLs
- OIDC Well Known endpoint: `https://auth1.openbanking.zopa.com/.well-known/openid-configuration`
- baseUrl: `https://auth1.openbanking.zopa.com/`

## Authorisation URL

We currently only support redirect via a deeplink to the Zopa mobile app. Unlike most ASPSPs which use a standard HTTPS authorisation endpoint, our authorisation URLs use a custom `zopa://` deeplink scheme to redirect the PSU into the Zopa mobile app.

> **Note:** The `/o3/v1.0/auth-code-url` endpoint is a convenience helper available on sandbox only to assist with testing. It builds the request object server-side using `alg=none` and **must not be used in production** — it does not support PS256 and will return a 500 error if attempted.

The deeplink format differs by consent type:

- **AIS:** `zopa://consent-access-request?client_id=<client_id>&response_type=code&scope=openid%20accounts&request=<signed_JWT>`
- **PIS Single Payment:** `zopa://open-banking/pis-single-payment-consent?client_id=<client_id>&response_type=code&scope=openid%20payments&request=<signed_JWT>`
- **PIS Standing Order:** `zopa://open-banking/pis-standing-order-consent?client_id=<client_id>&response_type=code&scope=openid%20payments&request=<signed_JWT>`

### Request Object JWT

The `request` parameter must be a **PS256-signed JWT** constructed using your registered private signing key.

The scope must include `openid` in both the deeplink URL and the JWT payload — the value depends on the consent type:
- AIS: `openid accounts`
- PIS: `openid payments`

**JWT Header:**
```json
{
  "alg": "PS256",
  "kid": "<your-signing-key-kid>",
  "typ": "JWT"
}
```

**JWT Payload — AIS example:**
```json
{
  "iss": "<your_client_id>",
  "aud": "https://auth1.openbanking.zopa.com",
  "response_type": "code",
  "client_id": "<your_client_id>",
  "redirect_uri": "<your_registered_redirect_uri>",
  "scope": "openid accounts",
  "state": "<unique_state>",
  "nonce": "<unique_nonce>",
  "nbf": <unix_timestamp_now>,
  "exp": <unix_timestamp_now + 500>,
  "claims": {
    "id_token": {
      "openbanking_intent_id": {
        "value": "<your_ais_consent_id>",
        "essential": true
      }
    }
  }
}
```

**JWT Payload — PIS example:**
```json
{
  "iss": "<your_client_id>",
  "aud": "https://auth1.openbanking.zopa.com",
  "response_type": "code",
  "client_id": "<your_client_id>",
  "redirect_uri": "<your_registered_redirect_uri>",
  "scope": "openid payments",
  "state": "<unique_state>",
  "nonce": "<unique_nonce>",
  "nbf": <unix_timestamp_now>,
  "exp": <unix_timestamp_now + 500>,
  "claims": {
    "id_token": {
      "openbanking_intent_id": {
        "value": "<your_payment_consent_id>",
        "essential": true
      }
    }
  }
}
```

> **Common mistakes:**
> - Using `scope: "payments"` or `scope: "accounts"` — `openid` must always be included
> - Using `aud: "https://as1.openbanking.zopa.com"` — the correct value is `https://auth1.openbanking.zopa.com`
> - Including a `userinfo` claims block or `acr` — these are not required

## Resource Server URLs
- Account Information Services API: https://rs1.openbanking.zopa.com/open-banking/v4.0/aisp/**
- Payment Initiation Services API: https://rs1.openbanking.zopa.com/open-banking/v4.0/pisp/**

## Dynamic Client Registration

Our API allows dynamic client registration in order to create a valid client that is able to use our Authorisation Server. We only trust Software Statement Assertions (SSAs) issued by the Open Banking Directory provided by Open Banking Limited. eIDAS certificates are supported via onboarding to the Open Banking Directory (as discussed in more detail below).

The url of the registration endpoint is advertised on our OIDC Discovery Endpoints using the registration_endpoint claim.

The `aud` claim used in the outer JWT of a Dynamic Client Registration request is the Open Banking Limited issued `org_id` (as documented in the Open Banking Limited DCR v3.1 standard).

## Production security profile

As defined further in the Zopa Open Banking API Specification

- ID Token Signing Algorithm: `PS256`
- Response Types: `code id_token`
- Request Object Signing Algorithms: `PS256`
- Token Endpoint Auth Signing Algorithms: `PS256`
- Token Endpoint Auth Methods: `private_key_jwt`, `tls_client_auth`

>For private_key_jwt - the `aud` claim is the url of the token endpoint as specified in OIDC client authentication.

> The request object used in OIDC flows the aud claim is the issuer url from the Zopa ASPSP .wellknown endpoint: `https://auth1.openbanking.zopa.com/.well-known/openid-configuration` - though please see above for details of our authorisation URLs which require TPPs to construct deeplinks.

> Note: Our Sandbox API also offers less strict profiles to assist with integration testing.

## Certificate Support

### OB WAC & OB Seal

We support the use of OBWAC and OBSeal on our production and sandbox environments. TPPs can use their QWACs and QSeals to onboard to the OBL directory and generate these certificates.

### QWACs

We support the use of QWACs, but this is not our recommended approach. TPPs facing issues onboarding with QWACs should contact our support desk. Please attach a pem file of the certificate to your support ticket.

### QSeal

We support the use of QSeals that have been attached to your software statement in the OB Directory.

## Tokens
Our refresh tokens last one year, after this TPPs will need to generate a new consent in order to get a new refresh token.
