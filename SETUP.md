# Cookie Fortune — Setup Guide

## Files
- `index.html` — submit page (photo + name + cookie name + description → fortune reveal)
- `gallery.html` — live gallery, auto-refreshes every 8s. Has a "New party" button to reset.

---

## Step 1: Create a Supabase project (free, no credit card)

1. Go to https://supabase.com → create a free account
2. Click **New project**, name it anything (e.g. `cookie-fortune`)
3. Wait for it to spin up (~1 min)

---

## Step 2: Create the database table

Go to **Table Editor** → **New Table**, name it `cookies`, and add these columns:

| Column | Type | Nullable |
|--------|------|----------|
| id | int8 (PK, auto) | no |
| creator_name | text | yes |
| name | text | no |
| description | text | yes |
| photo_url | text | no |
| fortune | text | no |
| created_at | timestamptz (default: now()) | no |

---

## Step 3: Create a Storage bucket

1. Go to **Storage** in the left sidebar
2. Click **New bucket**, name it: `cookie-photos`
3. Toggle **Public bucket** ON
4. Click **Create bucket**

---

## Step 4: Get your API keys

Go to **Settings → API** and copy:
- **Project URL**
- **anon public** key
- **service_role** key (used for the reset/delete on the gallery page)

---

## Step 5: Add keys to both files

In `index.html` and `gallery.html`, find and replace:

```js
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';
```

In `gallery.html` also replace:
```js
const SUPABASE_SERVICE_KEY = 'YOUR_SUPABASE_SERVICE_ROLE_KEY';
```

---

## Step 6: Write your 15 fortunes

In `index.html`, find the `FORTUNES` array and replace all 15 placeholder strings with your own. Make them personal to Emma (or whoever the party is for).

---

## Step 7: Customize the header text

In both files, find and update:
```html
<span class="header-chip">🎂 Emma's 28th · Cookie Party</span>
```

---

## Step 8: Deploy to GitHub Pages

1. Create a GitHub repo (e.g. `cookie-fortune`)
2. Upload `index.html` and `gallery.html`
3. Go to **Settings → Pages → Source: main branch → Save**
4. Your URL: `https://yourusername.github.io/cookie-fortune`

---

## At the party

- Open `gallery.html` on a laptop or TV — it updates live every 8 seconds
- Everyone opens the site on their phone and submits their cookie
- Each person gets their fortune privately after submitting

## After the party

- Open `gallery.html` → click **New party** in the top right
- A 15-second countdown appears at the bottom with an **Undo** button
- After 15 seconds, all cookies are cleared and the app is ready for the next event

---

## Reusing for a different event

Change three things in both files:
1. The header chip text
2. The fortunes array (in `index.html`)
3. That's it — everything else works as-is
