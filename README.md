# CallHome — Never Ring at the Wrong Hour

A world clock and best-time-to-call planner for families spread across time zones. One page, no backend, no sign-up — everything runs on your device and your data never leaves it.

**Live:** https://abhiramunni.github.io/callhome/

## What it does

- **World clock wall** — live ticking clocks for the places your people live (Bengaluru home + Casoria/Italy, Dubai, London, Singapore, Toronto, Sydney by default), each with an analog face, digital time, date, day/night pill, and offset against home. Add any of 14 time zones.
- **Best-time finder** — pick two people and a 24-hour day wheel shows when each is awake and where the hours overlap, in plain words and in both of their local times. Awake hours are editable per person.
- **Your people** — one card per person: their time right now, awake/asleep verdict, best window to call today (your time and theirs), editable awake hours, last-called date, and one-tap "Mark called".
- **Meeting planner** — pick a date and time in Bengaluru and see it in every time zone on your wall, with same-day / next-day labels and awake-hours notes. Copy the plan to paste into the family group.
- **Call log** — this week's calls on a Mon–Sun strip, a day streak that only grows if you keep calling, recent calls, and a copy-this-week summary.
- **Plain-language guides** — how time zones work, why Europe's clocks move and India's don't, the golden window for India–Europe and India–North America calls, when not to call, cheapest ways to call abroad, and birthdays across the date line.

## Time-zone maths, verified

All conversions are computed on-device with the browser's IANA time-zone database (`Intl.DateTimeFormat`). Hand-checked for 23 Nov 2026 (winter time in Europe/North America, Sydney on AEDT):

| 7:00 PM IST is… | |
|---|---|
| Casoria, Italy | 2:30 PM |
| London, UK | 1:30 PM |
| Dubai, UAE | 5:30 PM |
| Singapore | 9:30 PM |
| Toronto, Canada | 8:30 AM |
| Sydney, Australia | 12:30 AM next day |

Best window with Devika (Casoria, awake 7:00 AM–10:30 PM local): **11:30 AM – 10:30 PM IST** (7:00 AM – 6:00 PM her time). With Meera (Toronto, awake 8:00 AM–10:00 PM local): two windows, **7:00 – 8:30 AM** and **6:30 – 10:30 PM IST**.

## Design

Warm editorial palette (ivory paper, espresso ink, bronze and terracotta), Fraunces + Inter, a 4-second cinematic intro with tap-to-skip (quick on return visits), a 3-step onboarding tour, Ken Burns drift on the two AI-generated warm-editorial photos, and a day wheel drawn live in SVG.

## Privacy

No account, no analytics, no network calls for the app itself. People, places, awake hours and call logs live in `localStorage` under `callhome-v1`. "Remove samples" deletes the four seeded example people; "Erase everything" resets the app.

## Files

- `index.html` — the whole app (single file; photos are `callhome-hero.webp` and `callhome-flatlay.webp` in the repo root)
- `chunks/c01–c15` — the source chunks the page is assembled from
- `qa-test.js` — 67 headless jsdom assertions (run with `node qa-test.js`)

## QA

67/67 jsdom assertions pass, `node --check` clean, zero uncaught JS errors, no pictographic emoji. Includes a real bug found and fixed before publishing: the add-person sheet's inline `display:flex` overrode its `hidden` attribute, so it would have shown on page load.
