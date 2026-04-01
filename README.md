# EasyView — Screen Sharing for Helping Family

Simple browser-based screen sharing. No app installs, no backend server, no accounts.

## How It Works

1. **Mom** opens the `/share` link → taps one green button → a **6-digit code** appears
2. **She reads the code** to you over the phone
3. **You** open `/view`, type the 6 digits → instantly see her screen

## Deploy to Vercel

```bash
# Option A: Vercel CLI
npm i -g vercel
cd easyview-vercel
vercel

# Option B: GitHub
# 1. Push this folder to a GitHub repo
# 2. Go to vercel.com → New Project → Import repo
# 3. No build settings needed — just deploy
```

Once deployed at e.g. `https://easyview.vercel.app`:

| Who | Link | What they do |
|-----|------|-------------|
| Mom | `https://easyview.vercel.app/share` | Tap green button, read 6 digits |
| You | `https://easyview.vercel.app/view` | Type 6 digits, see her screen |

## How It's Built

- **Pure static site** — just one HTML file, no build step, no backend
- **PeerJS** handles signaling via their free cloud server
- **WebRTC** streams video directly between the two phones (peer-to-peer)
- Vercel just serves the HTML — all the magic is client-side

## Privacy

- Video goes **directly between devices** (never through any server)
- PeerJS cloud only relays tiny connection setup messages
- No data stored anywhere, no accounts, no tracking
- Codes are random and ephemeral

## Files

```
easyview-vercel/
├── index.html      ← The entire app (single file)
├── vercel.json     ← URL routing (/share, /view → index.html)
└── README.md
```
