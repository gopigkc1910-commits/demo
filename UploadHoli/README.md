# HoliHub (Mood + Festival Card Generator)

Single-page greeting app with shareable links, reactions, music search, and a Node/Express backend.

## Features

- Mood cards: Romantic, Sorry, Friendship, Crush, Funny, Breakup, Celebration
- Festival cards: Holi, Diwali, Christmas, New Year, Eid, Raksha Bandhan
- Shareable wish links: `/wish/:id`
- View counter per card
- Anonymous sender mode
- Reactions: love, funny, emotional, romantic
- Trending cards endpoint
- Daily mood prompt + random confession endpoint
- AI message generation endpoint (Hugging Face fallback to template)
- Basic spam checks + rate limiting

## Local Run

```bash
npm install
node server.js
```

Open: `http://localhost:3000`

## Environment Variables

Copy root `.env.example` values into Render env vars (or a local `.env`):

- `PORT` (default `3000`)
- `WISHES_FILE` (default `UploadHoli/wishes.json`, set to `/var/data/wishes.json` on Render)
- `ADMIN_PIN` (required for delete action in recent list)
- `SPOTIFY_CLIENT_ID` (optional, recommended)
- `SPOTIFY_CLIENT_SECRET` (optional, recommended)
- `HF_API_TOKEN` (optional for AI message endpoint)
- `RATE_LIMIT_WINDOW_MS` (optional)
- `RATE_LIMIT_MAX` (optional)
- `MAX_WISHES_PER_HOUR_PER_IP` (optional)

## Render Deploy

Use these settings:

- Root Directory: `UploadHoli`
- Build Command: `npm install`
- Start Command: `node server.js`
- Environment: `Node`
- Persistent Disk: mount at `/var/data`
- Render env var: `WISHES_FILE=/var/data/wishes.json`

Health check endpoint:

- `GET /api/health`

## SEO Routes Added

- `/romantic-message-generator`
- `/sorry-message-generator`
- `/friendship-message-generator`
- `/holi-wishes`
- `/diwali-wishes`
