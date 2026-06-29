# NAS Vendors and Patterns

Use this file to identify NAS devices and storage appliances from service combinations, hostnames, and banners.

## General NAS indicators

Common ports:

- 22
- 80
- 443
- 445
- 548
- 2049
- 5000
- 5001

Common clues:

- SMB on `445`
- NFS on `2049`
- AFP on `548`
- Web management UI
- Backup, media, or sync services
- Hostnames containing `nas`, `diskstation`, `qnap`, `storage`, or `backup`

## Synology

Common ports:

- 80
- 443
- 445
- 5000
- 5001
- 548
- 2049

Common clues:

- DSM web UI on `5000` or `5001`
- Hostnames such as `DiskStation`
- SMB, NFS, AFP, media, and backup services

## QNAP

Common clues:

- Web management UI
- SMB/NFS/AFP services
- QNAP-specific HTTP titles or certificates
- Media and backup service ports

## TrueNAS / FreeNAS

Common clues:

- Web UI on `80` or `443`
- SMB on `445`
- NFS on `2049`
- SSH on `22`
- Hostnames containing `truenas`, `freenas`, or storage-related names

## Asustor

Common clues:

- Web management UI
- SMB/NFS/AFP services
- Hostnames or titles containing `ADM` or `ASUSTOR`

## TerraMaster

Common clues:

- Web management UI
- SMB/NFS services
- Hostnames or titles containing `TOS` or `TerraMaster`

## Risk notes

NAS devices often contain sensitive data and credentials.

Escalate risk if:

- Admin UI is internet exposed
- SMB is exposed beyond trusted networks
- Firmware is outdated
- Default credentials may still be in use
- Unknown NAS appears on a trusted LAN

Recommended actions:

- Confirm owner and physical device
- Update firmware
- Disable unused services
- Enforce strong admin credentials
- Restrict admin UI to management networks
- Do not expose SMB/NFS to the internet
- Ensure backups exist before major remediation
