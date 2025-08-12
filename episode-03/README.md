# Episode 03 — OPNsense Firewall Setup

**Objective:** Deploy OPNsense as the primary firewall and establish a clean, unified LAN with DHCP and AP-backed Wi-Fi.

**Highlights**
- Installed OPNsense from USB (UEFI)
- Assigned interfaces in console (WAN=igb0, LAN=igb1)
- LAN: `192.168.1.1/24`, DHCP `192.168.1.100–192.168.1.200`
- DNS: Cloudflare (1.1.1.1 / 1.0.0.1)
- Integrated Spectrum modem on WAN (DHCP)
- Linksys Hydra Pro in Bridge/AP mode for Wi-Fi
- Verified wired & wireless connectivity
