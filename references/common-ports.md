# Common Ports

Use this file as a quick reference for interpreting open ports during safe network-device investigation.

Ports should not be interpreted in isolation. Prefer combinations of ports, banners, hostnames, MAC vendors, and user context.

| Port | Service | Common device clues |
| ---: | --- | --- |
| 21 | FTP | Embedded storage, cameras, NAS, old routers |
| 22 | SSH | Linux, Unix, routers, switches, NAS, appliances |
| 23 | Telnet | Legacy embedded admin shell; high-risk if enabled |
| 53 | DNS | Router, gateway, Pi-hole, DNS appliance |
| 67/68 | DHCP | Router, gateway, DHCP server |
| 80 | HTTP | Web admin, camera UI, printer UI, router UI |
| 123 | NTP | Router, appliance, server |
| 139 | NetBIOS | Windows, Samba, NAS, printers |
| 161 | SNMP | Printer, switch, router, UPS, NAS |
| 443 | HTTPS | Secure web admin, cloud appliance, NAS, router |
| 445 | SMB | Windows, Samba, NAS, printer |
| 515 | LPD | Printer |
| 548 | AFP | Apple file sharing, NAS |
| 554 | RTSP | IP camera, NVR, video stream |
| 631 | IPP | Printer |
| 1900 | SSDP/UPnP | IoT, media devices, routers, smart TVs |
| 2049 | NFS | NAS, Linux server |
| 3000 | Web app | Development server, appliance UI, Grafana-style apps |
| 32400 | Plex | Plex Media Server |
| 3306 | MySQL | Database server, appliance backend |
| 37777 | Dahua protocol | Dahua cameras/NVRs and OEM variants |
| 5000 | HTTP app / Synology DSM | Synology NAS, web apps |
| 5001 | HTTPS app / Synology DSM | Synology NAS |
| 5353 | mDNS | Apple, IoT, printers, HomeKit, Chromecast |
| 5432 | PostgreSQL | Database server or application host |
| 5900 | VNC | Remote desktop, embedded appliance |
| 6668 | Tuya LAN | Tuya-based IoT devices |
| 7547 | TR-069 / CWMP | ISP router management; investigate exposure carefully |
| 8000 | Hikvision SDK / alt HTTP | Hikvision/NVR/camera or alternate web service |
| 8008/8009 | Google Cast | Chromecast, Google Home, Android TV |
| 8060 | Roku | Roku devices and Roku TVs |
| 8080 | Alternate HTTP | Web admin, proxy, appliance UI |
| 8291 | MikroTik WinBox | MikroTik RouterOS |
| 8443 | Alternate HTTPS | Web admin, UniFi, appliances |
| 8728/8729 | MikroTik API | MikroTik RouterOS API |
| 8899 | ONVIF/IoT variant | Some cameras and IoT devices |
| 9100 | JetDirect/raw printing | Printers |
| 10001 | Ubiquiti discovery | UniFi discovery and adoption clues |

## High-signal combinations

- `80 + 554`: possible IP camera
- `80 + 443 + 554 + 8000`: possible camera/NVR
- `515 + 631 + 9100`: printer
- `22 + 445 + 5000/5001`: NAS, especially Synology-like devices
- `53 + 67/68 + 80/443`: router or gateway
- `1900 + 5353 + 8008/8009`: media or smart-home device
- `23 + embedded banner`: legacy IoT or embedded Linux device; treat as higher risk
