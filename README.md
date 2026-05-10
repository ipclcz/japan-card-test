# Japan Trading Cards · AR Experience

A mobile web AR app — no app store, no fees. Built with MindAR + Three.js.

## Live Demo
After deploying: `https://YOUR-USERNAME.github.io/japan-cards`

---

## Deploy to GitHub Pages (Free, ~5 minutes)

### Step 1 — Create the repo
1. Go to [github.com](https://github.com) → **New repository**
2. Name it `japan-cards`
3. Set to **Public**
4. Click **Create repository**

### Step 2 — Upload files
1. Drag and drop all files from this folder into the repo
2. The repo must contain at least: `index.html`, `targets.mind`
3. Click **Commit changes**

### Step 3 — Enable GitHub Pages
1. Go to repo **Settings** → **Pages** (left sidebar)
2. Under "Source": select **Deploy from a branch**
3. Branch: **main**, Folder: **/ (root)**
4. Click **Save**
5. Wait ~60 seconds → your URL appears at the top

---

## Generate `targets.mind` (Image Target File)

This is the file MindAR uses to recognize your card images.

### Option A — Online tool (easiest, free)
1. Go to: https://hiukim.github.io/mind-ar-js/tools/compile
2. Upload images of your card fronts (JPG/PNG, one per card)
3. Click **Start** → download `targets.mind`
4. Place it in the repo root (same folder as `index.html`)

### Option B — npm CLI
```bash
npm install -g mind-ar
npx mind-ar-compile -i card1.jpg card2.jpg card3.jpg -o targets.mind
```

### Tips for good tracking
- Use high-contrast card images (not plain white or plain black)
- The holographic foil pattern helps tracking — photograph under normal light
- Image resolution: 600×840px minimum
- Each card image = one "anchor" (index 0, 1, 2…)
- Order must match the `CARDS` array in `index.html`

---

## Customise Cards

Edit the `CARDS` array in `index.html`:

```js
{
  id: 'samurai',
  art: '⚔️',          // emoji shown in UI
  name: 'SAMURAI',    // English name
  jp: '侍',           // Japanese
  rarity: 'SSR',
  num: '#001',
  frontBg: 'rgba(29,158,117,0.15)',
  frontBorder: '#1D9E75',
  fullName: 'Miyamoto Musashi',
  era: 'Edo Period · 1584–1645',
  desc: 'Short description shown in AR overlay',
  history: 'Longer historical text shown in demo mode',
  quote: '"Famous quote here"',
  tags: [{t:'Sword Saint', c:'#1D9E75'}],
  stats: [['Style','Niten Ichi-ryū'], ['Duels','61']]
}
```

---

## Tech Stack

| Library | Version | Purpose |
|---|---|---|
| MindAR | 1.2.5 | Image tracking AR |
| Three.js | 0.150.1 | 3D rendering |
| Google Fonts | — | Noto Serif JP + Space Mono |

All loaded from CDN — no build step needed.

---

## Browser Support

| Browser | AR Scan | Demo Mode |
|---|---|---|
| Chrome Android | ✅ Full | ✅ |
| Safari iOS 15+ | ✅ Full | ✅ |
| Chrome Desktop | ✅ Full | ✅ |
| Firefox | ⚠️ Limited | ✅ |

---

## File Structure

```
japan-cards/
├── index.html      ← entire app (single file)
├── targets.mind    ← image target data (you generate this)
└── README.md
```
