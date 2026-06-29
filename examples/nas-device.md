# Example: NAS or File Server

This is a generic, anonymised example for a storage device or small server.

## Input evidence

```text
Unknown device on LAN
IP: 192.168.1.90
MAC: AA:BB:CC:DD:EE:22
OUI/vendor: Synology, QNAP, Intel, Realtek, or unknown
DHCP hostname: diskstation, nas, storage, or unknown
Open ports: 22/tcp, 80/tcp, 443/tcp, 445/tcp, 5000/tcp, 5001/tcp
User context: User has a backup/storage box but is unsure of its IP
```

## Analysis

### Known facts

- SMB on `445/tcp` indicates Windows file sharing, Samba, NAS, or printer/file-share functionality.
- `5000/tcp` and `5001/tcp` are common Synology DSM ports.
- SSH suggests an administrative interface or embedded Linux base.
- HTTP/HTTPS may expose web management.

### Likely identities

| Rank | Hypothesis | Confidence | Why |
| ---: | --- | ---: | --- |
| 1 | Synology NAS | High if `5000/5001` and DiskStation-like hostnames/titles appear | Port combination strongly matches Synology DSM |
| 2 | QNAP or other NAS | Medium | SMB + web management + SSH fits NAS broadly |
| 3 | Linux file server | Medium | SMB + SSH + web services could be a general Linux server |
| 4 | Printer or media appliance with SMB | Low | Possible, but 5000/5001 increases NAS confidence |

## Risk

Risk level: High until ownership and exposure are confirmed.

Reasons:

- NAS devices often contain sensitive backups, documents, media, and credentials.
- SMB and web admin interfaces are high-value services.
- Risk increases sharply if admin interfaces are internet-exposed or credentials are weak/default.

## Safe next checks

Check HTTP titles and headers:

```bash
nmap --script=http-title,http-headers -p 80,443,5000,5001 192.168.1.90
```

Check SMB service info without attempting login:

```bash
nmap -Pn -sV -p 445 --script=smb-protocols,smb2-security-mode 192.168.1.90
```

Check router/DHCP and physical inventory:

```bash
arp -a
ip neigh
```

Do not attempt SMB credential guessing.

## Recommended action

1. Confirm whether the device is expected and who owns it.
2. Check vendor UI for firmware updates.
3. Ensure admin UI is not exposed to the internet.
4. Enforce strong unique admin credentials and MFA if supported.
5. Disable unused file-sharing protocols.
6. Restrict SMB/admin access to trusted management clients.
7. Verify backups and snapshot/ransomware protection.
8. Segment NAS devices away from untrusted IoT networks.

## What would improve confidence

- HTTP title such as Synology DSM or QNAP
- DHCP hostname such as `diskstation`
- SMB server string
- Physical device label/model
- Router inventory or controller metadata
