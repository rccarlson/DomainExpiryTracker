# Domain Expiration Tracker

A web-based tool for tracking domain registration and expiration dates using RDAP (Registration Data Access Protocol) services using the ICANN RDAP API. Users can add domains individually or in bulk, view them in a sortable table, and update their information with rate-limited API queries. The application persists data using the browser's local storage.

[Link to live page](https://rccarlson.github.io/DomainExpiryTracker/)

## AI Disclosure

This application was built with the assistance of LLMs.

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


## Icon attribution

“internet” by IconMark from Noun Project (CC BY 3.0)

https://thenounproject.com/icon/internet-1246382/
