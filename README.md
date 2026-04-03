# Pickleball Haven Booker

A standalone OpenClaw skill to automate court reservations at Pickleball Haven Lake Forest via CourtReserve.

## 🚀 Installation

1.  **Clone or Copy** this folder into your OpenClaw workspace:
    `~/.openclaw/workspace/skills/pickleball-booker/`

2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    playwright install chromium
    ```

3.  **Configure Credentials:**
    Create a `.env` file in this directory:
    ```env
    COURTRESERVE_EMAIL=your@email.com
    COURTRESERVE_PASS=yourpassword
    ```
    *Alternatively, use macOS Keychain with the service name `openclaw-pickleball-booker`.*

## ⚠️ Membership Limitations (AM Membership)

This booker is hardcoded for the **AM Open Play membership** at Pickleball Haven Lake Forest. It will only attempt to book sessions that match all of the following:

| Constraint | Value | Why |
|---|---|---|
| Session type | **Open Play only** | AM membership doesn't cover reserved courts |
| Cost | **Free only** | AM membership has no drop-in fee — paid sessions are skipped |
| Start time | **Before 2:30 PM** | AM membership cutoff; sessions at or after 2:30 PM are excluded |
| Booking window | **Up to 7 days out** | CourtReserve site limit for this club |
| Target-time tolerance | **±45 minutes** | When `--target-time` is set, only books sessions within 45 min of the requested time |

If you have a different membership tier (e.g., Full or PM), these filters will cause the script to report no available sessions even when courts exist. You'd need to adjust `MAX_START_H`, `MAX_START_M`, and the `is_free` check in `pickleball_booker.py`.

## 🛠️ Usage

### From the CLI
- **Check today's availability (Dry Run):**
  `python3 pickleball_booker.py --dry-run`
- **Book for tomorrow at 8:00 AM:**
  `python3 pickleball_booker.py --date "2026-04-03" --target-time "8:00 AM"`

### Via the OpenClaw Agent
Ask your agent:
- "Check if there are any pickleball sessions tomorrow morning."
- "Book me a court for 9 AM today at Pickleball Haven."

## 📁 How to Share

1.  **GitHub:** Push this folder to a new repo. Others can install it with `openclaw skills install <your-repo-url>`.
2.  **Zip:** Zip this entire folder (excluding `.env`) and send it to a friend.

---
**⚠️ Security Note:** Never share your `.env` file. It contains your personal login credentials.
