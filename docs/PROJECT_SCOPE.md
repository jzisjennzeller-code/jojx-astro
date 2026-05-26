# JOJX V1 Project Scope

## 🎯 Overview

JOJX Landing Page V1 built with Astro, styled with high-contrast black/white editorial aesthetic, and content-managed via JSON files for easy editing in VS Code.

**Deployment Target:** Netlify (static generation)

---

## 📋 V1 Scope

### Pages Included

1. **Landing Page** (`/`)
   - Animated hero with text reveal
   - Featured work grid (6 videos)
   - Directors showcase (4 featured)
   - CTA sections
   - Scroll-to-work anchor

2. **Directors Directory** (`/directors`)
   - Grid of all directors
   - Cards with headshots, bio, CTA buttons
   - Links to individual director pages

3. **Individual Director Pages** (`/directors/[slug]`)
   - Director hero section with image + bio
   - Featured works by that director
   - Related directors suggestions
   - "Inquire About Work" CTA

4. **Work Gallery** (`/work`)
   - Full grid of all works
   - Video cards with brand/title overlay
   - Links to Vimeo/video hosting

5. **Contact Page** (`/contact`)
   - Contact info (email, location)
   - Social links (Instagram, Vimeo)
   - Netlify form for inquiries
   - Automated Netlify form submissions

### Not in V1 Scope

- ❌ Blog/News section
- ❌ Case studies (just title + video)
- ❌ Client testimonials
- ❌ Award submissions
- ❌ Custom CMS dashboard
- ❌ Admin authentication
- ❌ Search/filtering (consider for V2)

---

## 🗂️ Content Management (JSON-Based)

### Why JSON?

✅ **Easy to edit in VS Code** - No CMS learning curve  
✅ **Version control** - Git tracks changes  
✅ **No backend** - Fully static site  
✅ **Fast** - No API calls needed  
✅ **Free** - No CMS subscriptions  

### Content Files

**Directors:** `src/data/directors.json`

```json
[
  {
    "id": "1",
    "name": "Ace Norton",
    "slug": "ace-norton",
    "bio": "Short bio (1-2 sentences)",
    "image": "https://...",
    "reel": "https://vimeo.com/...",
    "featured": true
  }
]
```

**Works:** `src/data/works.json`

```json
[
  {
    "id": "1",
    "title": "Commercial Title",
    "brand": "Brand Name",
    "slug": "commercial-slug",
    "description": "Brief description",
    "thumbnail": "https://...",
    "videoUrl": "https://vimeo.com/...",
    "directorId": "1",
    "featured": true
  }
]
```

### Editing Workflow

1. **Open VS Code**
2. **Edit `src/data/directors.json` or `src/data/works.json`**
3. **Save file**
4. **Development server hot-reloads automatically** (if running `npm run dev`)
5. **Push to GitHub** when ready to deploy
6. **Netlify rebuilds and deploys** automatically

---

## 🎨 Design Direction

### Visual Aesthetic

- **High-Contrast Editorial** - Bold black on white, big typography
- **Minimal Color Palette** - Black, white, gray only
- **Bold Typography** - Uppercase headings, system fonts
- **Smooth Animations** - Fade-ins, hover scales, transitions
- **Editorial Grid** - Video cards, director cards on responsive grid

### Components

| Component | Details |
|-----------|---------|
| **Hero** | Animated text reveal, black bg, white text, CTA buttons |
| **Video Card** | Thumbnail, hover overlay with play button, brand/title info |
| **Director Card** | Headshot, name, bio snippet, "View" + "Reel" buttons |
| **Header** | Fixed top, minimal nav, JOJX logo, mobile menu toggle |
| **Footer** | Black bg, white text, links, social, copyright |
| **Form** | Clean, high-contrast, Netlify integrated |

### Colors

```css
--black: #000000
--white: #FFFFFF
--gray: #888888 (accents, secondary text)
```

---

## 🚀 Deployment to Netlify

### Prerequisites

- GitHub account with repository pushed
- Netlify account (free tier sufficient)

### Deploy Steps

