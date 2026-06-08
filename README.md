# 🕐 Auspicious Timings

A self-contained Hindu panchangam web app for Sunnyvale, CA. Shows daily timings (Rāhu Kālam, Yamagandam, Gulika Kālam, Abhijit Muhūrta), lunar observances (Ekādaśī, Pradoṣam, Kṛttikā, Anuṣam), and a monthly calendar marking observance days — all computed locally in the browser.

🔗 **Live:** [karthikdotcom.github.io/panchangam](https://karthikdotcom.github.io/Auspicious-Timings/)

## Features

### Daily timings

- **Live countdown** to each period starting or ending, updating every second
- **Sunrise & sunset** computed accurately for your location each day
- **6-day Rāhu Kālam outlook** so you can plan ahead
- Live clock with seconds, AM/PM, and timezone

### Lunar observances

- **Ekādaśī** (11th tithi · fast & devotion)
- **Pradoṣam** (13th tithi · Shiva worship)
- **Kṛttikā** (Krittika nakshatra · Murugan / Karthikai)
- **Anuṣam** (Anuradha nakshatra · Mahā Periyavā)
- Shows today's tithi & nakshatra at sunrise **and** the current moment
- Countdown to each observance's next occurrence

### Monthly calendar

- Visual grid of the current month with **E / P / K / A** markers on observance days
- Click any day to see what's on it; hover for a quick tooltip
- Navigate to previous / future months with the arrows

### Self-contained

- **No API keys, no internet required** after first load — all astronomy runs locally
- **Auto-adjusts for Daylight Saving Time** via your device clock
- **Add to Home Screen** on mobile for an app-like experience

## How the timings are calculated

### Daily periods (Rāhu Kālam etc.)

The day between sunrise and sunset is divided into **8 equal parts**. Each part is assigned to a planet depending on the day of the week — the traditional South Indian panchangam method (Drik system).

| Period          | Nature        | What to avoid                                |
| --------------- | ------------- | -------------------------------------------- |
| Rāhu Kālam      | Inauspicious  | Starting new ventures, travel, investments   |
| Yamagandam      | Inauspicious  | Important decisions, auspicious events       |
| Gulika Kālam    | Inauspicious  | New activities (outcomes tend to repeat)     |
| Abhijit Muhūrta | ✅ Auspicious | Nothing — this is the best window of the day |

Sunrise and sunset use the **NOAA solar position algorithm** — accurate within 1–2 minutes.

### Lunar observances

Computed from the Moon's position in the sky using **Jean Meeus's lunar algorithm** (chapter 47 of _Astronomical Algorithms_):

- **Tithi** (lunar day, 1–30) → derived from the Sun↔Moon angular separation. Ekādaśī is the 11th, Pradoṣam the 13th.
- **Nakshatra** (lunar mansion, 1 of 27) → derived from the Moon's sidereal longitude using the **Lahiri (Chitrapaksha) ayanamsa** — the Government of India standard.

Validated against drikpanchang / prokerala: tithi transitions match within ~3 minutes, nakshatra transitions exact. Today's status is evaluated at **local sunrise** (traditional rule), with a live "right now" indicator alongside.

> Note: because evaluation uses your _local_ sunrise, the app may show a different tithi/nakshatra than Indian panchangam sites for the same calendar day — the two are offset by ~12 hours, and both are correct for their respective sunrise.

## Relocating to a different city

Open `index.html` and find the `CONFIG` block near the top of the `<script>` tag:

```js
const LOCATION = {
  name: "Sunnyvale, California",
  lat: 37.3688,
  lng: -122.0363,
};
```

Replace with your city's coordinates (right-click any point in Google Maps to copy them). Everything recalculates automatically.

## Running locally

Just open `index.html` in any modern browser — no server, no build step, no install. Or use GitHub Pages (current setup) for a hosted URL you can add to your phone's home screen.

## Tech

No frameworks, no dependencies, no build step. Pure HTML + CSS + JS in a single file.

- **Solar position** — NOAA algorithm (Reda & Andreas)
- **Lunar position** — Meeus, abridged ELP-2000
- **Ayanamsa** — Lahiri (Chitrapaksha), calibrated to Indian govt ephemeris
- **Fonts** — [Fraunces](https://fonts.google.com/specimen/Fraunces) + [Newsreader](https://fonts.google.com/specimen/Newsreader) via Google Fonts
- **Hosting** — GitHub Pages
