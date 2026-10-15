# Date Difference Calculator — Inclusive & Exclusive

A single-file, zero-dependency web app that tells you exactly how much time
passed between two dates — in years, months, days, hours, minutes and seconds —
shown side-by-side as **exclusive** (elapsed) and **inclusive** (both endpoints counted).

Just open `index.html`. No build step, no packages, works offline.

## Run it

**Option A — double-click (easiest):**
```
open index.html   # or double-click it in Finder
```

**Option B — local server:**
```bash
cd date-difference-app
python3 -m http.server 8135
# → http://localhost:8135/index.html
```

## Exclusive vs inclusive

| mode | formula | example (Jan 1 → Jan 2) |
|---|---|---|
| 🟢 Exclusive (elapsed) | `End − Start` | 1 day / 24 hours |
| 🟡 Inclusive (both ends) | `End − Start + 1 day` | 2 days / 48 hours |

Each card shows: calendar breakdown (years, months, days, hours, mins, secs —
leap-year and month-length aware), total days / hours / minutes / seconds,
weeks + days, and years + days + hours.

If End is before Start, the dates are auto-swapped with a note.

## Features

- Start date + end date, with optional start/end times (`Include time` toggle)
- `Calculate difference`, `⇅ Swap dates`, `Today → Now`
- Quick presets: Last 7 / 30 / 365 days, Jan 1 → Today
- Shareable URL (state lives in the query string, synced live as you edit)
- `Copy link` button with clipboard fallback for `file://`
- Back/forward button support (`popstate` restores state from the URL)

## Shareable URL

Canonical format:

```
?start=YYYY-MM-DD&end=YYYY-MM-DD&startTime=HH:MM&endTime=HH:MM
```

Examples:

```
index.html?start=2020-01-01&end=2026-10-15&startTime=09:30&endTime=17:45
index.html?start=2020-01-01            # end defaults to today
index.html?start=2020-01-01&end=       # empty end → today
```

Rules:

- **Missing, empty, or invalid `end` → today** (local date). The address bar
  is synced to the resolved value on calculate.
- Aliases accepted when reading: `startDate` / `start_date` / `from` for start,
  `endDate` / `end_date` / `to` for end, `start_time` / `end_time` variants for times.
- Times accept `HH:MM` or `HH:MM:SS`; times are only added to the URL when
  `Include time` is checked.

## Files

| file | what |
|---|---|
| `index.html` | the whole app: layout, styles, and logic in one file |
| `README.md` | this file |
