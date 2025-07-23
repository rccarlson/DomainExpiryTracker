# Domain Expiration Checker

## Overview

This is a web-based application that allows users to check the registration and expiration dates of internet domains using the ICANN RDAP API. Users can add domains individually or in bulk, view them in a sortable table, and update their information with rate-limited API queries. The application persists data using the browser's local storage.

[Link to live page](https://rccarlson.github.io/DomainExpiryTracker/)

## API Details

The application uses the ICANN RDAP API in two steps:

1. TLD Services
   - Fetches `https://data.iana.org/rdap/dns.json` to get a mapping of top-level domains (TLDs) to their RDAP service URLs.
   - This data is cached in memory to avoid repeated requests.
2. Domain Information
   - Queries the appropriate RDAP service URL (e.g., `https://rdap.verisign.com/com/v1/domain/example.com`) to retrieve domain details.
   - Extracts registration and expiration dates from the `events` array in the response.

## Notes

- **Rate Limiting**: The application enforces a 1-second delay between API requests to prevent overwhelming the RDAP servers.
- **Error Handling**: Displays "N/A" for domains with unavailable data or unsupported TLDs.
- **Local Storage**: Domains and theme preferences are saved in the browser's local storage for persistence across sessions.
