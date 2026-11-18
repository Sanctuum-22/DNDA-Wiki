# How to Edit This Wiki

*For staff. You need to be added as a collaborator on the GitHub repository first.*

## Editing an existing page

1. On the wiki, open the page you want to change.
2. Click the **pencil icon** :material-pencil: at the top right of the page.
3. GitHub opens the page's text. Make your changes.
4. Click **Commit changes…** (green button), write a short note like *"Updated rest rules"*, then **Commit changes** again.
5. Wait about **1–2 minutes**, then refresh the wiki. Your change is live.

## Adding a new page

1. On GitHub, go into the `docs` folder (or a subfolder like `docs/characters`).
2. Click **Add file → Create new file**.
3. Name it with lowercase and dashes, ending in `.md`, e.g. `homebrew-rules.md`.
4. Start with a title line: `# Homebrew Rules`, then write the page. Commit it.
5. Open `zensical.toml` (in the main folder), find the `nav = [` section, and add a line for your page, e.g.
   ```toml
   { "Homebrew Rules" = "homebrew-rules.md" },
   ```
6. Commit. The page appears in the menu after the rebuild.

## If something goes wrong

- Click the **Actions** tab on GitHub. A red ❌ means the last change broke the build. Click it to see why. Usually it's a missing comma or quote mark in `zensical.toml`.
- Every change is saved in history, so nothing is ever truly lost. Ask the site owner to undo it.

See the **[Formatting Cheat Sheet](formatting.md)** for boxes, tables, tabs and more.
