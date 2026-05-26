# JOJX Astro Quick Start Guide

## ⚡ Get Started in 5 Minutes

### 1. Download & Install

```bash
# Clone the repository
git clone https://github.com/jzisjennzeller-code/jojx-astro.git
cd jojx-astro

# Install dependencies
npm install
```

### 2. Open in VS Code

```bash
code .
```

### 3. Start Development Server

```bash
npm run dev
```

Visit **http://localhost:3000** - your site is live and hot-reloading! 🔥

---

## 📝 Editing Your Content in VS Code

### Adding a New Director

1. **Open:** `src/data/directors.json`
2. **Add this object to the array:**

```json
{
  "id": "99",
  "name": "Director Name",
  "slug": "director-name",
  "bio": "Short biography (1-2 sentences about their style)",
  "image": "https://example.com/headshot.jpg",
  "reel": "https://vimeo.com/123456789",
  "featured": true
}
```

3. **Save the file** - Your site updates instantly!
4. **Visit:** `/directors/director-name` to see the new page

**Pro Tips:**
- `slug` must be unique (lowercase, hyphens, no spaces)
- `id` must be unique (use any number not already used)
- `featured: true` shows on homepage + directors page
- Images should be ~500x500px JPGs for best performance

---

### Adding New Work/Commercial

1. **Open:** `src/data/works.json`
2. **Add this object to the array:**

```json
{
  "id": "99",
  "title": "Commercial Title",
  "brand": "Brand Name",
  "slug": "commercial-slug",
  "description": "Brief description of the commercial (1 sentence)",
  "thumbnail": "https://example.com/thumbnail.jpg",
  "videoUrl": "https://vimeo.com/123456789",
  "directorId": "1",
  "featured": true
}
```

3. **Save file** - Video appears on `/work` page
4. **It also auto-links** to the director's page if `directorId` matches!

**Pro Tips:**
- `directorId` must match a director's `id` in `directors.json`
- `slug` must be unique (lowercase, hyphens)
- Use Vimeo videos for commercial content
- `featured: true` shows on homepage hero grid
- Thumbnail images should be ~1920x1080px

---

### Updating Header/Footer

**Header navigation:**
- **File:** `src/components/Header.astro`
- Edit the `<nav>` links

**Footer info:**
- **File:** `src/components/Footer.astro`
- Update email, location, social links

---

### Changing Site Colors

**File:** `tailwind.config.cjs`

```js
theme: {
  extend: {
    colors: {
      black: '#000000',    // ← change these
      white: '#FFFFFF',
      gray: '#888888',
    },
  },
},
```

---

## 🎨 File Structure Quick Reference

```
jojx-astro/
├── src/
│   ├── data/
│   │   ├── directors.json        ← EDIT: Add/remove directors
│   │   └── works.json            ← EDIT: Add/remove commercials
│   ├── components/
│   │   ├── Header.astro          ← EDIT: Nav links, logo
│   │   ├── Footer.astro          ← EDIT: Contact info, socials
│   │   ├── Hero.astro
│   │   ├── DirectorCard.astro
│   │   └── WorkCard.astro
│   ├── pages/
│   │   ├── index.astro           (/)
│   │   ├── contact.astro         (/contact)
│   │   ├── work/
│   │   │   └── index.astro       (/work)
│   │   └── directors/
│   │       ├── index.astro       (/directors)
│   │       └── [slug].astro      (/directors/[name])
│   └── styles/
│       └── global.css
├── astro.config.mjs
├── tailwind.config.cjs
├── package.json
├── README.md
└── docs/
    ├── PROJECT_SCOPE.md          ← Read this for full details
    └── DESIGN_SYSTEM.md          ← Component reference
```

---

## 🚀 Deploy to Netlify

### Option 1: Automatic (Recommended)

1. **Push changes to GitHub**
   ```bash
   git add .
   git commit -m "Update content"
   git push origin main
   ```

2. **Go to [netlify.com](https://netlify.com)**
3. **Click "New site from Git"**
4. **Connect your repo** `jzisjennzeller-code/jojx-astro`
5. **Accept default build settings:**
   - Build command: `npm run build`
   - Publish directory: `dist`
6. **Deploy!**

Netlify will automatically rebuild and deploy every time you push to GitHub.

### Option 2: Manual Deploy

```bash
# Build your site
npm run build

# This creates a 'dist' folder

# Drag & drop 'dist' folder to https://drop.netlify.com
# Done! Your site is live
```

---

## ✅ Common Tasks

### View Local Site
```bash
npm run dev
# Opens http://localhost:3000
```

### Build for Production
```bash
npm run build
# Creates optimized 'dist' folder
```

### Restart Dev Server
```
Press Ctrl+C to stop
npm run dev
```

### Preview Production Build
```bash
npm run preview
# Shows what Netlify will deploy
```

---

## 🐛 Troubleshooting

### Site won't start?

```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
npm run dev
```

### Changes aren't showing?

- Make sure you **saved the file** (Cmd+S / Ctrl+S)
- Check browser console for errors (F12)
- Hard refresh: Cmd+Shift+R (Mac) or Ctrl+Shift+R (Windows)

### JSON syntax error?

- Check `src/data/directors.json` or `src/data/works.json`
- Use [jsonlint.com](https://jsonlint.com) to validate
- Missing commas between objects cause errors

### Video not playing?

- Make sure `videoUrl` is a Vimeo embeddable link
- Check that video visibility is set to public on Vimeo
- Verify URL format: `https://vimeo.com/[VIDEO_ID]`

---

## 📚 Learning Resources

- **Astro Docs**: https://docs.astro.build
- **Tailwind CSS**: https://tailwindcss.com/docs
- **Netlify Docs**: https://docs.netlify.com
- **Vimeo Embed**: https://vimeo.com/api/embed

---

## 🎯 Next Steps

1. ✅ Clone repo locally
2. ✅ Run `npm install && npm run dev`
3. ✅ Edit `src/data/directors.json` with real data
4. ✅ Edit `src/data/works.json` with commercials
5. ✅ Update contact info in `src/components/Footer.astro`
6. ✅ Test everything at `localhost:3000`
7. ✅ Deploy to Netlify
8. ✅ Point your domain to Netlify

**You're ready to go!** 🚀
