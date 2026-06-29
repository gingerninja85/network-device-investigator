# Roadmap

This roadmap tracks planned improvements for Network Device Investigator.

The goal is to build a practical Hermes skill for safely identifying unknown network devices from evidence such as MAC addresses, OUI vendors, DHCP names, ports, banners, service fingerprints, and user context.

## v0.1.0 - Core skill foundation

Status: In progress

Planned scope:

- [x] Initial `SKILL.md`
- [x] Project `README.md`
- [x] Common ports reference
- [x] Common vendors reference
- [x] IoT pattern reference
- [x] Camera vendor reference
- [ ] Printer vendor reference
- [ ] NAS vendor reference
- [ ] Router/vendor reference
- [ ] Service banner reference
- [ ] mDNS service reference
- [ ] DHCP vendor class reference
- [ ] First example investigations

## v0.2.0 - Example investigations

Add realistic, generic examples that do not contain private network details.

Planned examples:

- [ ] Mystery IP camera
- [ ] Unknown printer
- [ ] NAS device
- [ ] Router or gateway
- [ ] Switch or access point
- [ ] Smart plug or Tuya-style IoT device
- [ ] Unknown Linux host
- [ ] Media device / smart TV

Each example should include:

- Input evidence
- Likely hypotheses
- Confidence rating
- Safe next checks
- Risk assessment
- Recommended remediation

## v0.3.0 - Device decision trees

Add decision-tree style references that teach Hermes how to reason through device identity.

Examples:

```text
Port 554 present?
├── Yes
│   ├── HTTP admin also present?
│   │   ├── Yes: camera confidence increases
│   │   └── No: check RTSP banner and ONVIF
│   ├── Port 8000 present?
│   │   └── Consider Hikvision or OEM variant
│   └── Port 37777 present?
│       └── Consider Dahua or OEM variant
└── No
    └── Check other service combinations
```

Planned decision trees:

- [ ] IP camera/NVR
- [ ] Printer
- [ ] NAS
- [ ] Router/gateway
- [ ] Smart home / IoT
- [ ] Media devices
- [ ] Enterprise management interfaces

## v0.4.0 - Better security triage

Improve defensive security guidance without crossing into offensive misuse.

Planned additions:

- [ ] Risk scoring rubric
- [ ] Telnet exposure guidance
- [ ] Internet-exposed admin service guidance
- [ ] UPnP risk guidance
- [ ] Unknown IoT isolation checklist
- [ ] Default credential safety policy
- [ ] Firmware update checklist
- [ ] VLAN and firewall segmentation examples

## v0.5.0 - Optional integrations

Document how the skill can integrate with other Hermes skills and external tools.

Planned additions:

- [ ] Anthropic Cybersecurity Skills integration notes
- [ ] PCAP handoff workflow
- [ ] IOC extraction handoff workflow
- [ ] Incident-response handoff workflow
- [ ] Nmap output examples
- [ ] Wireshark/tcpdump data collection examples
- [ ] SNMP discovery examples
- [ ] mDNS/SSDP discovery examples

The core skill should remain functional without optional integrations.

## v1.0.0 - First stable release

Criteria for v1.0.0:

- [ ] Standalone `SKILL.md` is usable and safe
- [ ] README clearly explains purpose, scope, installation, and safety
- [ ] Core references are complete enough for common home-lab/MSP use
- [ ] At least five example investigations are included
- [ ] Safety boundaries are clearly documented
- [ ] Optional integrations are documented but not required
- [ ] No private or user-specific network details are present
- [ ] License, contribution guide, changelog, and code of conduct are present

## Long-term ideas

Potential future enhancements:

- Vendor-specific fingerprint files
- Common RTSP path reference
- ONVIF investigation checklist
- SNMP OID clues for printers, switches, UPS devices, and NAS platforms
- TTL and OS-fingerprint notes
- Home Assistant / ESPHome / Shelly device patterns
- MikroTik, UniFi, Synology, QNAP, HP iLO, and Dell iDRAC deep dives
- Markdown linting via GitHub Actions
- Example report templates
- Contributor-friendly issue templates

## Contribution priorities

The most useful contributions are likely to be:

1. Realistic but anonymised example investigations
2. Vendor fingerprints
3. Port/service combinations
4. Safe investigation checklists
5. Corrections to misleading or overly broad fingerprints
6. Better wording around safety and authorisation
