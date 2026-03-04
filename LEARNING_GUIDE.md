# 🦖 Docusaurus Lab - Quick Learning Guide

**Created:** 2026-03-04  
**Purpose:** Hands-on learning environment for Docusaurus  
**Owner:** Master Yang

---

## 🚀 Quick Start

```bash
cd C:\code\docusaurus-lab

# Start dev server (hot reload enabled)
npm start

# Build for production
npm run build

# Preview production build
npm run serve
```

**Dev server:** Opens at `http://localhost:3000`  
**Changes auto-refresh** - edit and see results instantly!

---

## 📁 Project Structure

```
docusaurus-lab/
├── docs/                    # Documentation pages
│   ├── intro.md            # First doc page
│   ├── tutorial-basics/    # Tutorial section
│   └── tutorial-extras/    # Advanced tutorials
│
├── blog/                    # Blog posts (optional)
│   ├── 2024-01-01-welcome.md
│   └── authors.yml         # Blog authors
│
├── src/
│   ├── components/         # Custom React components
│   ├── css/               # Global styles
│   └── pages/             # Standalone pages (not docs)
│       └── index.tsx      # Homepage
│
├── static/                 # Static assets (images, files)
│   └── img/
│
├── docusaurus.config.ts   # ⭐ MAIN CONFIG FILE
├── sidebars.ts            # Sidebar navigation structure
└── package.json
```

---

## ⚙️ Key Configuration Files

### 1. `docusaurus.config.ts` - Site Configuration

**Most important settings:**

```typescript
const config = {
  title: 'Your Site Name',           // Browser title
  tagline: 'Your tagline here',      // Subtitle
  url: 'https://ly2xxx.github.io',   // Your domain
  baseUrl: '/docusaurus-lab/',       // Subpath (for GitHub Pages)
  
  // GitHub Pages deployment
  organizationName: 'ly2xxx',        // GitHub username
  projectName: 'docusaurus-lab',     // Repo name
  
  // Navbar links
  navbar: {
    title: 'My Site',
    logo: { /* ... */ },
    items: [
      { type: 'doc', docId: 'intro', label: 'Docs' },
      { to: '/blog', label: 'Blog' },
      { href: 'https://github.com/ly2xxx', label: 'GitHub' }
    ]
  },
  
  // Footer
  footer: { /* ... */ }
}
```

### 2. `sidebars.ts` - Docs Navigation

Controls left sidebar structure:

```typescript
const sidebars = {
  tutorialSidebar: [
    'intro',                          // Single doc
    {
      type: 'category',
      label: 'Tutorial',
      items: ['tutorial-basics/create-a-doc', ...]
    }
  ]
}
```

### 3. `docs/` - Your Documentation

Each markdown file becomes a page:

```markdown
---
sidebar_position: 1
title: My Page Title
---

# Content here

This is a regular markdown file with **frontmatter**.
```

---

## 🎨 Key Features to Explore

### 1. **Document Versioning**

```bash
npm run docusaurus docs:version 1.0.0
```

Creates a snapshot of current docs. Users can switch versions via dropdown.

**Use case:** Maintain docs for v1.0, v2.0, v3.0 simultaneously.

---

### 2. **Internationalization (i18n)**

```bash
npm run write-translations -- --locale zh-CN
npm run start -- --locale zh-CN
```

**Structure:**
```
i18n/
├── zh-CN/
│   ├── docusaurus-plugin-content-docs/
│   └── docusaurus-plugin-content-blog/
└── fr/
```

**Use case:** Support multiple languages (English, Chinese, French).

---

### 3. **MDX - Markdown + React**

You can use React components in markdown:

```mdx
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="python" label="Python">
    ```python
    print("Hello")
    ```
  </TabItem>
  <TabItem value="javascript" label="JavaScript">
    ```js
    console.log("Hello");
    ```
  </TabItem>
</Tabs>
```

**Result:** Interactive tabbed code blocks!

---

### 4. **Blog**

Just add markdown files to `blog/`:

```markdown
---
slug: my-first-post
title: My First Blog Post
authors: [yang]
tags: [ai, docusaurus]
---

Content here...
```

**Auto-generates:**
- Blog index page
- RSS feed
- Tag pages
- Author pages

---

### 5. **Search**

**Option A:** Local search (plugin)
```bash
npm install @easyops-cn/docusaurus-search-local
```

**Option B:** Algolia (free for open source)
- Add API key to config
- Algolia crawls your site
- Instant search across all docs

---

### 6. **Custom Pages**

Create React pages in `src/pages/`:

```typescript
// src/pages/projects.tsx
export default function Projects() {
  return (
    <Layout title="My Projects">
      <h1>Project Catalog</h1>
      {/* Your custom React code */}
    </Layout>
  );
}
```

**Result:** `localhost:3000/projects`

---

### 7. **Theming**

**Built-in themes:**
- Light mode
- Dark mode (auto-switching)

