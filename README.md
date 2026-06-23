# Active Directory DNS Configuration Lab

![Status](https://img.shields.io/badge/Project-Completed-success)
![DNS](https://img.shields.io/badge/Service-DNS-0078D4)
![Active Directory](https://img.shields.io/badge/Directory-Active%20Directory-2F6FED)

A completed Windows Server lab in which I configured and validated DNS services for an Active Directory environment, including zones, host records, aliases, reverse lookups, forwarders and dynamic registration.

> **Status:** Completed and validated. This repository documents work already performed in a private lab. Real domain names, hostnames, addresses and credentials have been generalized.

## Objectives completed

- Verified the Active Directory-integrated forward lookup zone
- Created and tested host records
- Created a reverse lookup zone and PTR records
- Added and validated CNAME aliases
- Configured DNS forwarders
- Tested dynamic DNS registration
- Verified Active Directory SRV records
- Diagnosed name-resolution failures
- Documented technical findings

## Implementation summary

1. Opened DNS Manager on the domain controller.
2. Reviewed the Active Directory-integrated forward lookup zone.
3. Created host and alias records for lab resources.
4. Created a reverse lookup zone for the lab subnet.
5. Added or registered PTR records.
6. Configured external DNS forwarders.
7. Configured domain clients to use the domain controller for DNS.
8. Registered client records and cleared stale resolver cache data during testing.
9. Verified host, reverse and service-record resolution from domain endpoints.

## Validation commands

```powershell
Get-DnsServerZone
Get-DnsServerResourceRecord -ZoneName "<domain-name>"
Resolve-DnsName "<host-name>"
Resolve-DnsName "<ip-address>"
Resolve-DnsName -Type SRV "_ldap._tcp.dc._msdcs.<domain-name>"
```

```cmd
ipconfig /flushdns
ipconfig /registerdns
nslookup <host-name>
nslookup <ip-address>
```

## Outcome

The domain clients successfully resolved internal hostnames, reverse records and Active Directory service records through the domain controller. External lookups were forwarded as configured, while internal domain discovery continued to use the authoritative AD-integrated zone.

## Findings

- Active Directory depended on DNS service records, not only simple host records.
- Pointing domain clients to a public DNS server allowed internet resolution but prevented reliable domain discovery.
- Forward and reverse lookup zones served different validation purposes; successful forward resolution did not guarantee a PTR record existed.
- DNS cache could preserve an earlier failure or obsolete record, so cache clearing was useful after configuration changes.
- Dynamic registration reduced manual record creation but still required correct client DNS settings and permissions.
- Testing the `_ldap._tcp.dc._msdcs` SRV record provided stronger domain-health evidence than a basic ping test.

## Skills demonstrated

- Windows DNS administration
- Active Directory-integrated DNS
- Forward and reverse zones
- A, PTR, CNAME and SRV records
- DNS forwarders
- Dynamic registration
- Name-resolution troubleshooting
- PowerShell and command-line validation

## Security notes

- No real domain or network information is included.
- All values shown in examples are placeholders.
- The lab was completed in a controlled non-production environment.

## Author

**Dewald Pretorius** — L2 IT Support Engineer
