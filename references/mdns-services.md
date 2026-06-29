# mDNS Services

mDNS can provide strong identity clues without logging into the device.

Use mDNS evidence together with MAC/OUI, DHCP hostname, ports, and user context.

## Common service names

| mDNS service | Possible device type |
| --- | --- |
| `_airplay._tcp` | Apple TV, AirPlay speaker, smart TV, receiver |
| `_raop._tcp` | AirPlay audio device |
| `_googlecast._tcp` | Chromecast, Google Home, Android TV, Cast-enabled speaker |
| `_hap._tcp` | Apple HomeKit device |
| `_printer._tcp` | Printer |
| `_ipp._tcp` | IPP printer |
| `_ipps._tcp` | Secure IPP printer |
| `_scanner._tcp` | Scanner or multifunction printer |
| `_smb._tcp` | SMB file server, NAS, Windows host |
| `_afpovertcp._tcp` | AFP file sharing, NAS, older Apple file sharing |
| `_ssh._tcp` | SSH host, Linux, NAS, router |
| `_http._tcp` | Web admin or web application |
| `_https._tcp` | HTTPS web admin or web application |
| `_workstation._tcp` | General workstation or Linux host |
| `_home-assistant._tcp` | Home Assistant instance |
| `_esphomelib._tcp` | ESPHome device |
| `_ewelink._tcp` | eWeLink / Sonoff-style smart home device |

## Safe discovery examples

Linux:

```bash
avahi-browse -a
avahi-browse -rt _services._dns-sd._udp
```

macOS:

```bash
dns-sd -B _services._dns-sd._udp local
```

## Risk notes

- mDNS is usually local-link only, but it may leak device names and model information.
- mDNS should not be exposed across untrusted networks unless intentionally bridged.
- Unexpected mDNS services can reveal unknown smart-home, media, printer, or NAS devices.
