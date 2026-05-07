# Production

## OIDC Discovery

The OIDC discovery documents describe the supported parameters for each environment:
- Production: `https://auth1.openbanking.zopa.com/.well-known/openid-configuration`
- Sandbox: `https://auth1.openbanking-sandbox.zopa.com/.well-known/openid-configuration`

Our production environment conforms to FAPI 1.0 Advanced. Sandbox offers less strict profiles to assist with integration testing — always verify your integration against the production discovery document before going live.

## Authorisation URL

The authorisation endpoint is the one parameter that cannot be derived from the discovery document. Rather than a standard HTTPS endpoint, we use `zopa://` deeplinks to redirect the PSU into the Zopa mobile app. The deeplink differs by consent type:

- **AIS:** `zopa://consent-access-request?client_id=<client_id>&response_type=code%20id_token&scope=openid%20accounts&request=<signed_JWT>`
- **PIS Single Payment:** `zopa://open-banking/pis-single-payment-consent?client_id=<client_id>&response_type=code%20id_token&scope=openid%20payments&request=<signed_JWT>`
- **PIS Standing Order:** `zopa://open-banking/pis-standing-order-consent?client_id=<client_id>&response_type=code%20id_token&scope=openid%20payments&request=<signed_JWT>`

> **Note:** The `/o3/v1.0/auth-code-url` endpoint is a convenience helper available on sandbox only. It builds the request object server-side using `alg=none` and **must not be used in production** — it does not support PS256 and will return a 500 error if attempted.

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
  "response_type": "code id_token",
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
  "response_type": "code id_token",
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
> - Using `response_type: "code"` — production only supports `code id_token` as required by FAPI 1.0 Advanced. Sandbox accepts both, so this error only surfaces when moving to production.
> - Including a `userinfo` claims block or `acr` — these are not required

## Resource Server URLs

- Account Information Services API: `https://rs1.openbanking.zopa.com/open-banking/v4.0/aisp/**`
- Payment Initiation Services API: `https://rs1.openbanking.zopa.com/open-banking/v4.0/pisp/**`

> **Note for PISPs:** All payment initiation requests must include a detached JWS signature in the `x-jws-signature` header. This is not required for AIS requests. See the [PIS API Overview](/perry/developer/documentation?resource=euhub-zopa-portal&document=docs/API%20Overview/pis.md) for full details.

## Dynamic Client Registration

Our API supports dynamic client registration. We only trust Software Statement Assertions (SSAs) issued by the Open Banking Directory provided by Open Banking Limited. eIDAS certificates are supported via onboarding to the Open Banking Directory.

The registration endpoint is advertised in the OIDC discovery document via the `registration_endpoint` claim.

The `aud` claim used in the outer JWT of a DCR request is the Open Banking Limited issued `org_id` (as documented in the OBL DCR v3.2 standard).

## Production Security Profile

- ID Token Signing Algorithm: `PS256`
- Response Types: `code id_token`
- Request Object Signing Algorithms: `PS256`
- Token Endpoint Auth Signing Algorithms: `PS256`
- Token Endpoint Auth Methods: `private_key_jwt`, `tls_client_auth`

For `private_key_jwt`, the `aud` claim is the URL of the token endpoint as specified in OIDC client authentication.

For the request object, the `aud` claim is the `issuer` value from the OIDC discovery document (`https://auth1.openbanking.zopa.com`). See the Authorisation URL section above for details on constructing the deeplinks.

## Certificate Support

### OB WAC & OB Seal

We support OBWAC and OBSeal on both production and sandbox. TPPs can use their QWACs and QSeals to onboard to the OBL directory and generate these certificates.

### QWACs

We support QWACs, but this is not our recommended approach. TPPs facing issues onboarding with QWACs should contact our support desk with a PEM file of the certificate attached.

### QSeal

We support QSeals that have been attached to your software statement in the OB Directory.

## Tokens

Refresh tokens are valid for one year. After expiry, TPPs will need to generate a new consent to obtain a new refresh token.
