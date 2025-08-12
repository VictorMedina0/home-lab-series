# Troubleshooting Notes

## WAN IP missing initially
- **Symptom:** WAN address blank.
- **Cause:** Spectrum modem MAC lock on previous router.
- **Fix:** Power cycle modem (unplug coax ~5–10 min), reboot modem first, then firewall.

## Auto-detect didn’t assign LAN
- **Symptom:** Only WAN assigned; no LAN IP.
- **Fix:** Console → Assign interfaces (WAN=igb0, LAN=igb1) → Set LAN IP, enable DHCP.

## Router blinking red in bridge mode
- **Symptom:** Linksys LED blinking red despite working Wi-Fi.
- **Cause:** Cosmetic in Bridge/AP mode (WAN LED logic).
- **Fix:** Confirm LAN uplink to a **LAN** port; verify clients get `192.168.1.x` + internet.

## General OPSEC
- Redacted public IPs and hostnames in screenshots.
