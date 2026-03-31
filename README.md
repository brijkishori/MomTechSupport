# 📱 EasyView — Screen Sharing for Helping Family with Tech

> **"Mom, open the link I sent you and tap the green button."**
> That's it. That's the whole setup.

A dead-simple, browser-based screen sharing tool built for one purpose: **helping non-tech-savvy family members over the phone** by seeing their screen in real time. No app installs, no accounts, no downloads, no copy-pasting — just one tap and a 6-digit code read aloud.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/YOUR_USERNAME/easyview)
&nbsp;&nbsp;![HTML](https://img.shields.io/badge/Pure-HTML%2FJS-orange)
&nbsp;&nbsp;![No Backend](https://img.shields.io/badge/Backend-None-green)
&nbsp;&nbsp;![License: MIT](https://img.shields.io/badge/License-MIT-blue)

---

## The Problem

You're on the phone with Mom. She can't find a setting. She's describing what she sees, but nothing matches. You're both frustrated. You ask her to install a screen sharing app — now you're debugging *that* instead.

## The Solution

Send her one link. She taps one button. You see her screen.

### Mom's Experience (Sharer)
1. Opens a link you texted her
2. Taps a big green **"Share My Screen"** button
3. Taps **"Start now"** when her phone asks
4. Reads you 6 numbers over the phone
5. ✅ That's it — she's done

### Your Experience (Viewer)
1. Open the `/view` link
2. Type the 6 digits Mom reads to you
3. Instantly see her screen in real time

---

## Features

- **Zero install** — runs entirely in the browser (Chrome, Safari, Edge, Firefox)
- **Zero accounts** — no sign-up, no login, no email
- **Zero backend** — static HTML file, deploy anywhere
- **One-tap sharing** — designed for people who aren't comfortable with technology
- **Peer-to-peer video** — screen stream goes directly between devices via WebRTC, never through a server
- **Privacy-first** — no data stored, no tracking, no analytics, codes are ephemeral
- **Mobile-friendly** — works on Android phones, iPhones, tablets, and desktops
- **Single file** — the entire app is one `index.html` (under 15KB)

---

## Deploy

### Vercel (Recommended)

```bash
# Clone and deploy
git clone https://github.com/YOUR_USERNAME/easyview.git
cd easyview
vercel
```

Or click the **Deploy with Vercel** button above.

### Other Platforms

Works on **any static hosting** — Netlify, GitHub Pages, Cloudflare Pages, Render, Railway, or even a simple file server. Just make sure it's served over HTTPS (required for screen capture API).

| Platform | Steps |
|----------|-------|
| **Vercel** | Push to GitHub → Import in Vercel → Done |
| **Netlify** | Drag and drop the folder at netlify.com/drop |
| **GitHub Pages** | Push to repo → Settings → Pages → Deploy from main |
| **Cloudflare Pages** | Connect repo → Deploy (zero config) |

---

## How It Works Under the Hood

```
Mom's Phone                          Your Phone
     │                                    │
     │  1. Captures screen                │
     │     (getDisplayMedia API)          │
     │                                    │
     │  2. Registers on PeerJS Cloud      │
     │     with ID based on 6-digit code  │
     │                                    │
     │         ← 3. You connect using  ───│
     │              the 6-digit code      │
     │                                    │
     │  4. WebRTC peer-to-peer            │
     │     video stream established  ─────│
     │                                    │
     │  Screen pixels flow directly ──────│
     │  (never through any server)        │
```

- **Signaling:** [PeerJS Cloud](https://peerjs.com/) (free) — only exchanges tiny connection metadata
- **Streaming:** WebRTC — peer-to-peer, encrypted, low latency
- **STUN:** Google's public STUN servers for NAT traversal
- **Frontend:** Vanilla HTML/CSS/JS — no framework, no build step

---

## Project Structure

```
easyview/
├── index.html      ← The entire application
├── vercel.json     ← URL routing for clean /share and /view paths
└── README.md
```

Yes, it's really just one file.

---

## Browser Support

| Browser | Share Screen | View Screen |
|---------|:-----------:|:-----------:|
| Chrome (Android) | ✅ | ✅ |
| Safari (iOS 15+) | ✅ | ✅ |
| Chrome (Desktop) | ✅ | ✅ |
| Edge | ✅ | ✅ |
| Firefox | ✅ | ✅ |

> **Note:** `getDisplayMedia` (screen capture) requires HTTPS in production. iOS Safari support for screen sharing was added in iOS 15.

---

## Privacy & Security

- 🔒 Video streams are **peer-to-peer** — pixels go directly between devices
- 🚫 No server ever sees the screen content
- 🗑️ Nothing is recorded or stored
- ⏱️ Room codes are random and single-use
- 👀 View-only — the viewer **cannot** control or interact with the sharer's device

---

## Why Not Just Use Zoom / TeamViewer / etc.?

| | EasyView | Zoom/Teams | TeamViewer |
|---|:---:|:---:|:---:|
| Requires app install | ❌ | ✅ | ✅ |
| Requires account | ❌ | ✅ | ✅ |
| Mom needs to navigate menus | ❌ | ✅ | ✅ |
| Works from a single link | ✅ | ❌ | ❌ |
| Steps for the sharer | **2** | 5+ | 5+ |
| Self-hosted / private | ✅ | ❌ | ❌ |
| Free forever | ✅ | ⚠️ | ⚠️ |

The goal isn't to replace professional tools. It's to reduce *"Mom, no, tap the OTHER button"* moments from 15 to zero.

---

## Contributing

PRs welcome! Some ideas:

- [ ] Optional audio sharing alongside screen
- [ ] "Draw on screen" annotation for the viewer to point at things
- [ ] QR code on sharer screen so viewer can scan instead of typing digits
- [ ] Self-hosted PeerJS server option for full independence
- [ ] PWA support so Mom can "install" it as a home screen shortcut

---

## License

MIT — do whatever you want with it. If it helps you help your mom (or dad, or grandparent), that's all that matters.

---

<p align="center">
  <i>Built with love for every patient child helping their parents navigate technology over the phone. 💚</i>
</p>
