# OPNsense Firewall Setup (Step 1 of Home Lab Rebuild)

This stage covers the installation and initial configuration of **OPNsense** as the primary firewall in my home lab.

---

## What Was Done
- Installed OPNsense on a dedicated mini PC.
- Configured WAN and LAN interfaces from the console.
- Integrated Spectrum WAN for internet access.
- Enabled DHCP on LAN for internal IP assignment.
- Connected LAN to TP-Link 8-Port Managed Switch.
- Completed setup wizard in OPNsense web UI for a clean baseline.

---

## Hardware Used
- **Beelink SER5 Pro** (Ryzen 7 5825U, 32GB RAM, 1TB NVMe)
- **TP-Link TL-SG108E** 8-Port Gigabit Managed Switch
- Spectrum Internet (WAN)

---

## Why This Matters
A firewall is the foundation for a secure and segmented home lab network. OPNsense provides flexibility, advanced rule configuration, and integration with future security tools like Security Onion and Suricata.

---

## Next Steps
1. VLAN configuration.
2. Proxmox setup.
3. IDS/IPS integration.
