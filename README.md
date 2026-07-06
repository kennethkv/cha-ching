# Cha-Ching 🧧

A fast, private, chat-style personal finance tracker built for Brunei. Type what you spent the way you'd text a friend — **`Lunch 5`**, **`Salary 1200`**, **`Save bibd 500`** — and Cha-Ching figures out the type, category, and account for you.

**Live app:** https://kennethsiaw.github.io/cha-ching/

Add it to your phone's home screen (it's an installable PWA) and it opens like a native app, fully offline.

## Why it's different

- **No forms, no dropdowns.** One text box. Auto-detects expense / income / savings / investment gain from your words, in **English, Malay, and Chinese**.
- **Local-first & private.** Everything lives in your browser (`localStorage`). Nothing is sent anywhere unless you turn on backup.
- **Optional Google Sheets backup.** Sign in with Google to mirror your ledger, accounts, transfers, and gains to a private Sheet on your own Drive (uses the narrow `drive.file` scope — the app only ever touches the one file it creates).
- **Built for Brunei.** Default currency BND; categories and bank names (BIBD, Baiduri, TAIB, DST Money, TabungHaji) match local life out of the box.

## How to use it

Type an entry and hit send:

| You type | Cha-Ching records |
|---|---|
| `Lunch 5` | Expense · Food & Drinks · today |
| `Salary 1200` | Income · Salary |
| `Save bibd 500` | Savings · BIBD |
| `Claims 155` | Income · Reimbursement |
| `Dividend 40` | Investment gain (credits your investment account) |
| `Yesterday coffee 3` | Expense dated to yesterday |
| `6/15 petrol 40` | Expense dated 15 June |
| `Delete` | Removes your last entry |

If the category isn't obvious, Cha-Ching asks you to pick one — and remembers nothing you didn't confirm.

### Tabs

- **Track** — the chat box where you log everything.
- **Fixed** — recurring monthly items (rent, subscriptions) auto-posted each month.
- **Stats** — spending by category and daily trend.
- **Records** — full searchable ledger, filterable by type.
- **Settings** — language, currency, categories, accounts, and Google Sheets backup.

## Installing

There's nothing to install and no account to create. Just:

1. Open **https://kennethsiaw.github.io/cha-ching/** on your phone.
2. Add it to your home screen (Safari: Share → *Add to Home Screen*; Chrome: menu → *Add to Home screen*).

It now opens like a normal app and works offline. Your data is saved right in the browser on your device — so keep using the same shortcut and it'll all be there. (Turn on Google Sheets backup in Settings if you want a copy on your own Drive.)

## Tech

A single self-contained `index.html` — no build step, no dependencies, no backend. HTML + CSS + vanilla JS, deployed on GitHub Pages. Data lives in `localStorage`; optional Google Sheets backup uses Google Identity Services (OAuth) and the Sheets/Drive REST APIs directly from the browser.

### For developers

To hack on it, serve the folder over `http://` (Google OAuth rejects the `file://` origin, so opening the file directly breaks only the backup feature):

```bash
python -m http.server 8000   # then visit http://localhost:8000
```
