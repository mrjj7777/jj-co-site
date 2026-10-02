# J&J Co. — AI Engineering & Automation Studio

**Official Website** | Built by JJ | Morbi, Gujarat, India

---

## 📁 Folder Structure

```
JJ-Co/
├── index.html              ← Main website (single file)
├── assets/
│   ├── libs/               ← All JS libraries (local, no CDN needed)
│   │   ├── three.min.js    ← Three.js r128 (WebGL particle sphere)
│   │   ├── gsap.min.js     ← GSAP 3.12.5 (scroll animations)
│   │   ├── ScrollTrigger.min.js
│   │   ├── ScrollToPlugin.min.js
│   │   ├── CustomEase.min.js
│   │   └── lenis.min.js    ← Lenis smooth scroll
│   ├── fonts/              ← (fonts loaded from Google Fonts CDN)
│   └── images/             ← Add any images/logos here
├── vercel.json             ← Deploy to Vercel with 1 click
└── README.md               ← This file
```

---

## 🚀 How to Run Locally

Simply open `index.html` in **Google Chrome** or **Microsoft Edge**.

> ⚠️ **Important:** Open via a local server for best results (WebGL + Lenis need it).
> Right-click `index.html` → Open With → Chrome works fine for preview.

**OR** run a local server:
```bash
# If Python is installed:
python -m http.server 8000
# Then open: http://localhost:8000
```

---

## 🌐 Deploy to Vercel (FREE — Recommended)

1. Go to [vercel.com](https://vercel.com) and create a free account
2. Click **"Add New Project"**
3. Drag and drop this entire **JJ-Co** folder into Vercel
4. Click **Deploy**
5. Your site is LIVE at `jjco.vercel.app` (or your custom domain)

---

## 📦 Deploy to Netlify (Alternative)

1. Go to [netlify.com](https://netlify.com)
2. Drag the entire **JJ-Co** folder onto the Netlify deploy zone
3. Done — live in 30 seconds

---

## ✏️ How to Edit Content

All content is in `index.html`. Search (`Ctrl+F`) for these markers:

| What to edit | Search for |
|---|---|
| Hero headline | `We engineer` |
| Contact WhatsApp | `+91 9537097033` |
| Contact Email | `jjco.official01@gmail.com` |
| Instagram | `@jjco.official` |
| Studio description | `J&amp;J Co. is an AI engineering studio` |
| Services | `srv-card-t` |
| Outcomes/results | `out-metric` |

---

## 🎨 Tech Stack

- **Three.js** — 3D WebGL particle sphere (GLSL shaders)
- **GSAP + ScrollTrigger** — All scroll-based animations
- **Lenis** — Ultra-smooth scroll
- **Space Grotesk + Instrument Serif** — Typography
- **Pure HTML/CSS/JS** — Zero frameworks, zero build step

---

**Contact:** jjco.official01@gmail.com | WhatsApp: +91 9537097033
