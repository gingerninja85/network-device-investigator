# Example: Mystery IP Camera

This is a generic, anonymised example based on a common home-lab/MSP scenario.

## Input evidence

```text
Unknown device on LAN

IP: 192.168.1.45
MAC: AA:BB:CC:DD:EE:FF
OUI/vendor: Generic Wi-Fi module vendor
DHCP hostname: unknown
Open ports: 23/tcp
Banner: ipc login:
User context: Several smart-home and camera devices are present on the network.
```

## Summary

The device is most likely an embedded IP camera, NVR-related device, or OEM camera module.

Confidence: Medium

The strongest clue is the `ipc login:` Telnet prompt. `ipc` is commonly used as shorthand for IP camera in embedded camera/NVR environments. The limited exposed service set makes the device harder to identify, so confidence should remain below High until more evidence is collected.

## Evidence

| Evidence | Interpretation |
| --- | --- |
| Telnet on `23/tcp` | Legacy embedded management service; higher-risk finding |
| `ipc login:` prompt | Strong camera/NVR-style embedded Linux clue |
| Generic Wi-Fi module OUI | Could indicate an OEM/rebranded IoT device |
| No HTTP/RTSP shown yet | Camera hypothesis is plausible but not confirmed |

## Likely identities

| Rank | Hypothesis | Confidence | Why |
| ---: | --- | ---: | --- |
| 1 | OEM IP camera or camera module | Medium | `ipc login:` strongly suggests camera/NVR firmware naming |
| 2 | NVR/DVR-related embedded device | Medium-Low | Same `ipc` clue could appear in video recorder ecosystems |
| 3 | Generic embedded Linux IoT device | Low-Medium | Telnet and generic Wi-Fi module fit, but `ipc` points more toward camera |

## Risk

Risk level: High

Reasons:

- Telnet is exposed.
- The device is not fully identified.
- Camera/NVR-class devices can expose sensitive video streams or credentials.
- Unknown IoT devices on a trusted LAN can create lateral-movement risk.

## Safe next checks

Start passive, then escalate only if needed.

### Tier 0: Passive evidence

- Check router/firewall DHCP lease table.
- Check Wi-Fi controller client list.
- Look for a matching physical device.
- Check whether any camera/mobile app shows the device as online.

### Tier 1: Local checks

```bash
arp -a
ip neigh
nslookup 192.168.1.45
dig -x 192.168.1.45
```

### Tier 2: Targeted camera checks

```bash
nmap -Pn -sV -p 23,80,443,554,8000,8080,8081,8899,5000,6668,37777 192.168.1.45
nmap --script=banner -p 23 192.168.1.45
```

### Tier 3: Deeper scan

Only use if targeted checks are insufficient and the device is not fragile.

```bash
nmap -Pn -sV -p- 192.168.1.45
```

## Recommended action

1. Identify the physical device.
2. Isolate it to an IoT/guest VLAN if possible.
3. Disable Telnet if the vendor interface allows it.
4. Update firmware.
5. Change default credentials through the official app or web UI.
6. Block internet access if the device is suspicious or no longer needed.
7. Remove it from the network if ownership cannot be confirmed.

## What would increase confidence

- RTSP on `554`.
- HTTP admin UI identifying a camera/NVR.
- ONVIF discovery.
- Camera app showing the same IP/MAC.
- Vendor/model from DHCP, mDNS, SSDP, or SNMP.

## What would change the conclusion

- Printer-specific ports such as `631` or `9100`.
- NAS services such as `445`, `5000`, or `5001`.
- Router/gateway role evidence such as DHCP/DNS services.
- A physical inventory match showing the device is not camera-related.
