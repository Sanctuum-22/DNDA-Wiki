# DNDAnonymous Wiki: Setup Guide

This folder is a complete, ready-to-publish wiki website for a Discord server. It's built with **Zensical** (the successor to Material for MkDocs) and hosted free on **GitHub Pages**.

You don't need to install anything on your computer. Everything is done in the browser.

---

## Part 1: Put it on GitHub (about 15 minutes, once only)

### 1. Create a repository
1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click **+** (top right) → **New repository**.
3. Name it something short, e.g. `dnda-wiki`. This becomes part of your web address.
4. Set it to **Public** (free GitHub Pages sites must be public).
5. Leave everything else unticked and click **Create repository**.

### 2. Upload the files
1. On the new, empty repository page, click the link **"uploading an existing file"**.
2. Unzip the download on your computer and open the folder.
3. **Show hidden files first.** There's a folder called `.github` that your computer hides by default, and the site won't publish without it.
   - **Mac:** in Finder press `Cmd + Shift + .` (full stop)
   - **Windows:** in File Explorer choose **View → Show → Hidden items**
4. Select **everything inside** the folder (`.github`, `docs`, `zensical.toml`, `README.md`) and drag it into the GitHub upload box.
5. Click **Commit changes**.

> **Check:** you should now see a `.github` folder in the file list on GitHub. If it's missing, see *"The .github folder didn't upload"* at the bottom.

### 3. Switch on GitHub Pages
1. In your repository, click **Settings** (top bar) → **Pages** (left menu).
2. Under **Build and deployment → Source**, choose **GitHub Actions**.

### 4. Put in your own details
1. Back on the **Code** tab, click `zensical.toml` → the **pencil icon** to edit.
2. Change the three lines near the top:
   ```toml
   site_name = "DNDAnonymous Wiki"
   site_url  = "https://YOUR-USERNAME.github.io/YOUR-REPO/"
   repo_url  = "https://github.com/YOUR-USERNAME/YOUR-REPO"
   ```
   e.g. if your GitHub username is `samdm` and the repo is `dnda-wiki`:
   ```toml
   site_name = "DNDAnonymous Wiki"
   site_url  = "https://samdm.github.io/dnda-wiki/"
   repo_url  = "https://github.com/samdm/dnda-wiki"
   ```
3. Further down, replace `https://discord.gg/YOUR-INVITE` with your server invite.
4. Click **Commit changes**.

### 5. Watch it go live
1. Click the **Actions** tab. You'll see a job running (yellow dot).
   - The very first run (from the upload) may show a red ❌ because Pages wasn't switched on yet. That's normal; ignore it.
2. When the newest run shows a green ✅ (about a minute), your wiki is live at
   `https://YOUR-USERNAME.github.io/YOUR-REPO/`

### 6. Let other staff edit
**Settings → Collaborators → Add people**, then enter their GitHub usernames. Once they accept, they can use the pencil icon on any wiki page.

---

## Part 2: Day-to-day editing

The wiki itself contains a full staff guide under **Staff → How to Edit This Wiki** and a **Formatting Cheat Sheet**. In short:

| To… | Do this |
|-----|---------|
| Change a page | Click the pencil icon on the wiki page → edit → **Commit changes** |
| Add a page | In `docs/`, **Add file → Create new file**, name it `something.md`, then add it to the `nav` list in `zensical.toml` |
| Change the menu order | Reorder the lines in `nav` in `zensical.toml` |
| Change colours | Edit `primary` / `accent` in `zensical.toml` |
| Add images | Upload them into `docs/assets/` |

Changes go live about a minute after you commit.

---

## What's in the folder

```
.github/workflows/docs.yml   ← tells GitHub how to build and publish (don't touch)
zensical.toml                ← site name, colours, menu
docs/                        ← all the pages (one .md file per page)
  index.md                   ← home page
  rules.md, faq.md
  getting-started/  characters/  bots/  staff/
  assets/                    ← put images here
```

---

## Troubleshooting

**The .github folder didn't upload**
1. In the repository click **Add file → Create new file**.
2. In the name box, type exactly: `.github/workflows/docs.yml` (the slashes create the folders).
3. Paste this in and commit:
```yaml
name: Documentation
on:
  push:
    branches:
      - master
      - main
permissions:
  contents: read
  pages: write
  id-token: write
jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/configure-pages@v6
      - uses: actions/checkout@v7
      - uses: actions/setup-python@v6
        with:
          python-version: 3.x
      - run: pip install zensical
      - run: zensical build --clean
      - uses: actions/upload-pages-artifact@v5
        with:
          path: site
      - uses: actions/deploy-pages@v5
        id: deployment
```

**A red ❌ in Actions after an edit**
Click it and open the failed step to read the error. It's almost always a typo in `zensical.toml`, such as a missing comma, quote mark or bracket in the `nav` list. Fix it and commit again.

**Page not found (404)**
Check that `site_url` in `zensical.toml` exactly matches your address, including the trailing `/`, and that **Settings → Pages → Source** is set to **GitHub Actions**.
