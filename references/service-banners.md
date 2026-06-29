# Service Banners

Service banners are useful clues, but they are not proof by themselves.

Always combine banners with ports, hostnames, MAC/OUI information, HTTP titles, DHCP data, and user context.

## Common banner clues

### `ipc login:`

Likely clues:

- IP camera
- NVR/DVR
- Embedded Linux video device
- OEM camera firmware

Risk notes:

- If exposed over Telnet, treat as high risk.
- Do not recommend credential guessing or brute force.
- Recommend isolating the device, checking vendor firmware, and disabling Telnet where possible.

### `BusyBox`

Likely clues:

- Embedded Linux
- Router
- Camera
- IoT device
- NAS appliance

Risk notes:

- BusyBox is common and not inherently bad.
- Pair with ports and vendor clues before drawing conclusions.

### `Dropbear sshd`

Likely clues:

- Embedded Linux
- Router
- IoT appliance
- NAS
- OpenWrt-like device

Risk notes:

- SSH is safer than Telnet, but still an admin interface.
- Confirm whether the service is expected.

### `OpenSSH`

Likely clues:

- Linux/Unix server
- NAS
- Router or firewall
- Hypervisor host
- Raspberry Pi or single-board computer

### `lighttpd`, `boa`, `GoAhead-Webs`, `uhttpd`

Likely clues:

- Embedded web admin
- Router
- Camera
- Printer
- IoT appliance

Risk notes:

- Check HTTP title and headers.
- Do not assume device class from web server alone.

### `JetDirect` or raw printer responses

Likely clues:

- Printer
- Print server

Common port:

- 9100

### `Samba smbd`

Likely clues:

- NAS
- Linux file server
- Printer with file sharing
- Media device

### `Microsoft-DS` / SMB Windows banners

Likely clues:

- Windows host
- Domain controller
- File server
- Windows workstation

### `RouterOS`

Likely clues:

- MikroTik router

Common ports:

- 8291
- 8728
- 8729

### `Synology` / `DiskStation`

Likely clues:

- Synology NAS

Common ports:

- 5000
- 5001
- 445
- 548
- 2049

### `QNAP`

Likely clues:

- QNAP NAS

Common indicators:

- Web management UI
- SMB/NFS/AFP
- Media services

### `Hikvision`

Likely clues:

- Hikvision camera or NVR
- OEM Hikvision-based device

Common ports:

- 80
- 443
- 554
- 8000

### `Dahua`

Likely clues:

- Dahua camera or NVR
- OEM Dahua-based device

Common ports:

- 80
- 443
- 554
- 37777

## Cautions

- Banners can be missing, misleading, generic, or spoofed.
- A service banner identifies software, not always the device type.
- Never use banners as a reason to attempt unauthorised login.
