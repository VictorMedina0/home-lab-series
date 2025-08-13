# 02 – Pi-hole DNS & Network-Wide Ad Blocking

## Overview
Set up **Pi-hole** on an Ubuntu Server VM (Proxmox) and made it the primary DNS for the LAN via **OPNsense (ISC DHCPv4)**. The goals: block ads/malicious domains for all devices and practice DHCP/DNS integration and troubleshooting.

## Result
- Pi-hole running and listening on **TCP/UDP :53**  
- Reserved IP **<PIHOLE_IP>** with hostname **pihole** in OPNsense DHCP (static mapping)  
- DHCP hands out **<PIHOLE_IP>** as DNS to clients  
- Name resolution and ad-blocking verified on multiple devices

## VM Specs (Proxmox)
- Ubuntu Server (netplan NIC: `ens18` on `vmbr0`)
- vCPU: 2 • RAM: 2 GB • Disk: 32 GB

## Next
- DoH/DoT for upstream privacy
- Conditional forwarding for local names
- Grafana/Prometheus for DNS metrics