**Customization:**
```typescript
// docusaurus.config.ts
colorMode: {
  defaultMode: 'dark',
  respectPrefersColorScheme: true
}

themeConfig: {
  colorMode: { /* ... */ },
  prism: {
    theme: lightCodeTheme,
    darkTheme: darkCodeTheme
  }
}
```

**Custom CSS:**
```css
/* src/css/custom.css */
:root {
  --ifm-color-primary: #25c2a0;  /* Your brand color */
}
```

---

## 🧪 Learning Exercises

### Exercise 1: Add a New Doc Page
1. Create `docs/my-first-doc.md`
2. Add frontmatter: `sidebar_position: 2`
3. Write some markdown
4. See it appear in sidebar automatically!

### Exercise 2: Create a Custom Page
1. Create `src/pages/about.tsx`
2. Export a React component
3. Visit `http://localhost:3000/about`

### Exercise 3: Add a Blog Post
1. Create `blog/2026-03-04-learning-docusaurus.md`
2. Add frontmatter (title, author, tags)
3. Write content
4. Check blog index at `/blog`

### Exercise 4: Customize Navbar
1. Edit `docusaurus.config.ts`
2. Add new link in `navbar.items`
3. See it appear in top navigation

### Exercise 5: Use MDX Features
1. Edit `docs/intro.md` → rename to `intro.mdx`
2. Import a component: `import Tabs from '@theme/Tabs'`
3. Use it in your content
4. See interactive tabs!

---

## 🚀 Deployment (GitHub Pages)

### Option 1: GitHub Actions (Recommended)

`.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
      - run: npm ci
      - run: npm run build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```

**Push to main → auto-deploys!**

### Option 2: Manual Deploy

```bash
GIT_USER=ly2xxx npm run deploy
```

---

## 📚 What Makes Docusaurus Special

### ✅ **Designed for Documentation**
- Versioning built-in
- Sidebar auto-generation
- Search integration
- i18n support

### ✅ **Developer Experience**
- Hot reload
- TypeScript support
- MDX (React in Markdown)
- Plugin ecosystem

### ✅ **Production-Ready**
- Fast static site generation
- SEO optimized
- Dark mode
- Responsive design

---

## 🎯 When to Use Docusaurus

**✅ Great for:**
- **Technical documentation** (APIs, SDKs, libraries)
- **Multi-version docs** (v1, v2, v3 side-by-side)
- **Multi-language docs** (English, Chinese, etc.)
- **Project documentation + blog** (combo site)
- **Open-source projects** (like React, Jest, Redux)

**❌ Not ideal for:**
- Simple blogs (use Hugo, Jekyll)
- **Project showcases/portfolios** (overkill)
- Landing pages (too heavy)
- Non-documentation sites

---

## 🔧 Common Customizations

### Change Theme Colors
```css
/* src/css/custom.css */
:root {
  --ifm-color-primary: #2e8555;
  --ifm-color-primary-dark: #29784c;
  --ifm-color-primary-darker: #277148;
}
```

### Add Google Analytics
```typescript
// docusaurus.config.ts
gtag: {
  trackingID: 'G-XXXXXXXXXX'
}
```

### Add Mermaid Diagrams
```bash
npm install @docusaurus/theme-mermaid
```

```typescript
// docusaurus.config.ts
themes: ['@docusaurus/theme-mermaid'],
markdown: { mermaid: true }
```

---

## 📖 Next Steps

1. **Run the site:** `npm start`
2. **Explore default content** in `docs/` and `blog/`
3. **Edit `docusaurus.config.ts`** - change title, tagline
4. **Create a new doc** in `docs/my-doc.md`
5. **Add a blog post** in `blog/`
6. **Customize homepage** in `src/pages/index.tsx`
7. **Try MDX features** (tabs, admonitions, etc.)
8. **Build for production:** `npm run build`

---

## 📚 Official Resources

- **Docs:** https://docusaurus.io/docs
- **Showcase:** https://docusaurus.io/showcase (see what others built)
- **Plugins:** https://docusaurus.io/community/resources
- **Discord:** https://discord.gg/docusaurus

---

## 💡 Key Takeaways

1. **Config-driven:** Most things controlled via `docusaurus.config.ts`
2. **Convention over configuration:** Put markdown in `docs/`, it just works
3. **React-powered:** Full React ecosystem available
4. **Plugin-based:** Extend with plugins (search, analytics, etc.)
5. **Production-ready:** Used by Facebook, Uber, Airbnb, etc.

---

**Happy learning! 🦖**

Experiment, break things, rebuild. That's how you learn.

---

## 🧠 Your Use Case Analysis

**For ly2xxx catalog:**
- **Docusaurus:** Docs-focused, versioning, i18n ➜ **Overkill** ❌
- **Jekyll Collections:** Lightweight, catalog-focused ➜ **Perfect fit** ✅

**But Docusaurus is great for:**
- Your AI/ML project documentation
- Tutorial series
- Multi-language guides
- API reference docs

Consider using it for **project documentation**, not the catalog itself!
