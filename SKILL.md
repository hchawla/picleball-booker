---
name: pickleball-booker
description: Automates court reservations at Pickleball Haven Lake Forest (site ID 13464) via CourtReserve.
---

# Pickleball Booker

A standalone tool for booking FREE AM Open Play sessions at Pickleball Haven Lake Forest.

## Capabilities
- **Check Availability:** Scans for free open play sessions for today or tomorrow.
- **Auto-Book:** Automatically registers for a session if one is available and free.
- **Target Time:** Prioritizes sessions closest to a specific time (e.g., 8:00 AM).

## Usage
The agent calls this via bash:
```bash
python3 pickleball_booker.py [--dry-run] [--tomorrow] [--target-time "HH:MM AM/PM"]
```

## Setup (User)
- Requires `playwright` (`pip install playwright` + `playwright install chromium`).
- Requires credentials in `.env` or macOS Keychain:
    - `COURTRESERVE_EMAIL`
    - `COURTRESERVE_PASS`
