<div align="center">

# 🎬 FunTime
### *Your personal movie & TV show streaming hub*

![HTML](https://img.shields.io/badge/HTML5-Single%20File-e8b86d?style=for-the-badge&logo=html5&logoColor=black)
![API](https://img.shields.io/badge/OMDb-API%20Powered-3d7fff?style=for-the-badge&logo=imdb&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-3dffc0?style=for-the-badge)
![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-ff4d6d?style=for-the-badge)

<br/>

> **Search, preview, and watch** thousands of movies & TV shows — all in a single HTML file. No install. No server. Just open and enjoy.

<br/>

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎭 **Flip Cards** | Hover any card to flip and see plot, rating & genre |
| 🔍 **Live Search** | Search the entire OMDb database in real time |
| 🎬 **Hero Showcase** | Auto-rotating cinematic hero with sharp poster art |
| 👁️ **Recently Viewed** | Tracks what you've watched across sessions |
| 🏆 **Top Lists** | Pre-loaded top movies & TV shows to browse |
| 🎛️ **Filters** | Filter by type (Movie / Series) and year |
| 📺 **In-page Player** | Watch directly in a modal — no redirects |
| 📱 **Responsive** | Works on desktop, tablet & mobile |

---

## 🚀 Getting Started

### Step 1 — Get Your Free OMDb API Key

1. Go to **[omdbapi.com](https://www.omdbapi.com/apikey.aspx)**
2. Select the **Free tier** (1,000 requests/day)
3. Enter your email and submit
4. Check your inbox and **activate** the key

### Step 2 — Add Your Key to the File

Open `funtime.html` in any text editor and find **line 1099**:

```js
// ─── CONFIG ───
const API_KEY = "your_key_here";   // 👈 paste your OMDb key here
```

Replace `your_key_here` with your actual key.

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
├── 🎨  CSS  ──── Dark cinematic theme, flip cards, hero slider
├── 🧱  HTML ──── Single-page layout, modal player, search bar
└── ⚙️  JS   ──── OMDb fetch, hero init, search, Recently Viewed
         │
         ├── CONFIG block (line 1099)
         │     ├── API_KEY        → your OMDb key
         │     ├── TOP_MOVIE_IDS  → curated top films
         │     ├── TOP_TV_IDS     → curated top shows
         │     └── HERO_IDS       → featured hero titles
         │
         ├── initHero()           → builds the hero slider
         ├── performSearch()      → live OMDb search
         ├── renderFlipGrid()     → renders the card grid
         ├── trackAndWatch()      → saves to Recently Viewed
         └── openModal()          → launches the video player
```

---

## ⚙️ Configuration

All settings live at the top of the `<script>` block in `funtime.html`:

```js
const API_KEY  = "xxxxxxxx";               // Your OMDb API key
const OMDB     = `https://www.omdbapi.com/?apikey=${API_KEY}`;
const VIDSRC   = "https://vidsrc-embed.ru/embed";  // Video embed source
```

### Customising the Top Lists

Want different movies or shows in the default grid? Just edit the IMDb ID arrays:

```js
const TOP_MOVIE_IDS = [
  "tt0111161",  // The Shawshank Redemption
  "tt0068646",  // The Godfather
  // add your own IMDb IDs here...
];

const HERO_IDS = [
  "tt1375666",  // Inception  ← shown in the big hero at the top
  // ...
];
```

> 💡 Find any IMDb ID by visiting a title on [imdb.com](https://www.imdb.com) — it's the `tt` number in the URL.

---

## 🎮 How to Use

```
🖱️  Hover a card          → flips to show plot + rating
▶️  Click "Watch Now"     → opens the in-page video player
🔍  Type in search bar    → searches OMDb live (450ms debounce)
🏆  Top Movies / Shows    → browse curated lists
👁️  Recently Viewed       → your watch history (saved locally)
🗑️  Clear button          → wipes Recently Viewed history
⌨️  Press Escape          → closes the video player
```

---

## 🔑 OMDb API — Quick Reference

| Endpoint | What it does |
|---|---|
| `?i=tt0111161&plot=full` | Fetch full details by IMDb ID |
| `?s=inception&page=1` | Search titles by keyword |
| `?i=tt0111161&type=movie` | Filter by type |

The free tier gives you **1,000 requests per day**. FunTime batches requests and caches results in memory to stay well within limits.

---

## 🛠️ Built With

- **[OMDb API](https://www.omdbapi.com/)** — movie & TV metadata, posters, ratings
- **[VidSrc](https://vidsrc.me/)** — embedded video player
- **[Bebas Neue](https://fonts.google.com/specimen/Bebas+Neue)** + **[DM Sans](https://fonts.google.com/specimen/DM+Sans)** — Google Fonts
- **Vanilla JS** — zero frameworks, zero dependencies
- **CSS Perspective + `rotateY`** — pure CSS 3D flip effect
- **localStorage** — Recently Viewed persistence

---

## 📋 Browser Support

| Browser | Status |
|---|---|
| Chrome / Edge | ✅ Full support |
| Firefox | ✅ Full support |
| Safari | ✅ Full support |
| Mobile Chrome/Safari | ✅ Responsive |

---

## ⚠️ Disclaimer

FunTime is a **personal project** built for educational purposes. It uses publicly available embed sources and the free OMDb API. Respect the [OMDb API Terms of Use](https://www.omdbapi.com/legal.htm) and do not exceed your daily request limit.

---

<div align="center">

Made with ☕ and too many late-night movies.

**[⬆ Back to top](#-funtime)**

</div>
