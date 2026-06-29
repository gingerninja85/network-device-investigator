# Router Vendors and Patterns

Use this file to identify routers, gateways, firewalls, wireless controllers, and small-business network appliances.

## General router/gateway indicators

Common ports:

- 53
- 67/68
- 80
- 443
- 500
- 4500
- 7547
- 8291
- 8728
- 8729

Common clues:

- Device is the default gateway
- DHCP server is active
- DNS resolver is active
- NAT/firewall behaviour
- Web management interface
- VPN ports
- ISP management protocols

## MikroTik

Common ports:

- 8291 WinBox
- 8728 API
- 8729 API over TLS
- 80/443 web management
- 22 SSH

Clues:

- RouterOS banners
- MikroTik OUI
- WinBox service

## Ubiquiti / UniFi

Common clues:

- Ubiquiti OUI
- UniFi discovery on `10001`
- Controller/adoption context
- UniFi Network or Protect environment

Common ports vary depending on whether the device is an AP, switch, gateway, controller, or console.

## pfSense / OPNsense

Common clues:

- FreeBSD-like SSH banners
- Web UI on `80`/`443`
- Gateway/firewall role
- VPN services
- Hostnames containing `pfsense`, `opnsense`, `firewall`, or `gateway`

## OpenWrt

Common clues:

- Dropbear SSH
- uhttpd web server
- Hostnames such as `OpenWrt`
- Embedded Linux router context

## ISP routers

Common clues:

- Default gateway role
- DNS/DHCP services
- TR-069/CWMP on `7547`
- ISP-branded hostname, certificate, or web UI

## Consumer router brands

Common vendors include:

- TP-Link
- Netgear
- ASUS
- D-Link
- Linksys
- Huawei
- ZTE
- Fritz!Box / AVM

Look for web UI titles, hostnames, certificates, and DHCP information.

## Risk notes

Escalate risk if:

- Admin UI is internet exposed
- Default credentials are suspected
- Firmware is unsupported or outdated
- UPnP is unexpectedly enabled
- Unknown router/gateway appears on the LAN
- TR-069/CWMP is reachable from untrusted networks

Recommended actions:

- Confirm whether it is the expected gateway
- Update firmware
- Disable remote admin unless required
- Disable UPnP unless needed
- Use strong admin credentials
- Restrict management access to trusted networks
