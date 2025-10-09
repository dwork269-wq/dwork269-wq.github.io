# Deployment Guide

This guide will help you deploy your Miruvor blog to GitHub Pages.

## Quick Start

### Step 1: Create a GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the "+" icon in the top right and select "New repository"
3. Name your repository (e.g., `miruvor-blog`)
4. Choose **Public** or **Private** (GitHub Pages works with both)
5. Click "Create repository"

### Step 2: Push Your Code

```bash
# Navigate to your project directory
cd /Users/dev/Documents/my/dwork269-wq

# Initialize git (if not already done)
git init

# Add all files
git add .

# Create your first commit
git commit -m "Initial commit: Miruvor blog"

# Add your GitHub repository as remote
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** tab
3. In the left sidebar, click **Pages**
4. Under "Source", select:
   - **Branch**: `main`
   - **Folder**: `/ (root)`
5. Click **Save**

Your site will be published at: `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

## Configuration Updates

After deployment, update `_config.yml` with your actual URL:

```yaml
url: "https://YOUR-USERNAME.github.io"
baseurl: "/YOUR-REPO-NAME" # Leave empty if using username.github.io
```

**Note:** If your repository is named `YOUR-USERNAME.github.io`, set `baseurl: ""` (empty).

## Testing Locally

Before deploying, test your site locally:

```bash
# Install dependencies (first time only)
bundle install

# Start the local server
bundle exec jekyll serve

# Visit http://localhost:4000 in your browser
```

Press `Ctrl+C` to stop the server.

## Publishing New Posts

1. Create a new file in `_posts/` directory
2. Name it: `YYYY-MM-DD-post-title.md`
3. Add content with front matter:

```markdown
---
title: "My New Post"
tags: [blockchain, payments]
---

Your amazing content here...
```

4. Commit and push:

```bash
git add _posts/YYYY-MM-DD-post-title.md
git commit -m "Add new post: Post Title"
git push
```

GitHub will automatically rebuild and publish your site in ~1-2 minutes.

## Custom Domain (Optional)

To use a custom domain like `blog.miruvor.me`:

1. Add a `CNAME` file to your repository root with your domain:

   ```
   blog.miruvor.me
   ```

2. Configure DNS with your domain provider:

   - Add a CNAME record pointing to `YOUR-USERNAME.github.io`
   - Or for apex domain, add A records pointing to GitHub's IPs

3. In GitHub Settings → Pages, add your custom domain

4. Update `_config.yml`:
   ```yaml
   url: "https://blog.miruvor.me"
   baseurl: ""
   ```

## Troubleshooting

### Site Not Building

- Check the **Actions** tab in your GitHub repository for build errors
- Verify your `_config.yml` syntax is correct
- Make sure all Markdown files have proper front matter

### CSS Not Loading

- Check that `baseurl` in `_config.yml` is set correctly
- Clear browser cache
- Inspect the page and check if CSS files are 404ing

### Posts Not Showing

- Verify post filename format: `YYYY-MM-DD-title.md`
- Check that posts have proper front matter
- Ensure posts are in the `_posts/` directory

## Build Time

- First deployment: 2-5 minutes
- Subsequent updates: 1-2 minutes

Check deployment status in the **Actions** tab on GitHub.

## Tips

- **Preview Changes**: Always test locally before pushing
- **Small Commits**: Make smaller, focused commits for easier debugging
- **Draft Posts**: Keep drafts outside `_posts/` until ready to publish
- **Backup**: GitHub is your backup, but keep local copies too

## Support

For Jekyll documentation: [jekyllrb.com](https://jekyllrb.com)  
For GitHub Pages: [pages.github.com](https://pages.github.com)

---

**Ready to go live?** Follow Step 1-3 above and your blog will be live in minutes! 🚀
