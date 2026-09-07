# Contact us

To contact us for help regarding integration, send us an email openbanking-support@zopa.com

When you onboard as a TPP and start using out APIs, we will retain your contact details so that you can be informed in the event of any outages or changes to our API specifications, as well as to contact you regarding any technical issues, unless you ask us not to do this. We recommend using a team email address over an individual contact.

## Reporting issues

When raising an issue, please include as much of the following as possible to help us investigate and respond quickly.

Please ensure any sensitive data or PII (such as customer names, account numbers, or access tokens) is redacted before sending.

**For all issues:**
- A description of the issue and the expected vs. actual behaviour
- Whether the issue is ongoing or has been resolved
- The `x-fapi-interaction-id` from the affected request(s)
- The approximate time and date the issue occurred
- The number of customers or requests impacted
- Whether the issue results in material detriment to customers — for example, are they unable to complete a journey or access a service, or is there a workaround available?

**For authorisation / redirect issues:**
- The device platform (iOS or Android)
- The Zopa app version installed on the affected device
- Whether the issue is reproducible and if so, steps to reproduce

**For API request/response issues:**
- The full request URL and method
- Relevant request headers
- The response status code received

**For consent-related issues:**
- The consent ID (`x-fapi-interaction-id` or consent ID from the response)
- The permissions requested in the consent
- Whether the consent was successfully authorised by the customer

Providing this information upfront will significantly reduce the time needed to diagnose and resolve your issue.
