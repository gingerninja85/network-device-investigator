# Network Device Investigator

A Hermes skill for safely identifying and investigating unknown network devices using IP addresses, MAC addresses, DHCP information, service fingerprints, and defensive analysis.

This project is designed for home labs, MSPs, network administrators, security analysts, and curious users who need to answer a simple but surprisingly common question:

> What is this device on my network?

## What it does

Network Device Investigator helps Hermes reason from evidence such as:

- IP addresses
- MAC addresses and OUI vendors
- DHCP hostnames
- Router or firewall client lists
- Nmap scans
- Open ports
- Service banners
- HTTP titles and headers
- mDNS, SSDP, SNMP, and UPnP clues
- User-provided screenshots or descriptions

It then produces a structured report with likely device identities, confidence levels, risk assessment, safe next steps, and remediation advice.

## Features

- Unknown device identification
- OUI and vendor interpretation
- Open-port fingerprinting
- Camera, printer, NAS, router, IoT, and embedded Linux detection patterns
- Defensive investigation methodology
- Risk assessment
- Confidence scoring
- Safe next-step commands
- Modular reference files for maintainability

## Safety scope

This skill is for defensive investigation only.

Use it only on devices and networks you own or are authorised to assess.

It does not assist with:

- brute forcing
- credential guessing
- exploitation
- persistence
- malware
- bypassing authentication
- unauthorised access

## Requirements

### Core

No external Hermes skill dependencies are required.

This repository is intended to work as a standalone Hermes skill.

### Recommended external tools

The skill produces better results when the user can provide output from tools such as:

- Nmap
- arp-scan
- netcat / nc
- curl
- dig / nslookup
- tcpdump
- Wireshark
- SNMP tools such as snmpwalk
- avahi-browse or other mDNS discovery tools
- UPnP / SSDP discovery tools

These tools are not bundled with the skill. They are recommended sources of investigation data.

## Optional Hermes integrations

For deeper security analysis, install the Anthropic Cybersecurity Skills or another compatible cybersecurity skill pack.

If those skills are available, Network Device Investigator may delegate specialised tasks such as:

- PCAP analysis
- malware triage
- IOC extraction
- threat hunting
- YARA rule generation
- Sigma rule writing
- memory forensics
- incident-response workflows

The skill should not require those integrations. It should remain useful on its own.

## Capability matrix

| Capability | Built in | Optional cybersecurity skills |
| --- | ---: | ---: |
| Device identification | Yes |  |
| OUI interpretation | Yes |  |
| Port fingerprinting | Yes |  |
| Camera detection patterns | Yes |  |
| Printer detection patterns | Yes |  |
| NAS/router/IoT patterns | Yes |  |
| Safe investigation workflow | Yes |  |
| Risk assessment | Yes |  |
| PCAP analysis |  | Yes |
| Malware triage |  | Yes |
| IOC extraction |  | Yes |
| Threat hunting |  | Yes |
| Memory forensics |  | Yes |

## Repository structure

```text
network-device-investigator/
├── SKILL.md
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── .github/ISSUE_TEMPLATE/
├── examples/
├── references/
└── docs/
```

Current examples include:

- `examples/mystery-ip-camera.md`
- `examples/unknown-printer.md`
- `examples/nas-device.md`

## Installation

Install the whole folder, not just `SKILL.md`. The supporting `references/`
and `examples/` files are part of the skill.

```bash
mkdir -p ~/.hermes/skills/networking
git clone https://github.com/gingerninja85/network-device-investigator.git \
  ~/.hermes/skills/networking/network-device-investigator
```

Verify Hermes can see it:

```bash
hermes skills list | grep network-device-investigator
```

Inside an active Hermes session, load it with:

```text
/skill network-device-investigator
```

If you install from a raw `SKILL.md` URL, references may not be copied. Use the
folder install above when you want the full investigation workflow.

## Example prompt

```text
Use Network Device Investigator.

Unknown device on my LAN:
- IP: 192.168.1.45
- MAC: AA:BB:CC:DD:EE:FF
- DHCP hostname: unknown
- Open ports: 23/tcp, 80/tcp, 554/tcp
- Banner: ipc login:

What is this likely to be, how risky is it, and what should I check next?
```

## Project status

Early public version. The core workflow, safety boundary, references, and the
first example investigation are present. More examples, decision trees, and
integration notes are still being expanded.

See `docs/roadmap.md` for planned improvements.
