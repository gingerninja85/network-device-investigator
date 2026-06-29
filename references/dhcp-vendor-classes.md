# DHCP Vendor Classes

DHCP lease information can provide useful passive identity clues.

Useful fields may include:

- Hostname
- Vendor class identifier
- Client identifier
- Requested options
- Lease time
- MAC address
- Assigned IP

## Common clues

### Hostnames

Hostnames are often the fastest clue.

Examples:

- `printer`, `brn`, `epson`, `canon`, `hp` → printer
- `diskstation`, `nas`, `qnap`, `storage` → NAS
- `android`, `iphone`, `ipad`, `watch` → mobile device
- `chromecast`, `google-home`, `roku`, `tv` → media device
- `esp`, `esphome`, `tasmota`, `shelly` → smart-home/IoT device
- `camera`, `ipc`, `nvr`, `dvr` → camera or recorder

### Vendor class identifiers

Vendor class strings vary widely, but may reveal:

- Operating system family
- Device manufacturer
- Embedded firmware family
- Router or ISP equipment
- VoIP phone platform

## Investigation guidance

Use DHCP clues as passive evidence, then confirm with:

- MAC/OUI
- mDNS/SSDP names
- Open ports
- HTTP titles
- Physical inventory

## Risk notes

- DHCP names can be user-set and misleading.
- Some devices randomise MAC addresses.
- A missing hostname does not mean the device is suspicious.
- A strange hostname on a trusted LAN is worth investigating but not proof of compromise.
