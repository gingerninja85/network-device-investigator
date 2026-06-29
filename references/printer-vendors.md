# Printer Vendors and Patterns

Use this file to identify printers and multifunction devices from ports, banners, hostnames, and service clues.

## General printer indicators

Common ports:

- 80
- 443
- 515
- 631
- 9100
- 161

Common clues:

- IPP on `631`
- JetDirect/raw printing on `9100`
- LPD on `515`
- SNMP on `161`
- Web management UI on `80` or `443`
- Hostnames containing `printer`, `print`, `laser`, `mfc`, `brn`, `epson`, `canon`, or `hp`

## Brother

Common clues:

- Hostnames beginning with `BRN`, `BRW`, or model names such as `MFC`, `DCP`, or `HL`
- Ports `80`, `443`, `515`, `631`, `9100`, and `161`
- Web UI often exposes model information

## HP / Hewlett-Packard

Common clues:

- JetDirect on `9100`
- IPP on `631`
- SNMP on `161`
- Embedded Web Server on `80` or `443`
- Hostnames containing `HP`, `LaserJet`, `OfficeJet`, or `JetDirect`

## Canon

Common clues:

- Web management on `80` or `443`
- IPP and LPD services
- Hostnames or banners containing `Canon`, `iR`, `imageRUNNER`, or `PIXMA`

## Epson

Common clues:

- IPP on `631`
- Web interface on `80` or `443`
- Hostnames or banners containing `EPSON`

## Xerox

Common clues:

- Web management interface
- IPP/LPD/JetDirect support
- SNMP model details
- Hostnames or banners containing `Xerox` or `WorkCentre`

## Risk notes

Printers are often overlooked but may expose:

- Web admin interfaces
- SNMP details
- Address books
- Scan-to-email credentials
- Stored print jobs
- Firmware update mechanisms

Recommended actions:

- Change default admin password
- Disable unused protocols
- Restrict printer management to trusted networks
- Keep firmware updated
- Avoid internet exposure
