<div align="center">

# 🎬 FunTime
### *Your personal movie & TV show streaming hub*

![HTML](https://img.shields.io/badge/HTML5-Single%20File-e8b86d?style=for-the-badge&logo=html5&logoColor=black)
![OMDb](https://img.shields.io/badge/OMDb-API%20Powered-3d7fff?style=for-the-badge&logo=imdb&logoColor=white)
![Streaming](https://img.shields.io/badge/Multi--Source-Streaming-ff4d6d?style=for-the-badge&logo=youtube&logoColor=white)
![Theme](https://img.shields.io/badge/Dark%20%2F%20Light-Mode-3dffc0?style=for-the-badge)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-a855f7?style=for-the-badge)

<br/>

> **Search, preview, and watch** thousands of movies & TV shows — all in a single HTML file.
> No install. No server. No framework. Just open and enjoy.

<br/>

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎭 **3D Flip Cards** | Hover any card for a smooth 3D flip showing plot, rating & genre |
| 🔍 **Live Search** | Search the entire OMDb database in real time with debounce |
| 🎬 **Cinematic Hero** | Auto-rotating hero with sharp portrait posters + blurred backdrop |
| 👁️ **Recently Viewed** | Tracks your watch history locally across sessions |
| 🏆 **Top Lists** | Pre-loaded curated top movies & TV shows to browse instantly |
| 🎛️ **Filters** | Filter by type (Movie / Series) and release year |
| 📺 **In-page Player** | Watch in a modal with Season & Episode selector for TV shows |
| 📡 **Multi-Source** | Switch streaming provider from the navbar — one click |
| 🌙 **Dark / Light Mode** | Full theme toggle saved to your preferences |
| 🗑️ **Clear History** | Wipe Recently Viewed with one button |
| 📱 **Responsive** | Works on desktop, tablet & mobile |

---

## 🚀 Getting Started

### Step 1 — Get Your Free OMDb API Key

1. Go to **[omdbapi.com](https://www.omdbapi.com/apikey.aspx)**
2. Select the **Free tier** (1,000 requests/day)
3. Enter your email and submit
4. Check your inbox and **activate** the key

### Step 2 — Add Your Key to the File

Open `funtime.html` in any text editor and find **line 1326**:

```js
// ─── CONFIG ───
const API_KEY = "your_key_here";   // 👈 paste your OMDb key here
```

### Step 3 — Open & Enjoy

```bash
# No server needed — just open it!
open funtime.html
```

Or simply **double-click** `funtime.html` in your file explorer. That's it. ✅

---

## 🗂️ Project Structure

```
funtime.html
│
├── 🎨  CSS  ──── Dark/light themes, 3D flip cards, hero slider, modal, ep-bar
├── 🧱  HTML ──── Navbar, hero, search, card grid, player modal, episode selector
└── ⚙️  JS   ──── All logic — zero external libraries
         │
         ├── CONFIG (line 1326)
         │     ├── API_KEY         → your OMDb key
         │     ├── ACTIVE_SOURCE   → default streaming provider
         │     ├── SOURCES         → all streaming provider URL builders
         │     ├── TOP_MOVIE_IDS   → curated top films (IMDb IDs)
         │     ├── TOP_TV_IDS      → curated top shows (IMDb IDs)
         │     └── HERO_IDS        → featured hero titles (IMDb IDs)
         │
         ├── initHero()            → builds the auto-rotating hero slider
         ├── performSearch()       → live OMDb search with debounce
         ├── renderFlipGrid()      → renders the 3D flip card grid
         ├── trackAndWatch()       → logs to Recently Viewed + opens player
         ├── openModal()           → launches player, shows ep-bar for TV
         ├── loadSeasons()         → fetches season count from OMDb
         ├── loadEpisodeList()     → fetches episode names per season
         ├── loadEpisode()         → reloads iframe for selected S/E
         ├── setSource()           → switches streaming provider live
         └── toggleTheme()         → flips dark ↔ light mode
```

---

## ⚙️ Configuration

All settings live at the top of the `<script>` block:

```js
const API_KEY       = "xxxxxxxx";  // Your OMDb API key
const ACTIVE_SOURCE = "vidsrc";    // Default streaming provider
```

### 📡 Switching Streaming Provider

You can switch provider **directly from the navbar** using the `📡` dropdown — no code needed. Your choice is saved automatically.

To change the **default** provider that loads on startup, edit line 1331:

```js
const ACTIVE_SOURCE = "vidsrc";     // default
const ACTIVE_SOURCE = "vidlink";    // switch to Vidlink
const ACTIVE_SOURCE = "111movies";  // switch to 111Movies
```

All three providers use the same **IMDb ID** — switching is instant with no other changes.

### 🎞️ Customising the Top Lists

Want different titles in the default grid or hero? Edit the IMDb ID arrays:

```js
const TOP_MOVIE_IDS = [
  "tt0111161",  // The Shawshank Redemption
  "tt0068646",  // The Godfather
  // add your own...
];

const HERO_IDS = [
  "tt1375666",  // Inception  ← shown in the big cinematic hero
  // ...
];
```

> 💡 Find any IMDb ID on [imdb.com](https://www.imdb.com) — it's the `tt` number in the URL.

---

## 🎮 How to Use

```
🖱️  Hover a card             → 3D flip reveals plot + rating
▶️  Click "Watch Now"        → opens the in-page video player
📺  TV show player           → Season & Episode dropdowns appear at top
🔄  Change season            → episode list auto-updates with names
▶️  Hit "Go"                 → loads selected episode (player stays open)
🔍  Type in search bar       → searches OMDb live (450ms debounce)
🏆  Top Movies / Shows tabs  → browse curated lists
👁️  Recently Viewed          → your local watch history
🗑️  Clear button             → wipes Recently Viewed history
📡  Navbar source btn        → switch VidSrc / Vidlink / 111Movies
🌙  Navbar moon btn          → toggle dark / light mode
⌨️  Press Escape             → closes the video player
```

---

## 🔑 OMDb API — Quick Reference

| Endpoint | What it does |
|---|---|
| `?i=tt0111161&plot=full` | Fetch full details by IMDb ID |
| `?s=inception&page=1` | Search titles by keyword |
| `?i=tt0111161&Season=2` | Fetch episode list for a season |

The free tier gives you **1,000 requests/day**. FunTime batches requests and caches in memory to stay well within limits.

---

## 📺 Streaming Sources — Quick Reference

FunTime supports **3 streaming providers** switchable from the navbar with no page reload.

| Provider | Movie URL | TV URL |
|---|---|---|
| **VidSrc** | `/embed/movie?imdb=ttXXX&autoplay=1` | `/embed/tv?imdb=ttXXX&season=S&episode=E` |
| **Vidlink** | `/movie/ttXXX?autoplay=true` | `/tv/ttXXX/S/E?autoplay=true` |
| **111Movies** | `/movie/ttXXX` | `/tv/ttXXX/S/E` |

**VidSrc mirrors** — if the default goes down, update the URL inside `SOURCES.vidsrc`:

```js
// around line 1334 in funtime.html
vidsrc: {
  name: "VidSrc",
  movie: (id) => `https://vidsrc-embed.ru/embed/movie?imdb=${id}&autoplay=1`,
  tv:    (id, s, e) => `https://vidsrc-embed.ru/embed/tv?imdb=${id}&season=${s}&episode=${e}&autoplay=1`,
},
```

Common mirrors:
```
https://vidsrc.to/embed
https://vidsrc.me/embed
https://vidsrc-embed.ru/embed   ← currently used
```

> 💡 Want to add a new provider? Just add a new entry to `SOURCES` following the same pattern — `movie(id)` and `tv(id, season, episode)`.

---

## 🛠️ Built With

- **[OMDb API](https://www.omdbapi.com/)** — movie & TV metadata, posters, ratings, episode lists
- **[VidSrc](https://vidsrc.me/)** · **[Vidlink](https://vidlink.pro/)** · **[111Movies](https://111movies.net/)** — streaming embed APIs
- **[Bebas Neue](https://fonts.google.com/specimen/Bebas+Neue)** + **[DM Sans](https://fonts.google.com/specimen/DM+Sans)** — Google Fonts
- **Vanilla JS** — zero frameworks, zero dependencies
- **CSS `perspective` + `rotateY`** — pure CSS 3D flip cards
- **`localStorage`** — watch history + theme preference + source preference

---

## 📋 Browser Support

| Browser | Status |
|---|---|
| Chrome / Edge | ✅ Full support |
| Firefox | ✅ Full support |
| Safari | ✅ Full support |
| Mobile Chrome / Safari | ✅ Responsive |

---

## ⚠️ Disclaimer

FunTime is a **personal project** built for educational purposes. It uses publicly available embed sources and the free OMDb API. Please respect the [OMDb API Terms of Use](https://www.omdbapi.com/legal.htm) and do not exceed your daily request limit.

---

<div align="center">

Made with ☕ and too many late-night movies — and a little help from **Claude** 🤖

**[⬆ Back to top](#-funtime)**

</div>
