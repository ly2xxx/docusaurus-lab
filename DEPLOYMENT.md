# 🚀 Deployment Guide - Docusaurus Lab

**Repository:** https://github.com/ly2xxx/docusaurus-lab  
**Live Site:** https://ly2xxx.github.io/docusaurus-lab (after setup)  
**Status:** ✅ Code pushed to GitHub

---

## ✅ What's Already Done

1. **✅ Git repository initialized**
2. **✅ All files committed** (46 files, 20,894 insertions)
3. **✅ Pushed to GitHub:** https://github.com/ly2xxx/docusaurus-lab
4. **✅ GitHub Actions workflow added** (auto-deployment)

---

## 🔧 One-Time Setup Required

To enable GitHub Pages deployment, you need to configure the repository settings:

### Step 1: Enable GitHub Pages

1. Go to: https://github.com/ly2xxx/docusaurus-lab/settings/pages
2. Under **"Build and deployment"**:
   - **Source:** Select "GitHub Actions"
3. Click **Save**

**That's it!** The workflow will auto-deploy on every push to `main`.

---

## 🎯 How It Works

### Automatic Deployment

Every time you push to `main` branch:

```bash
cd C:\code\docusaurus-lab
git add .
git commit -m "Your changes"
git push
```

**GitHub Actions will:**
1. ✅ Install dependencies (`npm ci`)
2. ✅ Build the site (`npm run build`)
3. ✅ Deploy to GitHub Pages
4. ✅ Site live at: https://ly2xxx.github.io/docusaurus-lab

**Build time:** ~2-3 minutes

---

## 📊 Monitoring Deployments

**Check deployment status:**
- Go to: https://github.com/ly2xxx/docusaurus-lab/actions
- See workflow runs (green ✅ = success, red ❌ = failed)
- Click on a run to see logs

**Live site:**
- After first successful deployment: https://ly2xxx.github.io/docusaurus-lab
- Updates appear ~1 minute after workflow completes

---

## 🛠️ Local Development

```bash
# Start dev server (http://localhost:3000)
npm start

# Build locally (test before pushing)
npm run build

# Preview production build locally
npm run serve
```

---

## 📝 Workflow File

**Location:** `.github/workflows/deploy.yml`

**What it does:**
- Triggers on push to `main` or manual dispatch
- Builds Docusaurus site
- Deploys to GitHub Pages via Actions
- Uses Node.js 18
- Caches npm dependencies for faster builds

**Permissions:**
- `contents: read` - Read repo files
- `pages: write` - Deploy to Pages
- `id-token: write` - OIDC authentication

---

## 🔄 Making Changes

### Workflow:

1. **Edit locally:**
   ```bash
   cd C:\code\docusaurus-lab
   npm start  # Preview changes
   ```

2. **Test build:**
   ```bash
   npm run build
   npm run serve  # Preview production build
   ```

3. **Commit and push:**
   ```bash
   git add .
   git commit -m "Description of changes"
   git push
   ```

4. **Wait for deployment:**
   - Check Actions tab: https://github.com/ly2xxx/docusaurus-lab/actions
   - Site updates in ~3-4 minutes

---

## 🎨 Quick Customizations

### Change Site Title
**File:** `docusaurus.config.ts`
```typescript
title: 'Your New Title',
tagline: 'Your new tagline',
```

### Change Colors
**File:** `src/css/custom.css`
```css
:root {
  --ifm-color-primary: #your-color;
}
```

### Add New Doc
**Create:** `docs/your-doc.md`
```markdown
---
sidebar_position: 4
title: Your Doc Title
---

# Content here
```

**Auto-appears in sidebar!** Just push to deploy.

---

## 🚨 Troubleshooting

### Deployment Failed?

**Check Actions logs:**
1. Go to: https://github.com/ly2xxx/docusaurus-lab/actions
2. Click on failed workflow run
3. Expand failed step to see error

**Common issues:**
- **Build error:** Fix locally with `npm run build`, then push
- **Pages not enabled:** Follow Step 1 above
- **Wrong baseUrl:** Should be `/docusaurus-lab/` in config

### Site Not Updating?

1. **Check workflow ran:** https://github.com/ly2xxx/docusaurus-lab/actions
2. **Clear browser cache:** Ctrl+Shift+R (hard refresh)
3. **Wait longer:** Can take 3-5 minutes total

---

## 📊 Repository Stats

**Initial commit:**
- 46 files
- 20,894 lines of code
- Includes: docs, blog, guides, config, workflow

**Commits so far:**
1. ✅ Initial setup with learning guides
2. ✅ GitHub Actions deployment workflow

---

## 🎯 Next Steps

1. **Enable GitHub Pages** (see Step 1 above)
2. **Wait for first deployment** (~3 mins)
3. **Visit:** https://ly2xxx.github.io/docusaurus-lab
4. **Start learning!** Edit docs, add blog posts, experiment

---

## 📚 Resources

- **Repository:** https://github.com/ly2xxx/docusaurus-lab
- **Actions:** https://github.com/ly2xxx/docusaurus-lab/actions
- **Settings:** https://github.com/ly2xxx/docusaurus-lab/settings
- **Docusaurus Docs:** https://docusaurus.io/docs

---

## 💡 Pro Tips

1. **Test locally first** - Always run `npm run build` before pushing
2. **Watch Actions tab** - Monitor deployment progress
3. **Use feature branches** - Create branches for experiments
4. **Pull before edit** - If editing from multiple locations
5. **Read workflow logs** - They show exactly what went wrong

---

**Your Docusaurus lab is live on GitHub! 🎉**

**Total setup time:** ~10 minutes from zero to deployed! 🚀

---

## 🔗 Quick Links

| Link | URL |
|------|-----|
| **Repository** | https://github.com/ly2xxx/docusaurus-lab |
| **Live Site** | https://ly2xxx.github.io/docusaurus-lab |
| **Actions** | https://github.com/ly2xxx/docusaurus-lab/actions |
| **Settings** | https://github.com/ly2xxx/docusaurus-lab/settings/pages |
| **Local Dev** | http://localhost:3000 (via `npm start`) |

---

**Happy learning and deploying! 🦖🚀**
