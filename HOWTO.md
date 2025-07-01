
# 🛠 How to Update and Publish the NHS Analytical Product Design Guide - South West

This guide explains how to correctly update and publish content to the MkDocs-powered site hosted at:

👉 **[https://hannahmitchell35.github.io/analytical-data-style-guide-SW/](https://hannahmitchell35.github.io/analytical-data-style-guide-SW/)**

---

## ⚠️ What *not* to do

- **❌ DO NOT manually change anything in the `gh-pages` branch.**
  > It's automatically managed by GitHub Actions and MkDocs.

- **❌ DO NOT commit directly into `site/` folder (if present locally).**
  > MkDocs builds this from your Markdown and config.

- **❌ DO NOT change GitHub Pages settings in `Settings > Pages` unless absolutely necessary.**

---

## ✅ Where to make changes

| What you want to change | Where to do it | Notes |
|--------------------------|----------------|-------|
| Content pages | `docs/` folder | e.g. `launch.md`, `reporting_corecomponents/index.md` |
| Navigation (sidebar) | `mkdocs.yml` | Update the `nav:` section |
| Site title, theme, config | `mkdocs.yml` | Careful with indentation! |
| Styling | `docs/stylesheets/extra.css` or `overrides/` |
| GitHub Actions deployment | `.github/workflows/pages.yml` | Already set up ✅ |

---

## 📝 Making a content update (step-by-step)

1. **Edit Markdown in `docs/`**
   - All content pages live here.
   - Example: Add a new page called `docs/my_new_page.md`.

2. **Update navigation in `mkdocs.yml`**
   - Add your new page under the appropriate section like this:
     ```yaml
     nav:
       - Core Components:
           - My New Page: my_new_page.md
     ```

3. **Commit and push changes to the `main` branch**
   ```bash
   git add .
   git commit -m "Add my new page"
   git push origin main
   ```

4. **Wait for GitHub Actions to deploy**
   - You'll see a green check mark next to the commit once it's complete.
   - Usually takes 30–60 seconds.

5. **Refresh your published site**
   - Visit: [https://hannahmitchell35.github.io/analytical-data-style-guide-SW/](https://hannahmitchell35.github.io/analytical-data-style-guide-SW/)
   - Do a hard refresh (Ctrl + Shift + R or Cmd + Shift + R) to clear cache.

---

## 🛠 What happens behind the scenes?

- Every time you **push to the `main` branch**, GitHub Actions:
  1. Installs the MkDocs dependencies from `requirements.txt`.
  2. Builds your site using `mkdocs build`.
  3. Deploys to the `gh-pages` branch using GitHub Pages native actions.
  4. GitHub Pages serves that `gh-pages` branch as your public site.

You don’t need to manually trigger anything.

---

## 💡 Troubleshooting tips

| Problem | Solution |
|--------|----------|
| Changes not appearing on the website | Wait ~1 min, hard refresh browser |
| Build fails in Actions | Check for YAML errors, missing files in `mkdocs.yml` |
| GitHub Pages showing wrong content | Confirm `gh-pages` is auto-deployed, **do not edit manually** |
| File excluded warning | Ensure file paths in `mkdocs.yml` match actual files |
| You need to "unpublish" a section | Move the folder to `/archived` or comment out from `nav` |

---

## 📁 Folder structure explained

```
analytical-data-style-guide-SW/
│
├── docs/                    # All site content in Markdown
│   ├── index.md             # Home page
│   ├── launch.md            # Launch info
│   ├── reporting_corecomponents/
│   └── archived/            # Old/unused content
│
├── mkdocs.yml               # Core config: theme, nav, plugins
├── requirements.txt         # Python packages for MkDocs
├── .github/workflows/pages.yml # GitHub Actions for deployment
```

---

## ✅ Final checks before pushing

- [ ] Content added in `docs/`
- [ ] `mkdocs.yml` navigation updated
- [ ] GitHub Actions workflow shows green ✅
- [ ] Site reflects changes after ~1 min
