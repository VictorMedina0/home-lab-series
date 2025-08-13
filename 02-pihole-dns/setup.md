# Setup Notes

## A. VM + Network checks
- Proxmox NIC: **VirtIO** on **vmbr0**
- Inside Ubuntu:
  ```bash
  ip a                      # shows ens18 with 192.168.10.50/24
  ping -c3 192.168.10.1     # reach OPNsense LAN gateway
B. Install Pi-hole
bash
Copy
Edit
sudo apt update && sudo apt upgrade -y
curl -sSL https://install.pi-hole.net | bash
Upstream DNS: Cloudflare (1.1.1.1 / 1.0.0.1)

After install:

bash
Copy
Edit
sudo systemctl status pihole-FTL
sudo ss -lntu | grep ':53'   # confirm TCP/UDP 53 listening
Web UI: http://192.168.10.50/admin

C. OPNsense – DHCP (ISC) + DNS
ISC DHCPv4 → LAN

Enable DHCP on LAN

Range: 192.168.10.100 – 192.168.10.200

DNS Servers: 192.168.10.50

Save + Apply

Leases → Add static mapping for Pi-hole:

MAC: AA:BB:CC:DD:EE:50

IP: 192.168.10.50

Hostname: pihole

Save + Apply

(Optional) System → Settings → General

DNS Servers: 192.168.10.50

Uncheck “Allow DNS server list to be overridden by DHCP/PPP on WAN”

Save

D. Refresh clients & verify
Windows:

powershell
Copy
Edit
ipconfig /release & ipconfig /renew
nslookup openai.com
From a client direct to Pi-hole:

powershell
Copy
Edit
nslookup openai.com 192.168.10.50
Expect Server to show 192.168.10.50 and sites to resolve; ads blocked.

E. Notes
Pi-hole address obtained via DHCP + static mapping so it appears in Leases and keeps assigned IP.

If DNS fails, temporarily set DHCP DNS to 1.1.1.1 to restore internet while fixing Pi-hole.
