# N3XUS × Vital Proposal

## Repository Structure
```
/
├── api/
│   └── chat.js       ← Serverless function (Anthropic proxy)
├── index.html        ← The proposal
├── vercel.json       ← Vercel config
└── README.md
```

## Deploy to Vercel

### 1. Push this repo to GitHub
Upload all files as-is. Do not move or rename anything.

### 2. Add your Anthropic API key in Vercel
Vercel Dashboard → Your Project → Settings → Environment Variables

| Name | Value | Environment |
|------|-------|-------------|
| `ANTHROPIC_API_KEY` | `sk-ant-...` | Production, Preview, Development |

### 3. Deploy
Vercel will auto-deploy on every push to GitHub.

Your proposal will be live at your Vercel project URL (e.g. `your-project.vercel.app`).
You can add a custom domain like `vital.n3xus.media` in the Vercel dashboard.
