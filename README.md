# N3XUS × Vital Proposal — Vercel Deployment

## Project Structure
```
vercel-project/
├── api/
│   └── chat.js          ← Serverless function (Anthropic proxy)
├── public/
│   └── index.html       ← The proposal (copy vital-nexus-proposal-v4.html here)
├── vercel.json          ← Vercel config
└── README.md
```

## Deployment Steps

### 1. Install Vercel CLI (if not already installed)
```bash
npm install -g vercel
```

### 2. Add your Anthropic API key as a Vercel environment variable
In your Vercel dashboard:
- Go to your project → Settings → Environment Variables
- Add: `ANTHROPIC_API_KEY` = your key (starts with `sk-ant-...`)
- Set for: Production, Preview, Development

Or via CLI:
```bash
vercel env add ANTHROPIC_API_KEY
```

### 3. Deploy
```bash
cd vercel-project
vercel --prod
```

That's it. Vercel will assign you a URL (e.g. `vital-proposal.vercel.app`).
You can also add a custom domain like `vital.n3xus.media` in the Vercel dashboard.

## How it works
- The proposal HTML lives at `/` (served from `/public/index.html`)
- When ARIA sends a message, it calls `/api/chat` (your serverless function)
- The serverless function injects your API key server-side and forwards to Anthropic
- Your API key is **never** exposed in the browser or the HTML file

## Security
- Your `ANTHROPIC_API_KEY` is stored as a Vercel secret — never in code
- The `/api/chat` endpoint only accepts POST requests
- You can add rate limiting or domain whitelisting to `api/chat.js` if needed
