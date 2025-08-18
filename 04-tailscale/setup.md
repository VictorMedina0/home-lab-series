# Setup – Exact Steps I Took

> All example IPs are **fake**. Replace `10.50.60.0/24` with your LAN and `<WAN_IF>` with your VM’s outbound interface (e.g., `eth0`, `enp3s0`).

## 1) VM prep
- Proxmox → Create Ubuntu Server VM (2 vCPU, 2–4GB RAM, 10–20GB disk).
- Update base OS:
  ```bash
  sudo apt update && sudo apt upgrade -y

Install & start Tailscale
curl -fsSL https://tailscale.com/install.sh | sh
sudo systemctl enable --now tailscaled

Join my tailnet
sudo tailscale up
# Follow the auth URL printed in the terminal to sign in.

Enable IP forwarding
# Persist forwarding
sudo sed -i 's/^#\?net.ipv4.ip_forward.*/net.ipv4.ip_forward=1/' /etc/sysctl.conf
sudo sed -i 's/^#\?net.ipv6.conf.all.forwarding.*/net.ipv6.conf.all.forwarding=1/' /etc/sysctl.conf
sudo sysctl -p

Advertise Exit Node + Subnet route (one command)

I avoid --reset so flags don’t get cleared.

sudo tailscale up \
  --advertise-exit-node \
  --advertise-routes=10.50.60.0/24

Approve on the admin side
Open the Tailscale admin → select this VM:
Approve the advertised subnet route (10.50.60.0/24)
Enable this device as an Exit Node

Select the exit node on clients
On my laptop/phone → Tailscale client:
Enable Use exit node → select the VM
Optional: Allow LAN access if I want local breakout

Verify

On the VM:
tailscale status
Expect to see labels like exit node and subnets: 10.50.60.0/24.
From a client with exit node enabled:
Visit an IP checker (should show home egress IP)
Reach an internal host (e.g., 10.50.60.20) if subnet routing is allowed

Summary of what I configured
Ubuntu VM on Proxmox
Tailscale installed + authenticated
IP forwarding enabled
Exit Node + subnet 10.50.60.0/24 advertised
Admin approvals applied (route + exit node)
NAT rules added when full-tunnel is required
Clients set to use the exit node
