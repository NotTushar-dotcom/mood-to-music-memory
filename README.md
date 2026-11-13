# 🎵 Mood-to-Music Memory

> A personal desktop music companion that connects your emotional state to your listening experience — and helps you remember the moments that mattered.

[![React](https://img.shields.io/badge/React-18.3-61DAFB?logo=react&logoColor=white)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.4-3178C6?logo=typescript&logoColor=white)](https://typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-5.4-646CFF?logo=vite&logoColor=white)](https://vitejs.dev)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://python.org)

---

## 📖 What Is This?

**Mood-to-Music Memory** is a premium Windows desktop music application built around a simple but powerful idea:

> *Instead of opening a music player and picking a song, you describe how you feel — and the app does the rest.*

You choose a mood (Sad, Happy, Romantic, Wholesome, or Ghazal), or describe it in your own words. The app selects a matching playlist, sets the right volume and pacing profile, and starts playing. You can save any listening moment as a **Memory** — a snapshot of the song, mood, date, and your personal reflection — and revisit them later.

The result feels less like a music player and more like a *personal music journal*.

---

## ✨ Features

### 🏠 Home
- Personalized welcome greeting
- Five mood selection cards: **Sad · Happy · Romantic · Wholesome · Ghazal**
- Custom free-text mood description input (up to 200 characters)
- **Start My Session** — creates a listening session and launches the player
- Recently played songs for quick access
- Quick stats: listening streak, songs played, saved memories

### 🎵 Now Playing
- Large album artwork with animated glow during playback
- Song title, artist, mood badge, and playlist name
- Interactive progress bar (click to seek)
- Full playback controls: **Shuffle · Previous · Play/Pause · Next · Repeat**
- Volume slider
- Playback profile display (volume %, fade-in style, speed)
- **Save This Moment** — saves the current song + mood as a Memory
- **Change Mood** — returns to Home to pick a new mood
- Up Next queue — shows all songs in the current playlist

### 📚 My Library
- **My Songs** tab — full sortable song table with artwork, title, artist, duration, mood badge
- **Playlists** tab — card grid view with play buttons for each playlist
- **Search** — real-time filter across songs and artists
- **Import Music** — local file picker supporting multiple audio files, with animated success toast
- Click any song to immediately load and play it

### 💭 Memories
- Full list of saved mood memories with artwork, date, mood badge, song, and personal reflection
- **Bookmark** individual memories
- **Delete** memories with confirmation
- **Save a Memory** modal — pre-fills current song and mood, free-text reflection field (up to 300 chars)
- **Similar Memory** recommendation sidebar — suggests a related memory based on mood
- Smooth add/remove animations

### 📊 Analytics
- **Total Listening Time** — cumulative hours and minutes
- **Most Listened Mood** — your dominant mood over time
- **Songs Played** — total playback count
- **Saved Memories** — count of saved moments
- **Listening History** — animated 7-day bar chart
- **Mood Distribution** — animated horizontal bar breakdown by mood percentage
- **Most Played Songs** — ranked table with play counts and mood tags

### 🎚️ Persistent Bottom Player
- Always visible on every page — never loses your place
- Shows current artwork, title, and artist
- **Previous · Play/Pause · Next** controls
- Seek-able progress bar across the top
- Volume slider
- Expand button → jumps to the Now Playing page
- Fully synchronized with the Now Playing page — same shared state, no duplicates

---

## 🗂️ Project Structure

```
mood-to-music-memory/
│
├── frontend/                    ← React + TypeScript app (primary UI)
│   ├── src/
│   │   ├── components/
│   │   │   ├── shell/           ← AppShell, BottomPlayer (persistent layout)
│   │   │   ├── mood/            ← MoodCard, CustomMoodInput
│   │   │   ├── player/          ← PlaybackControls, ProgressBar, VolumeControl
│   │   │   ├── library/         ← ImportMusic, SongsTable
│   │   │   └── memories/        ← MemoryCard, MemoryForm, SimilarMemory
│   │   ├── pages/               ← One component per route
│   │   │   ├── HomePage.tsx
│   │   │   ├── NowPlayingPage.tsx
│   │   │   ├── LibraryPage.tsx
│   │   │   ├── MemoriesPage.tsx
│   │   │   └── AnalyticsPage.tsx
│   │   ├── store/
│   │   │   └── appStore.ts      ← Global Zustand state
│   │   ├── data/                ← Mock songs, playlists, memories
│   │   ├── hooks/
│   │   │   └── usePlayback.ts   ← Playback timer hook
│   │   └── types/index.ts       ← Shared TypeScript interfaces
│   ├── package.json
│   ├── vite.config.ts
│   ├── tailwind.config.js
│   └── tsconfig.json
│
├── src/                         ← Python backend (early-stage)
│   ├── ui/app.py                ← Legacy Python UI prototype
│   └── services/
│       └── playback.py          ← Python playback service (pygame)
│
├── db/
│   ├── seed_db.py               ← Seed IBM Db2 with initial data
│   └── check_db2.py             ← Verify Db2 connection
│
├── music/                       ← Local audio files (not committed)
├── download_and_store.py        ← yt-dlp download + Db2 storage utility
├── requirements.txt             ← Python dependencies
├── .env.example                 ← Environment variable template
└── PRODUCT REQUIREMENTS DOCUMENT (PRD).md
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| UI Framework | React 18 + TypeScript | Component-based frontend |
| Build Tool | Vite 5 | Fast dev server and bundler |
| Styling | Tailwind CSS 3 | Utility-first CSS |
| Animations | Framer Motion 11 | Page transitions and micro-interactions |
| Icons | Lucide React | Consistent icon set |
| State | Zustand 4 | Global shared playback + app state |
| Routing | React Router 6 | Client-side page navigation |
| Backend (planned) | Python 3.11 | Playback services, Db2 integration |
| Database (planned) | IBM Db2 | Persistent songs, playlists, memories |
| Media Import | yt-dlp | Download user-permitted audio |
| Local Playback | pygame | Python audio playback engine |
| AI (future) | Ollama (llama3.2:3b) | Local mood text understanding |
| Embeddings (future) | nomic-embed-text | Semantic memory search |

---

## 🚀 Getting Started

### Frontend (React App)

```powershell
cd D:\mood-to-music-memory\frontend

# Install dependencies
pnpm install

# If esbuild needs manual setup (pnpm v12):
node node_modules\.pnpm\esbuild@0.21.5\node_modules\esbuild\install.js

# Start the dev server
pnpm run dev
```

Open **http://localhost:5173** in your browser.

### Python Backend (optional, early-stage)

```powershell
cd D:\mood-to-music-memory

# Create and activate virtual environment
py -m venv .venv
.\.venv\Scripts\Activate.ps1

# Install Python dependencies
pip install -r requirements.txt

# Copy and configure environment variables
Copy-Item .env.example .env
# Edit .env with your IBM Db2 credentials

# Verify Db2 connection
python db\check_db2.py

# Seed initial data
python db\seed_db.py
```

---

## 🔄 Application Flow

```
User opens app
      ↓
Home Page — "How are you feeling today?"
      ↓
Select a mood card  (or type a custom mood)
      ↓
Press "Start My Session"
      ↓
Now Playing Page — playlist loads, song starts
      ↓
Listen, skip, adjust volume, seek
      ↓
Press "Save This Moment"  ←→  Memories Page stores it
      ↓
Bottom Player stays visible on every page
      ↓
Analytics Page — see your listening history
```

---

## 🎨 Design System

| Token | Value | Usage |
|---|---|---|
| Background | `#09071a` | Main app background |
| Surface | `rgba(255,255,255,0.04)` | Cards and panels |
| Primary Purple | `#a855f7` | Buttons, active states |
| Deep Purple | `#6d28d9` | Gradient start |
| Sad | `#60a5fa` (blue) | Sad mood accent |
| Happy | `#fbbf24` (amber) | Happy mood accent |
| Romantic | `#f472b6` (pink) | Romantic mood accent |
| Wholesome | `#4ade80` (green) | Wholesome mood accent |
| Ghazal | `#c084fc` (violet) | Ghazal mood accent |
| Font | Inter | All text |

Design style: **Dark atmospheric glassmorphism** — deep navy/purple backgrounds, subtle blur surfaces, fine borders, purple neon glow on interactive elements.

---

## 📋 Mood Profiles

| Mood | Playlist | Volume | Style |
|---|---|---|---|
| Sad | Sad Comfort Playlist | 30% | Slow fade-in, 0.95× speed |
| Happy | Feel Good Vibes | 65% | Instant start, 1.0× speed |
| Romantic | Love Notes | 50% | Soft fade-in, 1.0× speed |
| Wholesome | Calm Waters | 45% | Gentle fade-in, 0.98× speed |
| Ghazal | Ghazal Nights | 40% | Slow fade-in, 0.95× speed |

---

## 🗃️ Database Schema (IBM Db2 — `MDMUSIC.MOODMUSIC`)

> The database layer is planned and partially set up. The frontend currently uses mock data.

| Table | Purpose |
|---|---|
| `SONGS` | Audio file paths, title, artist, duration, mood tag |
| `PLAYLISTS` | Named playlists linked to moods |
| `PLAYLIST_SONGS` | Many-to-many: playlist ↔ song |
| `MOOD_MEMORIES` | Saved listening moments with reflections |
| `PLAYBACK_PROFILES` | Volume, fade-in, speed per mood |
| `SESSIONS` | Historical listening session log |

---

## ⚙️ Environment Variables

Copy `.env.example` to `.env` and fill in your values:

```env
DB2_DATABASE=MDMUSIC
DB2_HOSTNAME=localhost
DB2_PORT=50000
DB2_USERNAME=db2admin
DB2_PASSWORD=your_password_here
DB2_SCHEMA=MOODMUSIC
MUSIC_FOLDER=D:\mood-to-music-memory\music
```

> ⚠️ Never commit `.env` to version control. It is already in `.gitignore`.

---

## 🧪 Current State (November 2026)

### ✅ Done
- [x] Full React + TypeScript + Vite + Tailwind CSS frontend
- [x] Single-window app with persistent sidebar, header, and bottom player
- [x] Home page with mood selection and session start
- [x] Now Playing page with full playback controls
- [x] My Library page with song table, playlists view, and import
- [x] Memories page with save, bookmark, and delete
- [x] Analytics page with charts and stats (mock data)
- [x] Persistent bottom mini-player across all pages
- [x] Global Zustand state — all controls synchronized
- [x] Framer Motion animations and transitions
- [x] Mock data for songs, playlists, and memories
- [x] Python virtual environment and Db2 driver setup
- [x] IBM Db2 database and schema created
- [x] Database seed script

### 🔧 Known Issues / In Progress
- [ ] esbuild requires manual install step on pnpm v12 (`ERR_PNPM_IGNORED_BUILDS`)
- [ ] Playback timer runs on mock data — no real audio playback in the browser yet
- [ ] Import Music picks files locally but does not actually play them (no Web Audio integration)
- [ ] Analytics data is fully mocked — not derived from actual session history
- [ ] No persistence — refreshing the browser resets all state (no localStorage yet)
- [ ] Memory editing (Edit button opens no form yet — only Delete works)

### 🗺️ Roadmap
- [ ] Connect frontend to Python backend via REST API
- [ ] Wire IBM Db2 as the data source (replace mock data)
- [ ] Real audio playback in-browser using Web Audio API or Howler.js
- [ ] localStorage / IndexedDB persistence for sessions and memories
- [ ] Memory editing form
- [ ] Real analytics derived from session history
- [ ] Ollama local LLM for free-text mood understanding
- [ ] Semantic memory search using nomic-embed-text embeddings
- [ ] Electron or Tauri wrapper for a true native desktop app
- [ ] Gradual volume fade-in per mood profile
- [ ] Keyboard shortcuts for playback controls

---

## 📄 License

Personal project. All rights reserved.

---

<div align="center">

Made with 💜 by **Tushar**

*Listen to how you feel.*

</div>
