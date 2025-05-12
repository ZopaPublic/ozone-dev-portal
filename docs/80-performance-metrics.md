# Quarterly Availability and Performance Metrics

## Overview
The figures below provide insight into our performance and availability regarding our Open Banking APIs. 

## Definitions

### Percentage Uptime
Availability of each dedicated interface is reported as a percentage of uptime. Percentage uptime as 100% minus the percentage downtime. The calculation for percentage downtime for each interface is outlined below:
#### Dedicated Interface (Open Banking APIs)
- Percentage downtime using the total number of seconds the dedicated interface was down in a 24-hour period starting and ending at midnight;
- We count the interface as 'down' when five consecutive requests for access to information for the provision of account information services  are not replied to within a total timeframe of 30 seconds, irrespective of whether these requests originate from one or multiple AISPs. In such case, Zopa will calculate downtime from the moment it has received the first request in the series of five consecutive requests that were not replied to within 30 seconds, provided that there is no successful request in between those five requests to which a reply has been provided.
#### PSU Interface (Mobile App)
- Percentage downtime is calculated using the % of minutes in a day where the average technical error rate was greater than 5%

### Average Response Time
Performance will be reported for each interface based on the daily average (median) time in milliseconds.
#### Dedicated Interface (Open Banking APIs)
- The median time taken for Zopa to provide the account information service provider (AISP) the information requested.
#### PSU Interface (Mobile App)
- The median time taken for Zopa to respond to payment service user requests, measured in milliseconds.

## Data


- [Q4 2024](/assets/performance_pdfs/2024Q4.pdf)
- [Q1 2025](/assets/performance_pdfs/2025Q1.pdf)