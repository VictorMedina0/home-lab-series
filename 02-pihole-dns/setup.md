# Setup Notes

## A. VM + Network checks
- Proxmox NIC: **VirtIO** on **vmbr0**
- Inside Ubuntu:
  ```bash
  ip a                 # shows ens18 with <PIHOLE_IP>/24
  ping -c3 <OPNSENSE_GATEWAY> # reach OPNsense LAN gateway

## B. Install Pi-hole
sudo apt update && sudo apt upgrade -y
curl -sSL https://install.pi-hole.net | bash

Upstream DNS: Cloudflare (1.1.1.1 / 1.0.0.1)

After install:

sudo systemctl status pihole-FTL
sudo ss -lntu | grep ':53'   # confirm TCP/UDP 53 listening
# Web UI: http://<PIHOLE_IP>/admin

## C. OPNsense – DHCP (ISC) + DNS

ISC DHCPv4 → LAN

Enable DHCP on LAN

Range: 192.168.1.100 – 192.168.1.200

DNS Servers: <PIHOLE_IP>

Save + Apply

Leases → Add static mapping for Pi-hole:

MAC: <PIHOLE_MAC>

IP: <PIHOLE_IP>

Hostname: pihole

Save + Apply

(Optional) System → Settings → General

DNS Servers: <PIHOLE_IP>

Uncheck “Allow DNS server list to be overridden by DHCP/PPP on WAN”

Save

## D. Refresh clients & verify

Windows:

ipconfig /release & ipconfig /renew
nslookup openai.com

From a client direct to Pi-hole:

nslookup openai.com <PIHOLE_IP>

Expect Server to show <PIHOLE_IP> and sites to resolve; ads blocked.

## E. Notes

Pi-hole address obtained via DHCP + static mapping so it appears in Leases and keeps assigned IP.

If DNS fails, temporarily set DHCP DNS to 1.1.1.1 to restore internet while fixing Pi-hole.
