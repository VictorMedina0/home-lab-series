# Troubleshooting Notes – OPNsense Firewall Setup

---

## WAN IP missing initially
- **Symptom:** WAN address not assigned.
- **Cause:** Spectrum modem not passing IP until reboot.
- **Fix:** Power cycle modem and firewall.

---

## Auto-detect didn’t assign LAN correctly
- **Symptom:** Only WAN detected after install.
- **Fix:** Assign interfaces manually in OPNsense console.

---

## Router blinking red (Linksys cosmetic issue)
- **Symptom:** Linksys router LED stays red.
- **Cause:** Cosmetic only, bridge mode still active.
- **Fix:** Confirm Wi-Fi works and LAN uplink is live.

---

## General OPSEC
- Redacted public IPs and sensitive details from screenshots.
