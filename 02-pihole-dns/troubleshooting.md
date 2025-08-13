
---

**troubleshooting.md**  
```markdown
# Troubleshooting

## LAN not visible under ISC DHCPv4
- Cause: another DHCP/DNS service (Dnsmasq/Kea) active or LAN not bound.
- Fix: disable other DHCP services; enable **ISC DHCPv4 → LAN**.

## Device not in Leases (Pi-hole)
- Cause: VM had a manual/static IP so it never requested DHCP.
- Fix: switch VM to DHCP, then create **static mapping** (MAC → 192.168.50.65, hostname `pihole`).

## DNS outage (clients show “DNS could not be found”)
- Cause: DHCP pointing to Pi-hole while Pi-hole not answering yet.
- Fix: temporarily set DHCP DNS to public (`1.1.1.1`, `9.9.9.9`) → restore internet → fix Pi-hole → switch back to `192.168.50.65`.

## Netplan warning about Open vSwitch
- `ovsdb-server.service is not running` is harmless if OVS isn’t used.

## Useful commands
```bash
sudo systemctl status pihole-FTL
sudo systemctl restart pihole-FTL
sudo ss -lntu | grep ':53'
dig google.com @127.0.0.1
