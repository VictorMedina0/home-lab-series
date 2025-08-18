# Nextcloud Homelab Deployment

This project documents my deployment of **Nextcloud** in my home cybersecurity lab using **Proxmox** and **OPNsense**. The goal is to provide a **secure, self-hosted backup solution** for personal files and mobile photos while gaining hands-on experience with containerization, networking, and data security.

---

## 🚀 Project Overview
- **Platform**: Proxmox (running on my homelab server)
- **Container**: Nextcloud (TurnKey Linux container image)
- **Networking**: Static IP assignment via OPNsense
- **Access**: Local web interface + Nextcloud mobile app
- **Use Case**: Redundant backups for family photos and important files

---

## 🔧 Key Steps

1. **Container Setup**
   - Created a Nextcloud container in Proxmox.
   - Configured resources (CPU/RAM) for scalability.
   - Assigned disk space for storage growth.

2. **Network Configuration**
   - Assigned a **static IP** through OPNsense DHCP settings.
   - Configured gateway and subnet for proper routing.
   - Verified connectivity and DNS resolution.

3. **Trusted Domain Fix**
   - Edited the `config.php` file to include the container’s IP as a **trusted domain**.
   - Verified successful login through web interface.

4. **Client Integration**
   - Connected the Nextcloud mobile app to my server.
   - Verified automatic photo uploads and file sync.
   - Confirmed desktop access for file management.


---

## 💡 Why This Project Matters
- **Data Security** – Keeps personal and family photos protected against device loss or damage.  
- **Networking Practice** – Reinforced static IP setup and containerized service management.  
- **Self-Hosting Experience** – Gained confidence deploying a service I fully control.  

---

## 📌 Next Steps
- Install **Tailscale VPN** for secure remote access to my homelab.  
- Deploy **Zabbix Network Monitoring** for infrastructure visibility.  
- Explore **encryption and alerts** for additional data security.  

---

## 🛠️ Tools Used
- Proxmox VE  
- OPNsense Firewall  
- Nextcloud (TurnKey container)  
- Nextcloud Mobile/Desktop Apps  

---
