# Tailscale – Homelab Exit Node (04-Tailscale)

This doc captures my deployment of **Tailscale** in my homelab with an **Exit Node** for secure remote access and optional full-tunnel routing.

## Environment
- **Hypervisor:** Proxmox
- **VM OS:** Ubuntu Server (Linux)
- **VPN:** Tailscale (mesh)
- **Example LAN:** `10.50.60.0/24` (fake), gateway `10.50.60.1`

## Goals
- Encrypted access to internal services (no public exposure)
- Optional full-tunnel via **Exit Node**
- Simple, repeatable setup with minimal moving parts

## Files
- `setup.md` – step-by-step setup I performed
- `troubleshooting.md` – issues I hit and how I fixed them


## Security Notes
- Keep the exit-node VM patched.
- Use SSH keys (disable password auth).
- Limit inbound ports and log access.
