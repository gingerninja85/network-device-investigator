# Example: Unknown Printer

This is a generic, anonymised example for a common office/home-lab device.

## Input evidence

```text
Unknown device on LAN
IP: 192.168.1.72
MAC: AA:BB:CC:DD:EE:11
OUI/vendor: Printer manufacturer or Lite-On module
DHCP hostname: printer-7c21 or unknown
Open ports: 80/tcp, 443/tcp, 515/tcp, 631/tcp, 9100/tcp, 161/udp
User context: There is a wireless printer somewhere in the building
```

## Analysis

### Known facts

- Multiple print-related ports are present.
- `631/tcp` suggests IPP.
- `9100/tcp` suggests JetDirect/raw printing.
- `515/tcp` suggests LPD.
- `161/udp` suggests SNMP discovery may be available.
- HTTP/HTTPS likely exposes a printer web admin interface.

### Likely identities

| Rank | Hypothesis | Confidence | Why |
| ---: | --- | ---: | --- |
| 1 | Network printer or multifunction printer | High | Multiple independent printer protocols are exposed |
| 2 | Print server appliance | Medium | Same ports fit a dedicated print server, especially if no scanner/fax clues exist |
| 3 | NAS or router with print sharing | Low | Possible, but the port combination strongly favours a printer |

## Risk

Risk level: Medium

Reasons:

- Printers often expose web admin and SNMP.
- Firmware/update state is unknown.
- Printers can store documents, address books, Wi-Fi details, and scan destinations.
- Risk increases to High if the admin interface uses default credentials, if SNMP exposes sensitive data, or if the printer sits on a trusted LAN with broad access.

## Safe next checks

Check passive/router evidence first:

```bash
arp -a
ip neigh
```

Check HTTP titles:

```bash
nmap --script=http-title,http-headers -p 80,443 192.168.1.72
```

If SNMP is authorised and expected, use read-only discovery carefully:

```bash
snmpwalk -v2c -c public 192.168.1.72 1.3.6.1.2.1.1
```

Do not print test pages or change printer settings unless authorised.

## Recommended action

1. Confirm the physical printer and owner.
2. Change default admin credentials through the official web UI.
3. Disable unused protocols such as LPD, raw 9100, FTP, or Telnet if present.
4. Restrict printer access to trusted client subnets.
5. Disable public SNMP community strings or replace them with secure management.
6. Update firmware.
7. Segment printers away from sensitive servers and user workstations where practical.

## What would improve confidence

- HTTP title/header with vendor/model
- SNMP system description
- DHCP hostname
- Physical printer label/model
- Router/AP client name
