# 🍪 Cookie Fortune

A live, real-time web app built for a birthday cookie decorating party — and designed to be reused for any gathering.

## What it does

Guests photograph their decorated cookie, give it a name, and submit it to a shared live gallery. After submitting, a cookie dramatically "breaks" on screen to reveal a personal fortune — hand-written by the host, randomly assigned.

The gallery updates every 8 seconds in real time, so it can live on a shared laptop or TV while everyone submits from their phones.

## Why I built it

My sister's 28th birthday had a cookie decorating party. I wanted the activity to feel effortless — no pressure on how to decorate, no judging, no ranking — just a way to celebrate every creation equally and give everyone a small, personal moment.

The fortune mechanic came from wanting something she could carry beyond the party. A random assignment means no one knows why they got theirs, which makes it feel more like fate than curation.

## Stack

- **Frontend**: Vanilla HTML/CSS/JS — no framework, intentionally lightweight
- **Database**: [Supabase](https://supabase.com) (free tier) — real-time reads, REST API
- **Hosting**: GitHub Pages (free)
- **Images**: Compressed client-side before upload to stay within Supabase free limits

## Features

- 📸 Photo capture with client-side compression
- 🍪 Cookie-break fortune reveal animation
- 🖼️ Live masonry gallery (auto-refreshes every 8s)
- 🔐 Password-protected admin panel to reset between events
- 🌸 Lilac aesthetic with floating petals and cookie cursor

## Setup

### 1. Supabase

1. Create a free project at [supabase.com](https://supabase.com)
2. Create a table called `cookies` with these columns:

| Column | Type | Notes |
|--------|------|-------|
| id | int8 | Primary key, auto-increment |
| creator_name | text | nullable |
| name | text | not null |
| description | text | nullable |
| photo | text | stores compressed base64 |
| fortune | text | not null |
| created_at | timestamptz | default: now() |

3. Go to **Settings → API** and copy your Project URL and anon key

### 2. Add your keys

In `index.html`, `gallery.html`, and `admin.html`, replace:

```js
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';
```

For `admin.html` also add your service role key (Settings → API → service_role).

### 3. Write your fortunes

In `index.html`, find the `FORTUNES` array and replace all 15 with your own. Make them personal.

### 4. Deploy to GitHub Pages

1. Push all files to a GitHub repo
2. Settings → Pages → Source: main branch
3. Your URL: `https://yourusername.github.io/repo-name`

## Reuse for any event

Change three things:
1. The header chip text (`Emma's 28th · Cookie Party`)
2. The fortunes array
3. The admin password

Everything else works out of the box.

---

Built with care for a real person, for a real party. No AI-generated content visible to guests.
