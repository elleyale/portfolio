# 🚀 QUICK START - 5 Minutes to Live Website

## What You Have

✅ `portfolio-website.zip` - Complete deployment package (5.1MB)

Contains:
- `index.html` - Landing page with 3D model
- `lab-notebook-portfolio.html` - Research/projects page
- `model_root.glb` - 3D model file (4.7MB)
- `README.md` - Documentation
- `DEPLOYMENT.md` - Detailed deployment guide
- `.gitignore` - Git ignore rules

---

## Option 1: GitHub Pages (Recommended)

### Step 1: Unzip the Package
Extract `portfolio-website.zip` to a folder on your computer.

### Step 2: Create GitHub Repository
1. Go to https://github.com/new
2. Repository name: `portfolio` (or your choice)
3. Select "Public"
4. Click "Create repository"

### Step 3: Upload Files
1. Click "uploading an existing file"
2. Drag ALL files from the extracted folder
3. Click "Commit changes"

### Step 4: Enable GitHub Pages
1. Go to **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main**, Folder: **/ (root)**
4. Click **Save**

### Step 5: Visit Your Site!
Wait 2 minutes, then visit:
```
https://YOUR-USERNAME.github.io/portfolio/
```

**Done! Your site is live!** 🎉

---

## Option 2: Netlify (Drag & Drop)

### Instant Deployment (30 seconds)

1. Go to https://app.netlify.com/drop
2. Drag the entire extracted folder
3. Done! Your site is live instantly
4. Free custom subdomain: `random-name-123.netlify.app`

**Want a custom domain?**
- Settings → Domain management → Add domain

---

## Option 3: Local Testing First

### Test on Your Computer

**Mac/Linux:**
```bash
cd path/to/extracted/folder
python3 -m http.server 8000
```

**Windows:**
```bash
cd path\to\extracted\folder
python -m http.server 8000
```

Then visit: `http://localhost:8000`

---

## ✅ Checklist - Make It Yours

### Immediate Updates

**1. Landing Page (`index.html`)**
- [ ] Line 463: Change "Ella Musaieva" to your name
- [ ] Line 464: Change "Creative Technologist" to your title
- [ ] Line 465-467: Update description
- [ ] Line 473: Update email address
- [ ] Line 476: Update CV link

**2. Research Page (`lab-notebook-portfolio.html`)**
- [ ] Line 828: Update header
- [ ] Lines 855-1075: Add your projects
- [ ] Line 1157: Update phone number
- [ ] Line 1158: Update email
- [ ] Lines 1163-1183: Update social links

### Optional Enhancements

**Replace 3D Model:**
1. Export your model as `model_root.glb`
2. Replace the existing file
3. Model should have:
   - Root object named `model_root`
   - Glass parts named `glass` (optional)
   - Main mesh named `pod` (optional)

**Update News Ticker:**
Edit `index.html` lines 503-510:
```javascript
const newsCollection = [
    { fact: "Your news", source: "Source", category: "AI" },
    // Add more items...
];
```

**Add Your Projects:**
Copy/paste this structure in `lab-notebook-portfolio.html`:
```html
<article class="entry">
    <div class="entry-header">
        <div class="entry-date">2024</div>
        <h2 class="entry-title">Project Title</h2>
        <p class="entry-subtitle">Project Type</p>
    </div>
    
    <div class="entry-section">
        <h3 class="entry-section-title">Research Question</h3>
        <p class="entry-section-content">Your question...</p>
    </div>
    
    <!-- Add more sections -->
</article>
```

---

## 📁 File Structure

```
portfolio/
├── index.html                 ← Landing page (main entry)
├── lab-notebook-portfolio.html ← Projects/research page
├── model_root.glb             ← 3D model (keep same name!)
├── README.md                  ← Full documentation
├── DEPLOYMENT.md              ← Detailed deployment guide
└── .gitignore                 ← Git ignore rules
```

**Important:**
- Keep `model_root.glb` in the SAME folder as `index.html`
- Don't rename files unless you update references
- Both HTML files should be in root directory

---

## 🐛 Common Issues

### "Model not loading"
✅ Make sure `model_root.glb` is in same folder as `index.html`
✅ File name must be exactly `model_root.glb` (lowercase)
✅ Check browser console (F12) for errors

### "Page not showing on GitHub Pages"
✅ Wait 2-5 minutes after enabling
✅ Check repository is Public
✅ Ensure files are in root (not in subfolder)
✅ Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)

### "News ticker not moving"
✅ Hard refresh the page
✅ Check JavaScript is enabled in browser
✅ Open browser console (F12) - any errors?

---

## 🎯 Next Steps

After deployment:

1. **Test Everything:**
   - ✅ Click all navigation links
   - ✅ Test on mobile device
   - ✅ Check 3D model rotates
   - ✅ Verify contact links work

2. **Share Your Site:**
   - Add to LinkedIn profile
   - Share on social media
   - Include in email signature
   - Add to resume/CV

3. **Track Performance:**
   - Run Lighthouse audit (Chrome DevTools)
   - Monitor with Google Analytics (optional)
   - Check mobile responsiveness

4. **Keep Updated:**
   - Add new projects regularly
   - Update news ticker items
   - Refresh contact information
   - Backup files regularly

---

## 💡 Pro Tips

- **Custom Domain**: Buy from Namecheap (~$10/year) and connect to GitHub Pages
- **SEO**: Add meta tags for better Google indexing (see DEPLOYMENT.md)
- **Analytics**: Add Google Analytics to track visitors
- **SSL**: GitHub Pages provides free HTTPS automatically
- **CDN**: Already handled by GitHub/Netlify - your site loads fast globally

---

## 📞 Need Help?

**Full Documentation:**
- `README.md` - Complete overview
- `DEPLOYMENT.md` - Detailed deployment instructions

**Online Resources:**
- GitHub Pages: https://pages.github.com
- Netlify Docs: https://docs.netlify.com
- Three.js Docs: https://threejs.org/docs

**Contact:**
For questions about your deployment, consult the documentation files or GitHub/hosting provider support.

---

**Your portfolio is ready to go live! 🚀**

Choose your hosting method above and you'll be online in minutes.
