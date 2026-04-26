# AFL Championship Manager — Vercel Deployment Guide

## What you need
- A **GitHub account** (free) — github.com
- A **Vercel account** (free) — vercel.com (sign up with GitHub)
- **Git** installed on your computer

## Step 1 — Get the game file

The game is a single `index.html` file. Copy the full HTML from the Claude chat widget (right-click → View Page Source on the widget, or ask Claude to output it as a downloadable file).

Save it as `index.html`.

## Step 2 — Create the project folder

```
mkdir afl-manager
cd afl-manager
```

Put your `index.html` inside this folder.

## Step 3 — Add Vercel config

Create `vercel.json` in the same folder:

```json
{
  "version": 2,
  "builds": [
    { "src": "index.html", "use": "@vercel/static" }
  ],
  "routes": [
    { "src": "/(.*)", "dest": "/index.html" }
  ]
}
```

## Step 4 — Create a GitHub repository

1. Go to **github.com/new**
2. Name it `afl-manager`
3. Leave it **Public** (required for free Vercel)
4. Click **Create repository**

## Step 5 — Push to GitHub

In your `afl-manager` folder:

```bash
git init
git add .
git commit -m "AFL Championship Manager v1"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/afl-manager.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your actual GitHub username.

## Step 6 — Deploy to Vercel

1. Go to **vercel.com** and sign in with GitHub
2. Click **Add New → Project**
3. Find `afl-manager` in your GitHub repos and click **Import**
4. Leave all settings as default — Vercel auto-detects it's a static site
5. Click **Deploy**

⏱️ Deployment takes about 30 seconds.

## Step 7 — Your live URL

Vercel gives you a URL like:
```
https://afl-manager-abc123.vercel.app
```

You can set a custom domain in Vercel settings if you want (e.g. `afl-manager.com`).

## Updating the game

Whenever Claude adds new features, just replace `index.html` and push:

```bash
git add index.html
git commit -m "Updated game features"
git push
```

Vercel automatically redeploys on every push. ✅

---

## Alternative: Deploy without GitHub (even faster)

Install the Vercel CLI:
```bash
npm install -g vercel
```

Then in your `afl-manager` folder:
```bash
vercel
```

Follow the prompts — done in under a minute, no GitHub needed.
