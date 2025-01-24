# Developer Documentation for Modified Customer Interface

## Overview
We support connections via our Modified Customer Interface as a contingency mechanism for when the main dedicated interface (i.e. the APIs) are down, this may be used in the event the dedicated interface faces significant disruption. We will notify the onboarded TPPs through the contact details provided, and also via the [Outages Log](/perry/developer/documentation?resource=euhub-zopa-portal-new&document=docs/50-planned-updates.md) if we have had to invoked the contingency mechanism. This document provides essential information for using the interface.

To access the customer interface, use the following URL: https://mci.openbanking.zopa.com/

## Accessing the MCI

#### UK TPPs
Obtain an Open Banking website authentication certificate (OBWAC) for UK based TPPs – As a first step towards accessing MCI API, please obtain a valid OBWAC certificated from Open Banking.

#### Non UK TPPs
Obtain Certificate (QWAC) and Onboard with Open Banking for non UK based TPPs - As a first step towards accessing MCI API, please obtain a valid QWAC certificate from a recognised QTSP.

Once you have the required certificates please contact us using  openbanking-support@zopa.com to onboard.

Once you have the QWAC or OBWAC and are registered, the MCI API provides the ability to access our Credit Card web channel. On successful validation of the client details and QWAC or OBWAC as relevant, you will be redirected towards the channel.

Ensure that all certificates are up-to-date and correctly installed on your systems.

## Contact Information
For further guidance or support, please reach out to us:
- **Email**: openbanking-support@zopa.com
