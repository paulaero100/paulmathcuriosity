# Chaos & Curiosity — Math Simulation Website

Your YouTube channel's companion website. Every episode gets a page with the YouTube embed + live interactive simulation.

Hosted free on **GitHub Pages**. Update by pushing to GitHub.

---

## One-Time Setup (20 minutes)

### Step 1 — Create GitHub account
Go to [github.com](https://github.com) and sign up (free).

### Step 2 — Create repository
1. Click **New repository**
2. Name it exactly: `mathsim-site`
3. Set to **Public**
4. Click **Create repository**

### Step 3 — Install Git on your laptop
- Windows: download from [git-scm.com](https://git-scm.com)
- Mac: open Terminal and run `git --version` (installs automatically)

### Step 4 — Upload the website files
Open Terminal (Mac) or Git Bash (Windows) and run:

```bash
cd /path/to/mathsim-site          # navigate to the folder you downloaded
git init
git add .
git commit -m "initial launch"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mathsim-site.git
git push -u origin main
```

### Step 5 — Enable GitHub Pages
1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Source", select **main** branch, **/ (root)** folder
4. Click **Save**

Your website will be live at:
```
https://YOUR_USERNAME.github.io/mathsim-site
```

---

## Adding a New Episode (After Every Video Upload)

Do this the same day you upload to YouTube.

### Step 1 — Copy episode folder
```bash
cp -r episodes/ep1 episodes/ep2
```

### Step 2 — Edit the new episode page
Open `episodes/ep2/index.html` and update:
- Episode number (`Episode 002`)
- Title, mystery question, tags
- YouTube video ID (get from your YouTube URL)
- Replace the simulation JavaScript with your new simulation code

To add YouTube embed, find this comment in the file:
```html
<!-- UNCOMMENT THIS after uploading to YouTube: -->
```
Remove the `<!--` and `-->` around the iframe, and replace `YOUR_VIDEO_ID` with your actual YouTube video ID.

### Step 3 — Register the episode on the homepage
Open `index.html` and find this comment:
```javascript
// ─── PASTE NEW EPISODES BELOW THIS LINE ───────────────────
```

Add your new episode object:
```javascript
{
  num: '002',
  title: 'Reaction Diffusion',
  mystery: 'How do leopard spots form from pure mathematics?',
  tags: ['Pattern Formation', 'Biology', 'PDEs'],
  date: '2024-01-08',              // use today's date
  youtube: 'YOUR_YOUTUBE_ID',
  path: 'episodes/ep2/',
  live: true
},
```

Also remove it from the `UPCOMING` array so it doesn't show as "coming soon" anymore.

### Step 4 — Push to GitHub (website updates instantly)
```bash
git add .
git commit -m "add episode 002 - reaction diffusion"
git push
```

**That's it.** The website updates in about 60 seconds.

---

## File Structure

```
mathsim-site/
├── index.html                 ← Homepage (episode grid)
├── README.md                  ← This file
└── episodes/
    ├── ep1/
    │   └── index.html         ← Episode 1 page (video + simulation)
    ├── ep2/
    │   └── index.html         ← Episode 2 page
    └── ep3/
        └── index.html         ← Episode 3 page (and so on...)
```

---

## Customization

### Change channel name
Search and replace `Chaos & Curiosity` across all HTML files.

### Change YouTube channel link
Search for `youtube.com/@yourchannel` and replace with your actual URL.

### Change GitHub repo link
Search for `yourusername/mathsim-site` and replace with your username.

### Change contact email
Search for `you@email.com` and replace.

---

## Episode Simulation Template

For each new episode, replace the `<script>` block in the episode HTML with your new simulation. Use p5.js or plain Canvas API.

To use p5.js, add this in the `<head>`:
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js"></script>
```

Then write your sketch in a `<script>` tag at the bottom.

---

## Quick Reference — Git Commands

| What you want to do | Command |
|---|---|
| Save changes and update website | `git add . && git commit -m "your message" && git push` |
| Check what files changed | `git status` |
| See history of updates | `git log --oneline` |
| Undo last change (before pushing) | `git checkout .` |

---

Built with plain HTML, CSS, and JavaScript. No frameworks, no build tools. Just push and it works.