1. **Go to [netlify.com](https://netlify.com)**
2. **Sign up/Log in with GitHub**
3. **Click "New site from Git"**
4. **Select repository:** `jzisjennzeller-code/jojx-astro`
5. **Build settings:**
   - Build command: `npm run build`
   - Publish directory: `dist`
6. **Deploy**

### Auto-Deployment

Every time you push to `main` branch, Netlify automatically:
1. Runs `npm run build`
2. Generates static files
3. Deploys to live site

### Custom Domain

1. **In Netlify:** Site settings → Domain management
2. **Add domain:** `jojx.co` (or subdomain)
3. **Update DNS** with your registrar
4. **Enable HTTPS** (automatic with Netlify)

---

## 📊 File Structure

```
jojx-astro/
├── src/
│   ├── components/
│   │   ├── Header.astro          (Navigation + Logo)
│   │   ├── Footer.astro          (Footer + Links)
│   │   ├── Hero.astro            (Landing hero)
│   │   ├── VideoGrid.tsx         (React video grid)
│   │   ├── DirectorCard.astro    (Reusable card)
│   │   └── WorkCard.astro        (Video card)
│   ├── data/
│   │   ├── directors.json        (Edit this!)
│   │   └── works.json            (Edit this!)
│   ├── layouts/
│   │   └── Layout.astro          (Base template)
│   ├── pages/
│   │   ├── index.astro           (/)
│   │   ├── work/
│   │   │   └── index.astro       (/work)
│   │   ├── contact.astro         (/contact)
│   │   └── directors/
│   │       ├── index.astro       (/directors)
│   │       └── [slug].astro      (/directors/[name])
│   └── styles/
│       └── global.css
├── astro.config.mjs
├── tailwind.config.cjs
├── tsconfig.json
├── package.json
└── README.md
```

---

## 🔧 Common Edits

### Add a New Director

**Edit `src/data/directors.json`:**

```json
{
  "id": "5",
  "name": "New Director",
  "slug": "new-director",
  "bio": "Brief bio here",
  "image": "https://example.com/image.jpg",
  "reel": "https://vimeo.com/...",
  "featured": true
}
```

Pages auto-generate:
- `/directors` (shows in grid)
- `/directors/new-director` (individual page)
- `/` (if featured)

### Add a New Work

**Edit `src/data/works.json`:**

```json
{
  "id": "7",
  "title": "New Commercial",
  "brand": "Brand",
  "slug": "new-commercial",
  "description": "Description",
  "thumbnail": "https://...",
  "videoUrl": "https://vimeo.com/...",
  "directorId": "1",
  "featured": true
}
```

Appears on:
- `/work` (all works)
- `/directors/[slug]` (if directorId matches)
- `/` (if featured)

### Update Site Title

**Edit `src/layouts/Layout.astro`:**
Change the `<title>` default tag and metadata.

### Change Colors

**Edit `tailwind.config.cjs`:**

```js
colors: {
  black: '#000000',
  white: '#FFFFFF',
  gray: '#888888',
}
```

---

## ✅ Quality Checklist

Before launching V1:

- [ ] All directors have headshots + bios
- [ ] All works have thumbnails + video URLs
- [ ] All videos link to Vimeo/hosting platform
- [ ] Contact form connected to Netlify
- [ ] Social links updated (Instagram, Vimeo)
- [ ] Custom domain configured
- [ ] Images optimized (< 200KB each)
- [ ] Mobile responsive tested
- [ ] Lighthouse audit run (aim for 90+)
- [ ] SEO meta tags reviewed
- [ ] All links tested (no 404s)

---

## 🚢 Launch Checklist

- [ ] GitHub repo ready
- [ ] Netlify site deployed
- [ ] Custom domain live
- [ ] DNS configured
- [ ] Analytics added (optional)
- [ ] Form submissions working
- [ ] Email notificationsset up (Netlify forms)

---

## 📈 Future Enhancements (V2+)

- Blog/News section
- Director testimonials/case studies
- Video search/filtering
- Analytics dashboard
- Email capture for awards
- Multiple language support
- Newsletter signup

---

## 💡 Pro Tips

1. **Use Vimeo for videos** - Better than YouTube for commercials
2. **Optimize images** - Use TinyPNG or similar
3. **Keep updates in GitHub** - Easy to rollback changes
4. **Monitor Netlify analytics** - See page traffic
5. **Test locally first** - Run `npm run dev` before pushing

---

## 📞 Support

- **Astro Docs**: https://docs.astro.build
- **Netlify Docs**: https://docs.netlify.com
- **Tailwind CSS**: https://tailwindcss.com
