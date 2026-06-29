# IoT Patterns

Use this file to reason about common IoT device fingerprints.

## Camera

Typical ports:

- 80
- 443
- 554
- 8000
- 8080
- 8081
- 8899
- 37777

Indicators:

- RTSP
- ONVIF
- HTTP admin interface
- `ipc` banner or prompt
- NVR-style service ports
- Embedded Linux banners

Risk notes:

- Telnet on cameras is high risk.
- Unknown cameras should usually be isolated until identified.
- Change default passwords and update firmware.

## Smart plug / smart switch

Typical ports:

- 80
- 443
- 6668

Indicators:

- Tuya LAN protocol
- ESP32/ESP8266 OUI
- Cloud-paired app context
- mDNS names related to switch, plug, bulb, or light

Risk notes:

- Prefer IoT VLAN or guest network.
- Block lateral access to trusted devices.

## NAS

Typical ports:

- 22
- 80
- 443
- 445
- 548
- 2049
- 5000
- 5001

Indicators:

- SMB
- NFS
- AFP
- Web management
- Media services
- Backup services

Risk notes:

- NAS devices often contain sensitive data.
- Avoid exposing admin interfaces to the internet.
- Keep firmware current.

## Printer

Typical ports:

- 80
- 443
- 515
- 631
- 9100
- 161

Indicators:

- IPP
- JetDirect/raw printing
- SNMP printer details
- Manufacturer web UI

Risk notes:

- Printers often expose SNMP and web admin.
- Change admin password where supported.
- Disable unused protocols.

## Router or gateway

Typical ports:

- 53
- 67/68
- 80
- 443
- 7547
- 8291
- 8728
- 8729

Indicators:

- Default gateway IP
- DHCP server
- DNS service
- Firewall or NAT behaviour
- ISP management protocols

Risk notes:

- Internet-exposed admin services are high risk.
- Disable remote admin unless required.
- Update firmware.

## Smart TV / media device

Typical ports:

- 8008
- 8009
- 8060
- 1900
- 5353

Indicators:

- Google Cast
- Roku service
- SSDP/UPnP
- mDNS media names

Risk notes:

- Usually lower risk than cameras or NAS, but still best isolated from sensitive systems.
