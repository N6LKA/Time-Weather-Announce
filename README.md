# Time and Weather Announcement

![Release Version](https://img.shields.io/github/v/release/N6LKA/Time-Weather-Announce?label=Version&color=f15d24)
![Release Date](https://img.shields.io/github/release-date/N6LKA/Time-Weather-Announce?label=Released&color=f15d24)
![Hits](https://img.shields.io/endpoint?url=https%3A%2F%2Fhits.dwyl.com%2FN6LKA%2FTime-Weather-Announce.json&label=Hits&color=f15d24)
![GitHub Repo Size](https://img.shields.io/github/repo-size/N6LKA/Time-Weather-Announce?label=Size&color=f15d24)

<img src="TimeWeather.png" alt="Time and Weather Logo" height="120">

---

An automated top-of-the-hour time and current weather conditions announcement system for [AllStar](https://allstarlink.org/) nodes, including ASL3 and HamVoIP. Originally developed for HamVoIP AllStar.

Supports US ZIP codes, ICAO airport codes, Canadian postal codes, and international locations. Weather data is sourced from NOAA METAR and Open-Meteo.

---

## Requirements

- AllStar (ASL3 or HamVoIP) installed and configured
- `curl` — pre-installed on most AllStar systems
- `perl` — pre-installed on most AllStar systems
- `bc`, `zip`, `plocate` — installed automatically during setup

---

## Installation & Updates

Run the following command as root or with sudo for both fresh installs and updates:

```bash
bash <(curl -fsSL -H "Cache-Control: no-cache" https://raw.githubusercontent.com/N6LKA/Time-Weather-Announce/main/install.sh)
```

The installer will prompt you for:
- **ZIP code or Airport/ICAO code** — e.g. `90210` or `KJFK`
- **AllStar node number** — your AllStar node number

**Fresh install:** Downloads and installs all scripts and sound files, creates the configuration file, and adds an hourly cron job.

**Existing install detected:** Pre-fills your current location and node number. Press Enter to keep them or type new values, then refreshes all scripts and sound files.

---

## What It Does

- Announces the current local time at the top of every hour
- Retrieves current weather conditions via NOAA METAR or Open-Meteo
- Plays announcements using pre-recorded GSM audio files
- Runs automatically via cron — no manual interaction required after setup

---

## Testing

After installation, test your setup manually:

```bash
/usr/local/sbin/saytime.pl <ZIP_or_AIRPORT> <NodeNumber>
```

Example:
```bash
/usr/local/sbin/saytime.pl 90210 123456
/usr/local/sbin/saytime.pl KJFK 123456
```

---

## Configuration

Edit `/etc/asterisk/local/weather.ini` to customize behavior:

| Setting | Default | Description |
|---|---|---|
| `Temperature_mode` | `F` | `F` for Fahrenheit, `C` for Celsius |
| `process_condition` | `YES` | Announce weather conditions (cloudy, rain, etc.) |
| `default_country` | `us` | Country code for postal code lookups |
| `DEFAULT_PROVIDER` | `auto` | Weather source: `auto`, `metar`, or `openmeteo` |

---

## Credits

| Script | Author(s) |
|---|---|
| `saytime.pl` | D. Crompton (WA3DSP) — original author |
| `weather.sh` | Jory A. Pratt (W5GLE), based on original work by D. Crompton (WA3DSP), modified by Joe (KD2NFC) |
| `install.sh` | Freddie Mac (KD5FMU) and Jory A. Pratt (W5GLE) — original; modified and updated by Larry K. Aycock (N6LKA) |

---

## License

GNU General Public License version 2 (GPL-2.0)

See [LICENSE](LICENSE) for details.
