# Outreach and Sharing Kit

Use this page when sharing Network Device Investigator with communities, contributors, and other Hermes users.

## One-line description

Network Device Investigator is a Hermes skill for safely identifying unknown devices on a network from evidence like IPs, MAC addresses, DHCP names, open ports, service banners, and Nmap output.

## Short description

Network Device Investigator helps Hermes answer a common home-lab and IT-support question: "What is this device on my network?"

It uses defensive investigation methods to reason from MAC/OUI vendors, port combinations, DHCP hostnames, banners, and user context. It produces likely device identities, confidence levels, safe next checks, risk assessment, and remediation advice.

## Longer description

Network Device Investigator is a community Hermes skill focused on safe network-device identification.

It is designed for home-lab users, MSP technicians, network administrators, and security analysts who regularly find mystery devices on a LAN and need a structured way to investigate them.

The project is intentionally defensive. It does not support brute forcing, exploitation, persistence, credential guessing, or unauthorised access. Instead, it focuses on evidence-based identification, safe enumeration, risk assessment, and practical remediation.

The skill is standalone, but can optionally work alongside cybersecurity skill packs such as the Anthropic Cybersecurity Skills for deeper PCAP analysis, IOC extraction, malware triage, and incident-response workflows.

## Suggested GitHub topics

If repository topics are editable, consider adding:

- hermes
- hermes-skill
- network
- networking
- homelab
- cybersecurity
- defensive-security
- nmap
- iot
- device-identification
- network-discovery
- msp

## Social post - short

I just published Network Device Investigator, a Hermes skill for safely identifying unknown devices on your network using IPs, MAC addresses, DHCP names, open ports, banners, and Nmap output.

It is built for home labs, MSPs, network admins, and defensive security work.

Repo: https://github.com/gingerninja85/network-device-investigator

## Social post - technical

I have started building Network Device Investigator, a Hermes skill for defensive network-device identification.

The goal is to help Hermes reason through mystery LAN devices using:

- MAC/OUI vendors
- DHCP hostnames
- Nmap scans
- Port combinations
- Service banners
- mDNS/SSDP/SNMP clues
- Device-specific fingerprints

It outputs hypotheses, confidence levels, safe next checks, risk assessment, and remediation steps.

The project is intentionally defensive and does not support brute forcing, exploitation, or unauthorised access.

Contributions welcome, especially vendor fingerprints, anonymised examples, and safe investigation workflows.

Repo: https://github.com/gingerninja85/network-device-investigator

## Reddit / forum post

Title: I started a Hermes skill for identifying mystery devices on a LAN

Body:

I have started building Network Device Investigator, a Hermes skill for safely identifying unknown devices on a network.

The idea is to help Hermes reason from evidence like MAC/OUI vendor, DHCP hostname, open ports, Nmap output, service banners, mDNS/SSDP clues, and user context.

The output is a structured investigation report with likely device identities, confidence levels, risk assessment, safe next checks, and remediation advice.

It is aimed at home-lab users, MSP techs, network admins, and defensive security folks.

The project is defensive-only. No brute forcing, exploitation, credential guessing, or unauthorised access.

I would especially appreciate contributions around:

- Camera/NVR fingerprints
- Printer fingerprints
- NAS/router fingerprints
- IoT patterns
- mDNS/SSDP clues
- Safe investigation examples
- Better risk scoring

Repo: https://github.com/gingerninja85/network-device-investigator

## LinkedIn-style post

I have started an open-source Hermes skill called Network Device Investigator.

It is designed to help identify unknown devices on a network using defensive investigation techniques: MAC/OUI vendors, DHCP hostnames, open ports, Nmap scans, service banners, and device-specific fingerprints.

The goal is to provide a structured report with likely identities, confidence levels, risk assessment, safe next checks, and remediation advice.

It is particularly relevant for home labs, MSP environments, network administration, and defensive security workflows.

Contributions are welcome, especially around vendor fingerprints and safe example investigations.

Repo: https://github.com/gingerninja85/network-device-investigator

## Communities to consider

Share only where self-promotion and project posts are allowed.

Potential communities:

- Hermes / NousResearch community channels
- Home lab communities
- Network administration forums
- Defensive security communities
- MSP communities
- GitHub topic discovery
- Relevant Discord servers where open-source project sharing is allowed

## Contribution ask

Good first contributions include:

- Adding anonymised example investigations
- Adding vendor fingerprints
- Improving common-port interpretations
- Expanding camera, printer, NAS, and router references
- Adding safe mDNS/SSDP/SNMP investigation notes
- Improving risk scoring and remediation guidance
- Reviewing safety language

## Maintainer note

When sharing the project, emphasise that it is defensive and safe-by-design. The project should not become a brute-force, exploitation, or unauthorised-access tool.
