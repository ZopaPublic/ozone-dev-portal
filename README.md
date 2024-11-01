# README #

This repository contains the content for the Zopa openbanking developer portal. This portal
will primarily used by third party developers (TPP developers) to consume the openbanking APIs
exposed by ozone  (for Zopa).

This repository can be used to tailor the content presented to the third party developers including
branding.
### How this repository is used ###

This repository is pulled by ozone and used to refresh the content being displayed on the developer portal.
The developer portal is maintained by ozone, this repository provides the content to be displayed on the portal.

If the API spec is changed, it is expected to update the swagger definitions checked into this repository.

```
Content placeholders
The following placeholders can be used for find/replace operations:

Find:     openbanking-support@zopa.com
Replace:  contact@prod-email-domain.com

Find:     openbanking.zopa.com
Replace:  api.zopa.eu-hub-prod.ozoneapi.co.uk

Find:     openbanking-sandbox.zopa.com
Replace:  sandbox.zopa.eu-hub-prod.ozoneapi.co.uk

Find:     {bank_name}
Replace:  Zopa

Find:     resource=dev-ui-portal
Replace   branch-name

```

