---
name: network-device-investigator
description: Identify and safely investigate unknown network devices using IP addresses, MAC addresses, DHCP information, service banners, network scans, and defensive analysis.
triggers:
  - unknown network device
  - identify this device
  - network device investigator
  - nmap scan
  - open ports
  - MAC address
  - OUI lookup
  - telnet open
  - RTSP
  - ONVIF
  - IoT device
  - mystery device
---

# Network Device Investigator

Use this skill when a user needs help identifying or safely investigating an unknown network-connected device.

Examples include:

- Cameras
- Printers
- NAS devices
- Routers
- Switches
- Smart TVs
- Home automation devices
- Embedded Linux devices
- IoT devices
- Access points
- Windows or Linux servers

## Safety boundary

Only assist with devices the user owns or is authorised to investigate.

Never recommend:

- brute force attacks
- credential guessing
- exploitation
- persistence
- malware
- bypassing authentication
- unauthorised access

You may recommend safe verification steps, vendor documentation, firmware updates, network isolation, VLANs, firewall rules, factory reset, and changing default credentials.

## Goal

Produce a concise device investigation report with:

1. Likely device identity
2. Confidence level
3. Evidence
4. Risk assessment
5. Safe next checks
6. Recommended remediation

## Inputs to request if missing

Ask for only the missing items that materially improve identification:

- IP address
- MAC address
- OUI/vendor
- Nmap command and output
- Open ports
- Service banners
- DHCP hostname
- Router/firewall client name
- Physical device candidates
- Screenshots or photos if relevant

Do not block if some inputs are missing. Work with what the user provides.

## Investigation workflow

### 1. Parse known facts

Extract:

- IP address
- MAC address
- OUI/vendor
- Hostname
- Open ports
- Protocols
- Service banners
- Device location or network segment
- User's suspected device
- Network context

### 2. Identify MAC/OUI

If a MAC address is provided:

- Identify the OUI/vendor when possible.
- Explain that OUI identifies the network chipset/vendor, not always the final product brand.
- Consider OEM/rebrand relationships.
- Consult `references/common-vendors.md`.

### 3. Interpret ports and services

Use:

- `references/common-ports.md`
- `references/service-banners.md`
- `references/iot-patterns.md`

Look for combinations rather than isolated ports.

For example:

- 80 + 554 may suggest an IP camera.
- 515/631/9100 may suggest a printer.
- 445 + 5000/5001 may suggest a NAS.
- 53 + 67/68 + 80/443 may suggest a router or gateway.

### 4. Determine likely device type

Consult relevant reference files:

- `references/camera-vendors.md`
- `references/printer-vendors.md`
- `references/nas-vendors.md`
- `references/router-vendors.md`
- `references/iot-patterns.md`
- `references/mdns-services.md`
- `references/dhcp-vendor-classes.md`

### 5. Build hypotheses

Create 2-5 hypotheses ranked by confidence.

For each hypothesis, explain:

- Device class
- Why it fits
- Why it may not fit
- What would confirm or disprove it

### 6. Recommend safe enumeration

Prefer passive or low-risk checks first. Use the lowest scan tier likely to answer the question. Escalate only when needed.

#### Tier 0: Passive evidence

Use before touching the target directly.

Examples:

- Router/firewall client list
- DHCP lease table
- ARP table
- Switch MAC address table
- Wi-Fi controller client list
- Physical inventory
- Existing monitoring data

#### Tier 1: Local host and name checks

Low-noise checks from the user's own machine or router.

```bash
arp -a
ip neigh
nslookup <ip>
dig -x <ip>
ping -c 3 <ip>
```

#### Tier 2: Targeted service checks

Use when there are likely device classes to test. Prefer targeted ports over full scans.

Camera-focused:

```bash
nmap -Pn -sV -p 80,443,554,8000,8080,8081,8899,5000,6668,37777 <ip>
```

Printer-focused:

```bash
nmap -Pn -sV -p 80,443,515,631,9100,161 <ip>
```

NAS-focused:

```bash
nmap -Pn -sV -p 22,80,443,445,5000,5001,548,2049 <ip>
```

HTTP title/header check:

```bash
nmap --script=http-title,http-headers -p 80,443,8080,8443 <ip>
```

Banner check:

```bash
nmap --script=banner -p <ports> <ip>
```

#### Tier 3: Deeper TCP scan

Use when targeted scans do not explain the device.

Warn that full-port scans may be noisy for fragile IoT devices.

```bash
nmap -Pn -sV -p- <ip>
```

Avoid aggressive timing unless the user understands the trade-off.

#### Tier 4: Advanced defensive discovery

Use when normal scans are insufficient or when the device appears security-relevant.

Examples:

- mDNS discovery
- SSDP/UPnP discovery
- SNMP read-only discovery where authorised
- Packet capture with tcpdump or Wireshark
- Controller logs
- Firewall logs

If compatible cybersecurity skills are installed, delegate specialised analysis such as PCAP review or IOC extraction.

Do not recommend brute forcing credentials.

### 7. Assess risk

Flag:

- Telnet open
- Default credentials suspected
- Unknown IoT device
- Exposed camera services
- Old firmware
- Internet exposure
- UPnP enabled
- Weak or unauthenticated HTTP admin
- Unknown device on trusted LAN

Risk levels:

- Low: identified, expected, patched, and appropriately segmented
- Medium: unknown device or unnecessary services
- High: Telnet, admin services, default credentials suspected, camera/NAS exposure, or untrusted IoT on trusted LAN
- Critical: confirmed compromise, malware, credential exposure, or internet-exposed admin service

### 8. Risk scoring rubric

Use this as a guide, not a rigid formula.

Start at Low, then increase risk when evidence supports it:

- Unknown device on trusted LAN: +1
- Telnet or legacy admin service exposed: +2
- Camera/NVR/NAS or device likely to contain sensitive data: +1
- Default credentials suspected or unchanged: +2
- Internet-exposed admin interface: +3
- UPnP or unexpected inbound exposure: +1
- Outdated firmware or unsupported vendor: +1
- Signs of compromise, malware, or credential exposure: Critical

Suggested mapping:

- 0-1: Low
- 2-3: Medium
- 4-5: High
- 6+ or confirmed compromise: Critical

### 9. Optional delegation to security skills

If compatible cybersecurity skills are installed, such as the Anthropic Cybersecurity Skills, delegate specialised work when appropriate.

Examples:

- PCAP analysis
- Malware triage
- IOC extraction
- Memory forensics
- Threat hunting
- YARA or Sigma generation
- Incident response

Do not require these skills. Network Device Investigator must remain useful on its own.

## Output template

# Unknown Network Device Report

## Summary

One paragraph with likely identity and confidence.

## Evidence

- IP:
- MAC:
- OUI/vendor:
- Hostname:
- Open ports:
- Banners:
- User context:

## Likely identities

| Rank | Hypothesis | Confidence | Why |
| ---: | --- | ---: | --- |

## Risk

Risk level: Low / Medium / High / Critical

Explain why.

## Safe next checks

Provide exact commands or checks, using scan tiers.

## Recommended action

Prioritised steps.

## Confidence

Explain how confidence was determined.

## Missing evidence

List additional evidence that would improve confidence.

## What would change my mind

List evidence that would confirm or disprove the top hypothesis.
