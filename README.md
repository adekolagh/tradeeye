# 📡 TradeEye

AI-powered trading chart scanner. Point your camera or upload a screenshot — Claude Vision extracts your indicator values automatically.

**Phase 1 — Chart Scanner**
- 📷 Camera (16:9 live capture)
- 🖼 Screenshot upload
- Auto-fills: Pair, Timeframe, Entry, SAR, ATR, ADX, +DI, −DI, RSI

---

## Project Structure

```
tradeeye/
├── api/
│   └── scan.js          ← Vercel serverless function (Anthropic proxy)
├── public/
│   └── index.html       ← Frontend app
├── .env.example         ← Env variable template
├── .gitignore
├── package.json
└── vercel.json
```

---

## Deploy to Vercel

### 1. Push to GitHub

```bash
git init
git add .
git commit -m "TradeEye phase 1"
git remote add origin https://github.com/adekolagh/tradeeye.git
git push -u origin main
```

### 2. Deploy on Vercel

1. Go to [vercel.com](https://vercel.com) → **Add New Project**
2. Import your `tradeeye` GitHub repo
3. Click **Deploy** (default settings work)

### 3. Add your API Key

1. In Vercel dashboard → your project → **Settings → Environment Variables**
2. Add:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-...`
   - **Environment:** Production, Preview, Development ✓
3. Click **Save** → go to **Deployments** → **Redeploy**

### 4. Update GitHub Pages (optional)

If you still want GitHub Pages to serve the frontend, update `public/index.html` fetch URL from `/api/scan` to your Vercel URL:

```js
const res = await fetch('https://tradeeye.vercel.app/api/scan', { ... })
```

---

## Local Development

```bash
npm install
cp .env.example .env.local
# Add your real key to .env.local
npx vercel dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## Environment Variables

| Variable | Description |
|----------|-------------|
| `ANTHROPIC_API_KEY` | Your Anthropic API key from [console.anthropic.com](https://console.anthropic.com) |

---

*Built with Claude AI Vision + Vercel Serverless*
