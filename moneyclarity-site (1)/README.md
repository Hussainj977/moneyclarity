# MoneyClarity — Launch Guide

Everything below assumes you're starting from zero: no GitHub repo, no Netlify site yet.

## What's in this folder

- **Eleventy (11ty) static site** — fast, simple, no database
- **3 starter blog posts** already written and live-ready
- **Halal Personal Finance pillar page** — the flagship page, fully drafted
- **Netlify CMS (Decap CMS)** wired up at `/admin` so you can write future posts from a browser, no code needed
- **Subscribe form** on the homepage using Netlify Forms (free, no email service needed to start)

## Step 1 — Push to GitHub

```bash
cd moneyclarity
git init
git add .
git commit -m "Launch MoneyClarity"
```

Create a new empty repo on GitHub called `moneyclarity` (github.com/new — don't initialize with a README), then:

```bash
git remote add origin https://github.com/YOUR-USERNAME/moneyclarity.git
git branch -M main
git push -u origin main
```

## Step 2 — Connect Netlify

1. Go to [app.netlify.com](https://app.netlify.com) → **Add new site → Import an existing project**
2. Pick GitHub, authorize, select the `moneyclarity` repo
3. Build settings should auto-detect from `netlify.toml`:
   - Build command: `npm run build`
   - Publish directory: `_site`
4. Click **Deploy**. First build takes ~1-2 minutes.

Your site will be live at a `*.netlify.app` URL immediately. You can add your own domain later under **Domain settings**.

## Step 3 — Turn on the subscribe form

Netlify Forms works automatically once deployed — no setup needed. Go to **Site settings → Forms** to see submissions and set up email notifications so you get pinged when someone subscribes.

## Step 4 — Enable the CMS (so you can post from your phone/browser)

The CMS at `/admin` needs Netlify Identity + Git Gateway to let you log in and publish without touching code:

1. In Netlify: **Site settings → Identity → Enable Identity**
2. Under Identity settings, set **Registration** to "Invite only" (so random people can't sign up)
3. Under **Services**, enable **Git Gateway**
4. Go to **Identity** tab on your site dashboard → **Invite users** → invite yourself
5. Check your email, accept, set a password
6. Visit `yoursite.netlify.app/admin` and log in — you'll see the Posts and Pages editor

From then on, writing a new post is: open `/admin` on your phone → New Post → write → publish. It commits straight to GitHub and Netlify rebuilds automatically.

## Step 5 — What's already live at launch

- Homepage with hero + latest posts + subscribe form
- `/halal-personal-finance/` — the pillar page
- 3 blog posts:
  - Why "Just Save 20%" Doesn't Work for Halal Personal Finance
  - Zakat Is a Financial Obligation, Not a Feeling
  - Screening a Stock for Halal Investing: A 5-Minute Checklist
- `/about/` page
- `/blog/` index

## Local development (optional)

```bash
npm install
npm run dev
```

Opens a local server with live reload at `http://localhost:8080`.

## Next steps after launch

- Work through the 16-week content calendar — add each new post either locally (`src/posts/`) or via `/admin`
- Consider connecting a real email provider (Mailerlite, ConvertKit) once subscriber count justifies it — Netlify Forms is fine for the first weeks
- Point your custom domain once you've picked one
