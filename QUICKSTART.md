# Quick Start Guide 🚀

Get your Miruvor blog live in 5 minutes!

## Prerequisites

- GitHub account
- Git installed on your computer

## Step 1: Test Locally (Optional but Recommended)

```bash
# Navigate to project
cd /Users/dev/Documents/my/dwork269-wq

# Install Jekyll (if not installed)
gem install bundler jekyll

# Install dependencies
bundle install

# Start local server
bundle exec jekyll serve

# Open http://localhost:4000 in your browser
```

## Step 2: Deploy to GitHub

### A. Create Repository on GitHub

1. Go to github.com
2. Click "+" → "New repository"
3. Name it (e.g., "miruvor-blog")
4. Click "Create repository"

### B. Push Your Code

```bash
# In your project directory
cd /Users/dev/Documents/my/dwork269-wq

# Initialize git (if needed)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: Miruvor blog with dark theme"

# Add your GitHub repo (replace with your actual URL)
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git

# Push
git branch -M main
git push -u origin main
```

### C. Enable GitHub Pages

1. Go to your repo on GitHub
2. Click **Settings**
3. Click **Pages** in sidebar
4. Under "Source":
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**

**Your site is now live!** 🎉

Visit: `https://YOUR-USERNAME.github.io/YOUR-REPO/`

## Step 3: Update Configuration

Edit `_config.yml`:

```yaml
url: "https://YOUR-USERNAME.github.io"
baseurl: "/YOUR-REPO"
```

Commit and push:

```bash
git add _config.yml
git commit -m "Update site URL"
git push
```

Wait 1-2 minutes for rebuild.

## Next Steps

### Add Your First Post

```bash
# Create new post
touch _posts/2025-02-13-my-first-post.md

# Edit the file with:
---
title: "My First Post"
tags: [updates]
---

This is my first post on the new blog!

# Commit and push
git add _posts/2025-02-13-my-first-post.md
git commit -m "Add first post"
git push
```

### Update Founder Page

Edit `pages/founder.md` with your bio and information.

### Customize Colors (Optional)

Edit `assets/css/style.css` - change the color variables:

```css
--bg: #0d1117; /* Background color */
--fg: #e6edf3; /* Text color */
--muted: #8b949e; /* Muted text */
--link: #58a6ff; /* Link color */
```

## Troubleshooting

**Site not building?**

- Check GitHub Actions tab for errors
- Verify all Markdown files have front matter

**CSS not loading?**

- Check `baseurl` in `_config.yml`
- Clear browser cache

**Posts not showing?**

- Verify filename format: `YYYY-MM-DD-title.md`
- Check that posts are in `_posts/` directory

## File Structure Reference

```
your-repo/
├── _posts/              ← Add blog posts here
├── pages/
│   ├── blog.md         ← Blog listing
│   ├── founder.md      ← Edit your bio here
│   └── ...
├── index.md            ← Home page
├── _config.yml         ← Site settings
└── assets/css/style.css ← Styling
```

## Daily Workflow

1. Write post in `_posts/YYYY-MM-DD-title.md`
2. Test locally: `bundle exec jekyll serve`
3. Commit: `git add . && git commit -m "Add post"`
4. Push: `git push`
5. Wait ~1 minute for live update

## Support

- 📖 Full docs: See `README.md`
- 🚀 Deployment details: See `DEPLOYMENT.md`
- 📋 Changes made: See `CHANGES.md`

---

**That's it!** You now have a fast, beautiful, dark-themed blog that matches the original Miruvor site. Happy blogging! ✨
