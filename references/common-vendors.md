# Common Vendors

OUI and MAC vendors are useful clues, but they rarely prove the final product brand.

Many devices use Wi-Fi, Bluetooth, or Ethernet modules made by a different company from the brand printed on the device.

## Interpretation rule

Treat OUI as evidence of the network chipset or module vendor, not the consumer product identity.

Combine OUI with:

- DHCP hostname
- Open ports
- Service banners
- HTTP titles
- mDNS/SSDP names
- Physical inventory
- User context

## Common vendors and clues

### Espressif

Usually ESP32 or ESP8266-based devices.

Often appears in:

- ESPHome devices
- Home Assistant sensors
- Smart plugs
- DIY IoT
- LED controllers
- Environmental sensors

### Shenzhen Bilian Electronic

Often Wi-Fi modules used inside:

- IP cameras
- Smart plugs
- Generic IoT devices
- Tuya-style embedded devices
- Low-cost embedded Linux hardware

The final product may be sold under a completely different brand.

### AzureWave

Wireless modules found inside:

- Laptops
- IoT devices
- Cameras
- Media devices
- Embedded systems

### Murata

Wi-Fi/Bluetooth modules used by many brands.

Can appear inside:

- Phones
- Laptops
- IoT devices
- Cameras
- Consumer electronics

### Lite-On

Networking and wireless hardware.

Often appears in:

- PCs
- Laptops
- Printers
- Consumer devices

### Broadcom

Common in:

- Routers
- NAS devices
- Switches
- Wireless hardware
- Media devices

### Realtek

Common in:

- Embedded networking
- Routers
- Cameras
- Mini PCs
- USB Ethernet adapters
- Low-cost network appliances

### Hon Hai / Foxconn

Large OEM manufacturer.

May appear in devices sold by many other brands.

Do not assume the device is branded Foxconn.

### Intel

Common in:

- Desktops
- Laptops
- Servers
- NICs
- Mini PCs
- Virtualisation hosts

### Hewlett Packard Enterprise / HP

Common in:

- Servers
- iLO interfaces
- Printers
- Enterprise networking
- Storage devices

### Dell

Common in:

- Servers
- Workstations
- Storage
- Enterprise networking
- iDRAC interfaces

### Ubiquiti

Common in:

- UniFi access points
- UniFi switches
- UniFi gateways
- AirMAX devices

Look for port `10001`, UniFi discovery, or controller adoption clues.

### MikroTik

Common in:

- Routers
- Wireless bridges
- Small business networks

Look for ports `8291`, `8728`, and `8729`.

### Synology

Common in:

- NAS devices

Look for ports `5000`, `5001`, `445`, `548`, `2049`, and hostnames containing `diskstation`.

### QNAP

Common in:

- NAS devices

Look for web management ports, SMB, AFP, NFS, and QNAP-specific HTTP titles.
