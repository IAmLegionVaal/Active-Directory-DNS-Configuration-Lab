# Repairs and Remediation Performed

The completed DNS lab included corrective work when internal names and Active Directory service records did not initially resolve as expected.

## Repairs completed

- Corrected domain clients that were using the wrong DNS server.
- Cleared stale resolver data on the affected systems.
- Corrected missing or inaccurate host and reverse records.
- Re-registered dynamic client records.
- Corrected the reverse lookup zone used for the lab subnet.
- Corrected DNS forwarder configuration for external lookups.
- Repeated Active Directory service-record validation after the repairs.
- Confirmed both forward and reverse resolution from the domain clients.

The final DNS configuration supported internal host resolution, domain discovery and external forwarding.

**This was tested by me to be working. User experience may vary.**
