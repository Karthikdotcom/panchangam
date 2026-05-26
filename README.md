# 🕐 Auspicious Timings

A lightweight, self-contained web app that shows daily Hindu panchangam timings for Sunnyvale, CA — including Rāhu Kālam, Yamagandam, Gulika Kālam, and the auspicious Abhijit Muhūrta window.

## Features

- **Live countdown** to each period starting or ending, updating every second
- **Sunrise & sunset** computed accurately for your location each day
- **6-day Rāhu Kālam outlook** so you can plan ahead
- **No API keys, no internet required** after first load — all calculations run locally in the browser
- **Auto-adjusts for Daylight Saving Time** via your device clock
- **Add to Home Screen** on mobile for an app-like experience

## How the timings are calculated

The day between sunrise and sunset is divided into **8 equal parts**. Each part is assigned to a planet depending on the day of the week — this is the traditional South Indian panchangam method (Drik system).

| Period | Nature | What to avoid |
|---|---|---|
| Rāhu Kālam | Inauspicious | Starting new ventures, travel, investments |
| Yamagandam | Inauspicious | Important decisions, auspicious events |
| Gulika Kālam | Inauspicious | New activities (outcomes tend to repeat) |
| Abhijit Muhūrta | ✅ Auspicious | Nothing — this is the best window of the day |

Sunrise and sunset are computed using the **NOAA solar position algorithm**, which gives accuracy within 1–2 minutes for any location and date, and handles DST automatically.

## Relocating to a different city

Open `panchangam.html` and find the `CONFIG` block near the top of the `<script>` tag:

```js
const LOCATION = {
  name: "Sunnyvale, California",
  lat:   37.3688,
  lng: -122.0363,
};
```

Replace with your city's coordinates (find them on Google Maps — right-click any point → copy coordinates). Everything recalculates automatically.

## Hosting

Hosted on **GitHub Pages** at:
`https://karthikdotcom.github.io/panchangam/`

To run locally, just open `panchangam.html` directly in any browser — no server needed.

## Tech

No frameworks, no dependencies, no build step. Pure HTML + CSS + JS in a single file.

- Solar position: NOAA algorithm (in-browser, no API)
- Fonts: [Fraunces](https://fonts.google.com/specimen/Fraunces) + [Newsreader](https://fonts.google.com/specimen/Newsreader) via Google Fonts
- Hosting: GitHub Pages
# panchangam
