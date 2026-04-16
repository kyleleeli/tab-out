# Tab Out

**Keep tabs on your tabs.**

Tab Out is a Chrome extension that replaces your new tab page with a dashboard of everything you have open. Tabs are grouped by domain, with homepages (Gmail, X, LinkedIn, etc.) pulled into their own group. Close tabs with a satisfying swoosh + confetti.

No server. No account. No external API calls. Just a Chrome extension.

---

## Install with a coding agent

Send your coding agent (Claude Code, Codex, etc.) this repo and say **"install this"**:

```
https://github.com/zarazhangrui/tab-out
```

The agent will walk you through it. Takes about 1 minute.

---

## Features

- **See all your tabs at a glance** on a clean grid, grouped by domain
- **Homepages group** pulls Gmail inbox, X home, YouTube, LinkedIn, GitHub homepages into one card
- **Close tabs with style** with swoosh sound + confetti burst
- **Duplicate detection** flags when you have the same page open twice, with one-click cleanup
- **Click any tab to jump to it** across windows, no new tab opened
- **Save for later** bookmark a single tab or an entire group to a checklist before closing
- **Localhost grouping** shows port numbers next to each tab so you can tell your vibe coding projects apart
- **Expandable groups** show the first 8 tabs with a clickable "+N more"
- **100% local** your data never leaves your machine
- **Pure Chrome extension** no server, no Node.js, no npm, no setup beyond loading the extension

### New in this fork

- **Tab search** — press `/` to focus a search box in the header; results filter in real time as you type, `Enter` jumps to the first matching tab, `Esc` clears
- **Collapse cards** — click any card's title row to fold the tab list away; collapsed state survives page refresh
- **Drag to reorder** — drag domain cards into any order; your layout is saved and restored automatically
- **Color labels** — hover a card header to reveal four color dots (amber / sage / slate / rose); click to color-code the top bar and remember it across sessions
- **Bulk save & close** — each card now has a "Save all & close" button to save every tab in a group for later in one click, then close them all
- **Close stats** — the footer shows how many tabs you closed today and all-time
- **7-day sparkline** — a mini line chart in the footer shows your tab-closing trend over the past week

---

## Manual Setup

**1. Clone the repo**

```bash
git clone https://github.com/zarazhangrui/tab-out.git
```

**2. Load the Chrome extension**

1. Open Chrome and go to `chrome://extensions`
2. Enable **Developer mode** (top-right toggle)
3. Click **Load unpacked**
4. Navigate to the `extension/` folder inside the cloned repo and select it

**3. Open a new tab**

You'll see Tab Out.

---

## Personal config

Create `extension/config.local.js` (already gitignored) to add your own landing page patterns and custom tab groupings:

```js
// Treat Notion workspace root as a "homepage"
var LOCAL_LANDING_PAGE_PATTERNS = [
  { hostname: 'www.notion.so', pathExact: ['/'] },
];

// Merge all Google apps into one card
var LOCAL_CUSTOM_GROUPS = [
  { hostname: 'mail.google.com',     groupKey: 'google', groupLabel: 'Google' },
  { hostname: 'docs.google.com',     groupKey: 'google', groupLabel: 'Google' },
  { hostname: 'drive.google.com',    groupKey: 'google', groupLabel: 'Google' },
  { hostname: 'calendar.google.com', groupKey: 'google', groupLabel: 'Google' },
];
```

---

## How it works

```
You open a new tab
  -> Tab Out shows your open tabs grouped by domain
  -> Homepages (Gmail, X, etc.) get their own group at the top
  -> Search with "/" to quickly find and jump to any tab
  -> Drag cards to reorder, color-code them for at-a-glance context
  -> Collapse groups you want to keep but not look at right now
  -> Close groups you're done with (swoosh + confetti)
  -> Save tabs for later — one at a time or the whole group
  -> Footer tracks how many tabs you've closed today and this week
```

Everything runs inside the Chrome extension. No external server, no API calls, no data sent anywhere. Saved tabs and preferences are stored in `chrome.storage.local`.

---

## Tech stack

| What | How |
|------|-----|
| Extension | Chrome Manifest V3 |
| Storage | chrome.storage.local |
| Sound | Web Audio API (synthesized, no files) |
| Animations | CSS transitions + JS confetti particles |
| Drag & drop | Native HTML5 Drag and Drop API |
| Charts | Inline SVG polyline (no libraries) |

---

## License

MIT

---

Built by [Zara](https://x.com/zarazhangrui)
