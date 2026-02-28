# Local Time Tracker

A lightweight, local-only time tracker that runs as a single HTML file in your browser. No server, no installation, no deployment — just double-click and go.

Built for tracking time across work categories with automatic syncing to an Excel spreadsheet that builds up over time.

## Features

- **One-click timers** — tap a category to start, tap again (or press Space) to stop
- **Keyboard shortcuts** — press 1–9 to start a timer, Space to stop, E to edit the last entry
- **Optional notes** — prompted after each timer stop
- **Persistent Excel sync** — link a `.xlsx` file once and entries auto-sync to it. Today's data is always overwritten from the browser; older days are preserved
- **Edit last entry** — fix start/end times, category, or notes without opening Excel
- **Daily & weekly summary** — live totals and per-category breakdowns at the bottom of the page
- **Fully local** — all data stays in your browser (localStorage) and your local spreadsheet. Nothing leaves your machine

## Getting Started

1. Download `timetracker.html` and open it in **Chrome** or **Edge**
2. Click **Link file** and either select the included `timesheet.xlsx` template or create a new file
3. Start tracking — click a category or press its number key

That's it. The file handle persists in your browser, so next time you open the tracker it reconnects to the same spreadsheet automatically.

## Files

| File | Purpose |
|------|---------|
| `timetracker.html` | The tracker — open in your browser |
| `timesheet.xlsx` | Template spreadsheet with the correct column headers |

## Spreadsheet Format

The tracker reads and writes the following columns:

| Column | Description |
|--------|-------------|
| Date | e.g. `28 Feb 2026` |
| Category | The timer category name |
| Start | `HH:MM` format |
| End | `HH:MM` format |
| Hours | Integer hours component |
| Minutes | Integer minutes component |
| Seconds | Integer seconds component |
| Duration (decimal hrs) | Total duration as a decimal (e.g. `1.5` = 1h 30m) |
| Note | Optional free text |

You can manually add or edit rows in the spreadsheet for previous days. The tracker only overwrites today's rows when syncing — everything else is left untouched.

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `1`–`9` | Start/switch to category by number |
| `Space` | Stop the active timer |
| `E` | Edit the last entry |

Shortcuts are disabled when typing in an input field or when a modal is open.

## How Syncing Works

- **Auto-sync** happens each time you stop a timer and save/skip the note
- **Forced sync** happens after editing or deleting an entry
- When syncing, the tracker reads the Excel file, removes all rows for today's date, and replaces them with the current browser entries. Previous days are never touched
- If the browser loses file permission (e.g. after a restart), you'll be prompted to re-grant access on the next save — one click

## Requirements

- **Chrome** or **Edge** (uses the File System Access API for persistent file linking)
- Firefox works for tracking but will download a new file each time instead of syncing to a linked one

## Customisation

Default categories are set in the `defaultState()` function inside the HTML file. You can also add/remove categories directly in the UI — click **+ Category** or right-click a category to remove it.

## License

MIT
