# Network Topology – Home Lab

**Firewall:** OPNsense 25.7  
**Firewall Hardware:** Mini PC (Intel Celeron J3160, 4 cores)  
**Switch:** TP-Link TL-SG108E (Easy Smart Managed Switch)  
**Internet:** Spectrum (bridged mode modem)  
**Primary LAN Gateway:** 192.168.1.1/24  

## Topology
- Modem (Bridge Mode) → Firewall WAN  
- Firewall LAN → TP-Link Managed Switch  
- Switch → Home devices (wired + wireless via existing Wi-Fi access point)  

## VLAN Planning
- VLAN 10 – Management  
- VLAN 20 – Servers / Lab  
- VLAN 30 – IoT  
- VLAN 40 – Guest Wi-Fi
