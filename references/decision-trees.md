# Decision Trees

Use these lightweight decision trees to reason through common unknown-device cases. They are not proof by themselves; combine them with OUI, DHCP names, banners, physical inventory, and user context.

## IP camera or NVR

```text
Does the evidence mention video/camera terms (`ipc`, `nvr`, `dvr`, `onvif`, `rtsp`)?
├── Yes
│   ├── Is Telnet open?
│   │   ├── Yes: likely embedded camera/NVR firmware; risk increases to High
│   │   └── No: continue with camera service checks
│   ├── Is RTSP on 554 open?
│   │   ├── Yes: camera/NVR confidence increases
│   │   └── No: check HTTP title, ONVIF, vendor apps, and cloud pairing
│   ├── Is port 8000 open?
│   │   └── Consider Hikvision or Hikvision OEM variant
│   ├── Is port 37777 open?
│   │   └── Consider Dahua or Dahua OEM variant
│   └── Is port 6668 open?
│       └── Consider Tuya/Smart Life style IoT camera
└── No
    └── Do not assume camera; check other device trees
```

## Printer

```text
Are printer ports present: 515, 631, or 9100?
├── Yes
│   ├── Is SNMP on 161 open?
│   │   └── Safe SNMP discovery may reveal model and serial; avoid exposing sensitive values in reports
│   ├── Is HTTP/HTTPS admin open?
│   │   └── Check title/headers for vendor clues
│   └── Are multiple print protocols open?
│       └── Printer confidence increases
└── No
    └── Printer less likely unless hostname/OUI strongly suggests it
```

## NAS or file server

```text
Is SMB on 445 open?
├── Yes
│   ├── Are 5000/5001 open?
│   │   └── Consider Synology DSM
│   ├── Are NFS 2049 or AFP 548 open?
│   │   └── NAS/file-server confidence increases
│   └── Is SSH also open?
│       └── Admin-capable NAS or Linux file server possible
└── No
    └── NAS less likely; check web app and media-service clues
```

## Router or gateway

```text
Is the IP the default gateway or DHCP/DNS server?
├── Yes
│   ├── Are 53 and 67/68 present?
│   │   └── Router/gateway confidence increases
│   ├── Is 7547 present?
│   │   └── ISP/router management clue; investigate exposure carefully
│   ├── Are MikroTik ports 8291 or 8728/8729 present?
│   │   └── Consider MikroTik RouterOS
│   └── Is internet-facing admin enabled?
│       └── At least High risk; Critical if default creds, unauthenticated, or known-vulnerable
└── No
    └── Could still be an AP/bridge; check OUI and controller data
```

## Smart home / IoT

```text
Is the vendor a common IoT module vendor: Espressif, Shenzhen Bilian, Realtek, Tuya-like OEM?
├── Yes
│   ├── Is 6668 open?
│   │   └── Tuya LAN protocol clue
│   ├── Are mDNS/SSDP names present?
│   │   └── Use names to infer device class: plug, bulb, camera, TV, sensor
│   ├── Is Telnet open?
│   │   └── High risk; isolate until identified
│   └── Is the device expected and app-managed?
│       └── Lower risk after firmware, credentials, and segmentation checks
└── No
    └── Continue with ports, banners, DHCP, and physical inventory
```

## Media device / smart TV

```text
Are 8008/8009, 8060, 1900, or 5353 present?
├── Yes
│   ├── 8008/8009 present?
│   │   └── Chromecast / Google Cast / Android TV clue
│   ├── 8060 present?
│   │   └── Roku clue
│   └── SSDP/mDNS names mention TV, cast, media, speaker, or vendor?
│       └── Media-device confidence increases
└── No
    └── Media device less likely unless DHCP/app context supports it
```

## Confidence rule

- High confidence: multiple independent clues agree, such as OUI + ports + banner + DHCP name.
- Medium confidence: one strong clue plus supporting context.
- Low confidence: generic OUI or one weak signal with no corroboration.

Always state what would change the conclusion.
