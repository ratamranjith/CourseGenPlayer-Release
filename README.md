# 📚 CourseGenPlayer

**CourseGenPlayer** is a premium, high-performance desktop application designed for managing and playing offline video courses. Built with Electron, React, and SQLite, it offers a seamless and immersive learning experience without the need for an internet connection.

![App Banner](C:\Users\ratam\.gemini\antigravity\brain\e8c9e15f-2bea-4989-9195-5190bca45353\dashboard_mockup_1778772021569.png)

## ✨ Key Features & Premium Upgrades

LearnCreator has been upgraded to a premium learning suite offline player, packed with powerful learning intelligence features:

### 🎥 Playback Intelligence
- **Adaptive Bitrate Streaming (ABR)**: Ingests `.m3u8`/`.mpd` manifests using `hls.js`, dynamically scaling resolution from 240p to 1080p+ based on your network bandwidth.
- **Predictive Next-Lesson Pre-fetching**: A background Service Worker automatically pre-fetches the first 30 seconds of the next lesson into `CacheStorage` when you hit 90% completion, ensuring instant zero-latency load times.
- **Playback Speed Memory**: Remembers your preferred playback speed per course and lesson.
- **Autoplay next Toggle**: Automatically play the next lesson when the current video ends, with an on-screen countdown timer.
- **Frame-by-Frame Navigation**: Step through videos frame-by-frame using `,` (previous frame) and `.` (next frame) hotkeys.
- **Last 10 Seconds Replay**: Instantly rewind the video by 10 seconds with a single button.
- **Timeline Hover Preview**: Hover over the timeline to preview video frame thumbnails rendered dynamically onto an offline canvas tooltip.

### 🔎 Global Command Palette (`Ctrl + K`)
- Press `Ctrl + K` anywhere in the app to search all courses, modules, lessons, and bookmarks.
- Run quick actions directly: "Switch to AMOLED Theme", "Accent Color: Violet Charm", "Go to Dashboard", or type `:90` to jump directly to a timestamp.

### 📈 Advanced Analytics, Gamification & Dashboard
- **Leveling XP System**: Gain experience points (+50 XP for completing lessons, +5 XP for bookmarking, daily bonus) to advance from Level 1 to 20 with descriptive titles (e.g. *Code Warrior*).
- **Daily Study Goals**: Animated progress ring displaying study minutes compared to customized daily goal limits (configured via modal).
- **Streaming-Style Course Cards**: Netflix-style horizontal Continue Watching row with animated hover zoom, glassmorphism card surfaces, remaining study durations, and circular completion ProgressRings.
- **GitHub-style Heatmap Calendar**: Contributions grid depicting study activity density over the past 365 days.
- **Weekly Velocity Chart**: Smooth velocity bars tracking daily study session minutes.
- **Learning Streak Counter**: Hot streak tracker of consecutive days learned.

### 📝 Notes & Bookmarks System
- **Double-Tier Auto-Save System**: Notes are debounced and instantly saved to a high-speed `IndexedDB` draft to prevent UI thread blocking. Explicit "Save" pushes the draft directly to SQLite. 
- **Hydration Prompts**: If you close the app without a full save, a Framer Motion prompt will ask to recover your lost draft the next time you open the lesson.
- **Per-Lesson Markdown Notes**: Integrated editor featuring split-screen Markdown editing, full live preview, and quick Markdown format exports.
- **Keyboard Shortcut Isolation**: Global shortcuts (Space, J, L, M) are automatically isolated and blocked while typing in the notes or AI panels to prevent accidental video commands.
- **Timeline Micro-Markers**: Timestamped bookmarks automatically render as amber dots directly on the video progress track. Hovering reveals an isolated micro-popover; clicking instantly seeks to the mark.

### 🌙 Premium Themes & Custom Layouts
- **6 Premium Theme Packs**: Midnight Learning (navy), Cyber Purple (neon violet), Emerald Focus (calm forest), Amber Productivity (warm gold), Light Mode, and AMOLED Black Mode.
- **Collapsible Sidebar**: Compact 56px vertical icon strip when collapsed, expanding to a 320px tab view. Toggled by clicking or pressing `[`.
- **Course Tree States**: Outline lessons reflect learning states: Completed (check icon + line-through), Current (bold with pulsing Zap icon), and Not Started.
- **Layout Configurations**: 
  - **Study Mode**: Standard player layout with collapsible sidebar.
  - **Split Mode**: Half-screen video, half-screen Markdown notes.
  - **Focus Mode**: Video-only distraction-free canvas with header stats.
  - **Workspace Mode**: 4-panel study console (Player, Notes, Bookmarks, and AI side-by-side).
  - **Zen Mode**: True immersive cinematic view (video-only with auto-hiding controls, dynamic ambient glow extraction, and Apple TV blurred background).
  - Press `Escape` in Zen mode to immediately exit back to windowed mode.

