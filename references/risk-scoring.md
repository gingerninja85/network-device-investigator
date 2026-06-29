# Risk Scoring

This rubric helps produce consistent risk ratings during network-device investigation.

It is a guide, not a rigid formula. Use judgement and explain uncertainty.

## Risk levels

### Low

Use when the device is:

- Identified
- Expected on the network
- Patched or reasonably current
- Not exposing unnecessary admin services
- Appropriately segmented

### Medium

Use when:

- The device is unknown but not clearly dangerous
- Unnecessary services are exposed on the LAN
- The device is IoT but not highly sensitive
- Firmware/update status is unknown
- The device is on a trusted LAN but should probably be segmented

### High

Use when:

- Telnet or legacy admin services are exposed
- Default credentials are suspected
- The device is a camera, NVR, NAS, router, firewall, or management interface
- The device is unknown and sits on a trusted network
- Admin services are reachable from broader internal networks than needed
- Firmware appears old or unsupported

### Critical

Use when:

- There is confirmed compromise
- Malware or suspicious traffic is observed
- Credentials are exposed
- Admin interface is exposed to the internet
- Sensitive data is accessible to unauthorised users
- The device is acting as a rogue gateway, DNS server, DHCP server, or MITM point

## Additive scoring guide

Start at 0.

| Evidence | Add |
| --- | ---: |
| Unknown device on trusted LAN | +1 |
| Unnecessary service exposed | +1 |
| Telnet or legacy admin exposed | +2 |
| Camera/NVR/NAS/router/firewall/management device | +1 |
| Default credentials suspected | +2 |
| Internet-exposed admin interface | +3 |
| UPnP or unexpected inbound exposure | +1 |
| Outdated firmware or unsupported vendor | +1 |
| Signs of compromise, malware, credential exposure, or rogue network role | Critical |

Suggested mapping:

- 0-1: Low
- 2-3: Medium
- 4-5: High
- 6+ or confirmed compromise: Critical

## Remediation priorities

1. Confirm ownership and physical identity.
2. Remove or isolate untrusted devices.
3. Disable internet exposure for admin interfaces.
4. Change default credentials.
5. Update firmware.
6. Disable unused services.
7. Move IoT or untrusted devices to a segmented network.
8. Monitor for suspicious traffic if compromise is suspected.
