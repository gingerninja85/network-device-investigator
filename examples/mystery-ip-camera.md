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
User context: Possible camera or smart-home device, but not confirmed
```

## Analysis

### Known facts

- The device is active on the LAN.
- It exposes Telnet on port `23`.
- The login prompt contains `ipc`, which is often associated with IP camera firmware.
- The OUI points to a module/OEM vendor rather than a clear retail brand.

### Likely identities

| Rank | Hypothesis | Confidence | Why |
| ---: | --- | ---: | --- |
| 1 | OEM IP camera or NVR-related device | High | `ipc login:` is a strong embedded-camera clue, and Telnet is common on older/low-cost camera firmware |
| 2 | Generic embedded Linux IoT device | Medium | Telnet plus generic OUI fits many embedded devices |
| 3 | Smart-home device using camera-like firmware | Low | Possible, but `ipc` points more strongly toward camera/NVR firmware |

## Risk

Risk level: High

Reasons:

- Telnet is exposed.
- Device identity is not fully confirmed.
- Possible camera/NVR devices can expose sensitive video or credentials.
- Unknown IoT devices should not sit unsegmented on a trusted LAN.

## Safe next checks

Start passive:

```bash
arp -a
ip neigh
```

Check targeted camera-related services:

```bash
nmap -Pn -sV -p 23,80,443,554,8000,8080,8081,8899,5000,6668,37777 192.168.1.45
```

Check HTTP titles if web ports are open:

```bash
nmap --script=http-title,http-headers -p 80,443,8080,8081 192.168.1.45
```

Do not brute force the Telnet login.

## Recommended action

1. Identify the physical device.
2. Check router/firewall DHCP lease history for hostnames or vendor clues.
3. Confirm whether it is an expected camera or smart-home device.
4. If expected, update firmware and disable Telnet if possible.
5. Change default credentials through the official app/web UI.
6. Move the device to an IoT VLAN or guest network.
7. Block internet access if the device is suspicious or no longer needed.
8. Remove the device from the network if ownership cannot be confirmed.

## What would improve confidence

- HTTP title or web UI screenshot
- RTSP/ONVIF presence
- DHCP hostname
- Physical device inventory
- App pairing history
- mDNS/SSDP names
