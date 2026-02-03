---
description: How to add a new texture pack repo to the dashboard
---

# Adding a New Texture Pack

When you create a new texture pack repository on GitHub, follow these steps to integrate it with countxd.github.io.

## Step 1: Create Your GitHub Repo

Create the repo with branches for each Minecraft version (e.g., `1.20-1.20.1`, `1.21-1.21.1`, `latest`).

## Step 2: Update the Dashboard

Edit `index.html` and add your repo name to the `SUBPAGE_REPOS` array (~line 680):

```javascript
const SUBPAGE_REPOS = [
    'enchant-icons',
    'enchant-icons-colorless',
    'cassette-music-discs',
    'square-music-discs',
    'my-minimal-armor',
    'your-new-pack'  // ← Add your new repo here
];
```

This adds a "View Downloads" button to your repo card on the dashboard.

## Step 3: Create the Download Sub-Page

1. Copy an existing sub-page folder (e.g., `enchant-icons/`)
2. Rename it to match your repo name exactly
3. Edit `index.html` inside and change:

```javascript
const REPO = 'your-new-pack';  // ← Your repo name
```

4. Optionally customize:
   - Page title and `<h1>`
   - Description text
   - Icon emoji in `.pack-icon`
   - Accent color (search for `--accent` in CSS)
   - Modrinth link (if published there)

## Step 4: Commit and Push

```bash
git add -A
git commit -m "Add your-new-pack download page"
git push origin main
```

## Color Reference

| Pack Type | Accent Color | Hex |
|-----------|--------------|-----|
| Purple (default) | `#8b5cf6` | Enchant Icons |
| Gray | `#6b7280` | Colorless |
| Pink | `#ec4899` | Cassette |
| Blue | `#3b82f6` | Square |
| Orange | `#f59e0b` | Armor |

## Notes

- The dashboard auto-fetches new repos from GitHub API
- Download pages auto-fetch branches for version buttons
- ZIPs are repackaged client-side (no root folder, no README/.gitattributes)
