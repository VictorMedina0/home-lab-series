# Step-by-Step Setup

## Install
1. Created bootable OPNsense USB (Etcher).
2. Booted mini PC via **UEFI: SanDisk**, installed OPNsense to SSD (UFS).
3. Removed USB, rebooted into OPNsense.

## Console Configuration
1. **Assign interfaces**:
   - WAN → `igb0` (connected to Spectrum modem)
   - LAN → `igb1` (connected to switch)
2. **Set LAN IP**: `192.168.1.1/24`
   - No gateway on LAN
   - IPv6 skipped for now
3. **Enable DHCP on LAN**: `192.168.1.100–192.168.1.200`
4. Keep **HTTPS** for Web GUI; generate new self-signed cert; restore GUI access defaults.

## Web Wizard (https://192.168.1.1, `root` / `opnsense`)
- Hostname: `OPNsense` | Domain: `internal`
- DNS: `1.1.1.1`, `1.0.0.1`
- WAN: DHCP (leave MAC spoof blank since IP obtained)
- LAN: Confirm static `192.168.1.1/24`, DHCP enabled

## Cabling (Unified)
- Modem → Firewall **WAN**
- Firewall **LAN** → Switch
- Switch → Main PC, Proxmox host, Linksys (Bridge/AP)
- Linksys uplink uses a **LAN** port (not WAN) in bridge mode

## Validation
- Main PC received `192.168.1.110` via DHCP
- Internet accessible; Wi-Fi clients online in `192.168.1.x`
- Dashboard screenshot added (public IP/hostname redacted)
