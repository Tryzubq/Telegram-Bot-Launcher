Telegram Video Bots 🎬

Two Telegram bots that turn raw video links into short-form content,
run from one shared desktop launcher with no coding required.

## Features

- 📱 **Clip & Caption Bot** — send a
  YouTube/TikTok link and get AI-picked (or manually timestamped)
  vertical clips back, titles burned in automatically.
- 🎯 **Multiple output formats** — 9:16 full-frame, 4:3, 1:1 square, or a
  facecam+gameplay split layout, each with your choice of background
  style (blur, dark blur, solid black, solid white).
- 💬 **Auto-generated subtitles** — optional local speech-to-text burns
  captions onto every clip, no API key or per-clip cost.
- 🏆 **Video Rater Bot** — send clips one at a
  time and build a single growing "ranking countdown" video, with AI or
  your own titles for each entry.
- 🖥️ **One shared desktop launcher** — pick a bot, paste your keys,
  press Start. No terminal commands, no manually edited config files.
- 🔒 **Isolated per-bot environments** — each bot installs into its own
  `.venv`, so setting one up can never break the other.

## Requirements

- Python 3.10+
- FFmpeg (used for all video cropping, cutting, and format conversion)
- A Telegram bot token ([@BotFather](https://t.me/BotFather))
- A Google Gemini API key ([Google AI Studio](https://aistudio.google.com/apikey))

## Installation

1. Clone or download this repo.
2. Make sure **Python 3.10+** and **ffmpeg** are installed and on your PATH
   (`python --version` and `ffmpeg -version` should both work in a terminal).
3. Double-click **`Start.bat`** (Windows) or run **`Start.sh`** (Mac/Linux) —
   this opens the shared launcher window.
4. In the launcher: pick a bot from the dropdown, click **📦 Install
   Requirements** (builds that bot's own `.venv`), paste in its Telegram
   bot token and Gemini API key (hover the ⓘ next to each field if you need
   a reminder of where to get them), then **▶ Start Bot**.
5. Repeat step 4 for the other bot if you want both running (switch the
   dropdown, click **Browse…** to point it at the other bot's folder the
   first time).

See each bot's own README for what it actually does and how
to use it once it's running.

## Getting your own API keys

- **Telegram Bot Token**: message [@BotFather](https://t.me/BotFather) on
  Telegram, send `/newbot`, and copy the token it gives you.
- **Gemini API Key**: get a free key at
  [Google AI Studio](https://aistudio.google.com/apikey).

## Fixing YouTube download errors

Both bots run on [`yt-dlp`](https://github.com/yt-dlp/yt-dlp), and YouTube
sometimes blocks a download with an error like **"Sign in to confirm
you're not a bot"** or **"The page needs to be reloaded"**. This isn't a
bug in either bot — it's YouTube asking for proof that a real, logged-in
person is downloading, and it happens to every `yt-dlp`-based tool
occasionally, not just this one.

Each bot already retries automatically across 10 different download
methods first, at no cost and with no setup, before it ever shows this
error — so seeing it means all 10 were specifically blocked for this
video.

The fix is a one-time, few-minute setup, done entirely through the
launcher — no config files to edit by hand:

1. Install a browser extension called **"Get cookies.txt LOCALLY"**
   (search that exact name in your browser's extension store — works in
   Chrome, Edge, Opera/Opera GX, Brave, and Firefox).
2. Make sure you're logged into YouTube in that browser, go to
   youtube.com, click the extension's icon, and hit **Export**. This
   downloads a file named `cookies.txt`.
3. In the Bot Launcher, find the **"Cookies file"** field and click
   **Browse…**, then select that downloaded file. No need to move or
   rename it yourself.
4. Press **▶ Start Bot** (or Stop then Start again if it was already
   running).

Notes:

- Do this once — you don't need to repeat it per video.
- Never share your `cookies.txt` file or paste its contents anywhere
  (including into an AI assistant, a chat, or an issue on this repo).
  It's equivalent to your login session — treat it like a password.
  Everyone who runs these bots needs to export their *own* cookies file
  from their *own* account.
- If exporting cookies doesn't fix it either, the block is likely on
  your network/IP rather than your account — restarting your router or
  trying a different network (e.g. mobile data) can help.

## Notes

- `.env` files (holding your actual keys) and each bot's `.venv/` folder are
  gitignored — they're never meant to be committed. If you fork/clone this,
  you'll set your own keys up locally via the launcher.
- Both bots are built around `yt-dlp`, so they're subject to whatever
  YouTube/TikTok/etc. currently allow — see each bot's README for
  known quirks and workarounds (e.g. YouTube's occasional "confirm you're
  not a bot" check).
- Built for clipping content you own or have the rights to reuse. What you
  point these at is on you.
