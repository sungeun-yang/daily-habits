# Daily Five

A minimal personal habit tracker designed to live on your iPhone home screen. No account, no server, no app store — just a single HTML file hosted on GitHub Pages.

![Daily Five](https://img.shields.io/badge/platform-iOS%20Safari-lightgrey) ![License](https://img.shields.io/badge/license-MIT-green)

## What it tracks

Each day you check off up to four things:

- **Exercise** — aerobic or weight training (mutually exclusive, color-coded in the calendar)
- **No snacking** — stayed off between-meal snacks
- **Time with kids** — meaningful, present time
- **Bible reading** — daily reading done

The calendar shows a 2×2 dot grid on each day. Filled dots mean done; the exercise dot changes color depending on whether you ran or lifted. A streak counter at the bottom shows consecutive complete days and a 7-day history.

## Live demo

👉 [your-username.github.io/daily-five](https://your-username.github.io/daily-five)

## Install on iPhone

This app is designed to run as a full-screen web app from your home screen, with no browser chrome.

1. Open the link above in **Safari** (not Chrome)
2. Tap the Share button → **Add to Home Screen**
3. Tap Add

It will launch full-screen like a native app.

## Data and backup

There is no cloud sync. Your data lives in Safari's `localStorage` — it loads instantly and saves automatically on every tap.

Because `localStorage` can be cleared by iOS under low storage conditions or when you clear Safari's browsing data, the app includes a manual backup system. Tap the **↑ upload icon** (top right) to export your data as a `daily-five.json` file via the iOS Share Sheet — save it to Files or iCloud Drive. Tap the **↓ download icon** to restore from that file on a new device or after a reinstall.

A red dot on the upload button means you have local changes not yet saved to a backup file. The app also reminds you on next open if you closed it with unsaved changes.

The JSON file is human-readable and easy to inspect or edit if needed.

## Customization

The five habits are hardcoded but easy to change. In `index.html`, find the `BOOL_HABITS` array and `EX_CHOICES` array near the top of the `<script>` block and edit the labels. Colors are defined as CSS variables at the top of the `<style>` block.

## Deployment

The app is a single self-contained HTML file with no dependencies, build step, or package manager.

To host your own copy on GitHub Pages:

1. Fork this repository or create a new one and upload `index.html`
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch**, branch `main`, folder `/`
4. Your app will be live at `https://[username].github.io/[repo-name]/` within a minute

## Technical notes

- Runs entirely in the browser — no backend, no database, no tracking
- Calls `navigator.storage.persist()` on load to request that iOS treat `localStorage` as persistent rather than evictable
- Export uses the Web Share API (`navigator.share`) on iOS for native Share Sheet integration, with a download fallback for desktop browsers
- Light and dark mode follow the system setting automatically via `prefers-color-scheme`
- Safe area insets are respected for notch and home indicator on all iPhone models
- Tested on iPhone SE (3rd generation) and iPhone 15

## License

MIT — free to use, modify, and redistribute.
