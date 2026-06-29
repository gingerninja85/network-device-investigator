# Contributing

Thanks for considering a contribution to Network Device Investigator.

This project is a Hermes skill for safe, defensive identification of unknown network devices.

## Good contributions

Useful contributions include:

- Anonymised example investigations
- Vendor fingerprints
- Port/service combinations
- mDNS, SSDP, SNMP, and DHCP clues
- Safe scan guidance
- Risk scoring improvements
- Documentation improvements
- Corrections to misleading fingerprints

## Safety rules

This project is defensive-only.

Do not contribute workflows for:

- brute forcing
- credential guessing
- exploitation
- persistence
- malware
- bypassing authentication
- unauthorised access

It is fine to document that a risky service exists, such as Telnet or an exposed admin UI. It is not fine to provide steps to break into it.

## Anonymisation

When adding examples, remove or replace:

- Real public IP addresses
- Private IPs tied to your real network
- Real MAC addresses
- Serial numbers
- Hostnames containing personal or company names
- Screenshots with sensitive details
- Customer names
- Credentials, tokens, or secrets

Use documentation ranges and placeholders such as:

```text
192.168.1.45
AA:BB:CC:DD:EE:FF
example-camera.local
```

## Writing style

Prefer:

- Clear evidence
- Confidence levels
- Safe next checks
- Practical remediation
- Explicit uncertainty

Avoid:

- Overclaiming identity from one clue
- Treating OUI as final product brand
- Aggressive scan defaults
- Offensive language or tactics

## Pull request checklist

Before opening a pull request, check that:

- The contribution is defensive and authorised-use only.
- No private network or customer details are included.
- The file fits the existing structure.
- The guidance is safe for fragile IoT devices.
- Any uncertainty is clearly stated.
