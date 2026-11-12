# Focus Tasks — The Warrior's Timetable

A single-file habit and focus tracker with a daily routine timetable, alarms, hydration and exercise counters, a weekly streak and simple analytics.

**Live demo:** [https://yjhacker.github.io/Focus_Tasks/](https://yjhacker.github.io/Focus_Tasks/)

Everything is stored in `localStorage` — there is no account, backend or network sync. Clearing site data resets the app.

## Features

- **Daily routine timetable** — add a routine with a start time, end time and a custom alarm message.
- **Alarm reminders** — browser notifications and an in-app "Time to Rise!" modal when a routine starts.
- **Hydration tracker** — tap a glass each time you drink water; the day's total is saved.
- **Exercise tracker** — log exercise sessions and see the daily count.
- **Weekly streak** — mark each day and keep the chain alive.
- **Analytics tab** — daily reports and a seven-day bar chart built from your own entries.
- **"Do not burn out" reminders** — periodic nudges if you have been going too long.
- **Responsive layout** — bottom navigation on mobile, wider layout on desktop.
- **Offline-friendly** — after the CDN assets load, no server is required.

## Stack

- HTML5 + vanilla JavaScript
- Tailwind CSS (CDN)
- Font Awesome (CDN)
- Browser `Notification` API
- `localStorage` for persistence

No build step, no dependencies to install.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## How it works

The whole app lives in `index.html`:

| Area | Responsibility |
|---|---|
| `userData` | Single state object: routines, water, exercise, streak, analytics, profile |
| `saveState()` / `loadState()` | JSON serialization to `localStorage` |
| `renderTimetable()` | Builds today's routine list and completion buttons |
| `checkAlarms()` | Fires notifications when a routine start time passes |
| `renderAnalytics()` | Aggregates daily/weekly data into report cards and bars |

Data is keyed by date (`YYYY-MM-DD`), so each day starts fresh while history remains available in the analytics tab.

## Privacy

All data stays in your browser. There is no backend, analytics script or external data store. The only network requests are the Tailwind and Font Awesome CDNs.

To reset: DevTools → Application → Local Storage → delete the `userData` key, or clear site data for the page.

## Limitations

- Single HTML file; not modular and has no automated tests.
- No multi-device sync or export.
- Browser notifications require permission and only fire while the page is open.
- Clearing browser storage permanently deletes the data.

## License

MIT © 2026 Yash Chauhan