### 🤖 Multi-LLM Provider Architecture & AI Integration
- **17+ LLM Providers & Generic OpenAI-Compatible Support**: Connect to any AI model provider through a unified provider architecture:
  - **Google Gemini** (Gemini 2.5 Flash, 2.5 Pro, 1.5 Flash, 1.5 Pro)
  - **OpenAI** (gpt-4o, gpt-4o-mini, o3-mini, o1)
  - **OpenAI-Compatible APIs** (vLLM, Ollama, LM Studio, LocalAI, OpenRouter, Together AI, Groq, Fireworks AI, DeepInfra, custom endpoints)
  - **Anthropic Claude** (Claude 3.5 Sonnet, Haiku, Opus)
  - **xAI Grok** (Grok 2)
  - **Mistral AI**, **Cohere** (Command R+), and **DeepSeek** (DeepSeek-Chat, DeepSeek-R1)
- **AI Provider Settings UI**: Dedicated modal allowing users to test connections in real-time (`⚡ Test Connection`), fetch available models dynamically, adjust temperature/max tokens/custom JSON headers/timeouts, and switch active profiles on-the-fly without restarting.
- **Unified Real-time Streaming**: Standardized SSE streaming engine across all providers for instant typing responses.
- **📍 Temporal Context Injection**: Click "Capture Timestamp" to read the video's current time, extract ±15 seconds of surrounding WebVTT subtitle dialogue, and inject it into prompt context.
- **Lesson Summaries & Smart Transcript Lookup**: Generate summaries, cheat sheets, and ask timestamped questions like *"Where did he explain React hooks?"*.

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** (LTS version recommended)
- **npm** (comes with Node.js)

## 📥 Download & Installation

### 🪟 Windows
- **Installer**: Download `CourseGenPlayer Setup 1.0.0.exe`. Double-click to install.
- **Portable**: Download `CourseGenPlayer 1.0.0.exe`. No installation required—just run and learn!

### 🐧 Linux

- **Portable (Recommended)**: Download `CourseGenPlayer-1.0.0.AppImage`. Right-click -> Properties -> Permissions -> **Allow executing file as program**, then double-click to run.
- **Debian/Ubuntu**: Download `.deb` and install via `sudo dpkg -i CourseGenPlayer-1.0.0.deb`.

---

## 🚀 Development Setup
If you want to run the source code locally:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/ratamranjith/CourseGenPlayer.git
   cd CourseGenPlayer
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start Development Mode**:
   ```bash
   npm run dev
   ```

---

## 🛠 Step-by-Step Usage Guide

### Step 1: Import Your Course
Click the **"Import Course"** button on the dashboard. Select the root folder containing your course videos. The app will automatically scan for modules and lessons.

![Import Flow](C:\Users\ratam\.gemini\antigravity\brain\e8c9e15f-2bea-4989-9195-5190bca45353\import_flow_mockup_1778772318693.png)

### Step 2: Organize & Track
Your course will appear on the dashboard with a progress bar. Click on it to open the **CourseGenPlayer**.

### Step 3: Immersive Learning
Use the accordion sidebar to navigate modules. As you watch, your progress is saved automatically. Once you reach 90% of a video, it marks itself as complete with a green tick!

![Player Mockup](C:\Users\ratam\.gemini\antigravity\brain\e8c9e15f-2bea-4989-9195-5190bca45353\player_mockup_1778772245275.png)

---

## 📦 Building for Distribution

To create standalone executables for different platforms, use the following commands:

- **Windows**:
  ```bash
  npm run build:win
  ```
- **macOS**:
  ```bash
  npm run build:mac
  ```
- **Linux**:
  ```bash
  npm run build:linux
  ```
- **All Platforms (Win + Linux)**:
  ```bash
  npm run build:all
  ```



The installers will be generated in the `release/` directory.


---

## 🛠 Technology Stack

- **Frontend**: React 19, Tailwind CSS v4, Framer Motion, Lucide Icons, `hls.js`.
- **Backend**: Electron 42, Node.js, Express 5 (for local asset serving + HLS proxy routing).
- **Offline Edge**: Service Worker + `CacheStorage` for predictive caching.
- **Database**: SQLite (using native `node:sqlite`) + `IndexedDB` (for fast draft memory).
- **Build System**: Vite 8, electron-builder.

---

## 🚀 Development Setup (For Contributors)

If you want to run the source code locally or build it yourself:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/ratamranjith/CourseGenPlayer.git
   cd CourseGenPlayer
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start Development Mode**:
   ```bash
   npm run dev
   ```

4. **Build for Distribution**:
   ```bash
   npm run build:win  # For Windows
   ```

---

## 👋 Community & Support

We’re using **GitHub Discussions** as a place to connect with our users. 

*   **Ask Questions**: Need help with imports or playback?
*   **Share Ideas**: Have a feature request for the next version?
*   **Engage**: Connect with other lifelong learners.
*   **Stay Open**: Remember that this is a community we build together 💪.

To get started, head over to our Discussions tab and introduce yourself!

---

## 📄 License


This project is licensed under the ISC License.

---

*Built with ❤️ for lifelong learners.*

---

> **Total Lines of Application Code**: ~3,200+ lines
> **Database Tables**: 8
> **IPC Channels**: 17
> **React Components**: 7
> **Keyboard Shortcuts**: 10
