# Camera Vendors and Patterns

This file contains common clues for identifying IP cameras and NVRs.

## General camera indicators

Common evidence:

- RTSP on port `554`
- ONVIF-related ports or service names
- HTTP/HTTPS admin UI
- Prompts or banners containing `ipc`, `ipcamera`, `nvr`, or `dvr`
- Ports `8000`, `8080`, `8081`, `8899`, or `37777`
- MAC OUI belonging to a Wi-Fi module vendor rather than the camera brand

## Hikvision and OEM variants

Common ports:

- 80
- 443
- 554
- 8000

Clues:

- SDK service on `8000`
- RTSP support
- ONVIF support
- Web UI with Hikvision-style titles or headers

## Dahua and OEM variants

Common ports:

- 80
- 443
- 554
- 37777

Clues:

- Dahua protocol on `37777`
- RTSP support
- ONVIF support
- OEM camera brands may expose Dahua-like services without Dahua branding

## Reolink

Common ports:

- 80
- 443
- 554
- 8000
- 9000

Clues:

- Reolink HTTP titles or certificates
- RTSP support on many models
- ONVIF support on many models

## Axis

Common ports:

- 80
- 443
- 554

Clues:

- Axis HTTP titles or headers
- Enterprise camera environment
- ONVIF and RTSP support

## UniFi Protect

Common clues:

- Ubiquiti OUI
- UniFi network context
- Camera adopted into UniFi Protect
- Services may be less obvious when camera is managed by a console/NVR

## Tuya / Smart Life style cameras

Common clues:

- Generic/OEM OUI
- `6668` Tuya LAN protocol may be present on some devices
- Cloud-app pairing context
- Embedded Linux banners
- Telnet on some low-cost or older devices

Risk note:

Telnet on a camera is a high-risk signal. Recommend isolation, firmware update, and disabling Telnet where possible.
