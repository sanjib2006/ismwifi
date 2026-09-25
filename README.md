# ismwifi
Auto-login and keep-alive tool for IIT (ISM) campus Wi-Fi on Linux.

- Runs as a persistent `systemd --user` background service.
- Automatically starts on boot / login and survives terminal closure.
- Checks Wi-Fi every 15s and authenticates immediately upon detecting `ISM-Campus-Wi-Fi`.
- Detects system sleep / suspend and re-authenticates automatically on wake.
- Probes internet health every 30s and recovers instantly if the campus gateway drops the session.
- Detects IP address changes and re-authenticates automatically.
- Re-authenticates every 60 minutes to prevent timeouts.
- Idles silently on other networks (hotspots / home Wi-Fi) without touching your Wi-Fi interface.

---

## Start

### Option 1: Direct Download

```bash
mkdir -p ~/.local/bin && curl -fsSL https://raw.githubusercontent.com/sanjib2006/ismwifi/main/ismwifi -o ~/.local/bin/ismwifi && chmod +x ~/.local/bin/ismwifi && ismwifi
```

### Option 2: Clone from GitHub

```bash
git clone https://github.com/sanjib2006/ismwifi.git
cd ismwifi
chmod +x ismwifi
./ismwifi
```

On first run, it will prompt for your admission number and password once. Credentials are saved locally in `~/.config/ismwifi/credentials` (`chmod 600`, readable only by your user).

---

## Usage

From any terminal:

```bash
# Start and enable background auto-login
ismwifi

# Stop and disable it (will not run in background or on reboot)
ismwifi kill

# Restart the background service
ismwifi restart

# Check current status (SSID, IP, service state)
ismwifi status

# View live service logs
ismwifi logs

# Log out of campus portal using saved session cookie & stop auto-login
ismwifi logout

# Update stored credentials
ismwifi config

# Uninstall service and binary
ismwifi uninstall
```
