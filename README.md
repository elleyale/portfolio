# Ella Musaieva - Portfolio

Creative Technologist portfolio with interactive 3D models, AI news ticker, and research documentation.

## 🚀 Quick Start - GitHub Pages Deployment

### Step 1: Create Repository

1. Go to https://github.com/new
2. Repository name: `portfolio` (or your choice)
3. **Public** repository (required for GitHub Pages)
4. Click "Create repository"

### Step 2: Upload Files

Upload ALL files from this package:
- `index.html`
- `archive.html`
- `photogrammetry_blog1.html`
- `model_root.glb` ⚠️ **IMPORTANT: Must be uploaded!**
- `Ella_Musaieva_resume.pdf`
- `README.md`
- `.gitignore`

**Via Web Interface:**
1. Click "uploading an existing file"
2. Drag all 7 files
3. Commit changes

**Via Git CLI:**
```bash
git clone https://github.com/YOUR-USERNAME/portfolio.git
cd portfolio
# Copy all files here
git add .
git commit -m "Initial portfolio"
git push origin main
```

### Step 3: Configure 3D Model Loading

Edit `index.html` and find this section (around line 835):

```javascript
const GITHUB_CONFIG = {
    enabled: true,
    username: 'YOUR-GITHUB-USERNAME',  // ← UPDATE THIS
    repo: 'YOUR-REPO-NAME',            // ← UPDATE THIS
    branch: 'main',
    modelPath: 'model_root.glb'
};
```

**Example:**
```javascript
const GITHUB_CONFIG = {
    enabled: true,
    username: 'ellamusaieva',
    repo: 'portfolio',
    branch: 'main',
    modelPath: 'model_root.glb'
};
```

**Save and commit:**
```bash
git add index.html
git commit -m "Configure model loading"
git push origin main
```

### Step 4: Enable GitHub Pages

1. Go to **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / Folder: **/ (root)**
4. Click **Save**

### Step 5: Access Your Site

Wait 2-3 minutes, then visit:
```
https://YOUR-USERNAME.github.io/portfolio/
```

---

## 🔧 How 3D Model Loading Works

The portfolio uses a **smart fallback system**:

1. **Primary:** Tries to load from GitHub (if configured)
   - URL: `https://raw.githubusercontent.com/username/repo/main/model_root.glb`
   
2. **Fallback:** If GitHub fails, tries local file
   - URL: `model_root.glb` (same directory)

### Console Output (Press F12)

**Success:**
```
Model loading configuration:
Primary: GitHub → https://raw.githubusercontent.com/.../model_root.glb
Fallback: Local → model_root.glb
Attempting to load: [GitHub URL]
Loading: 100%
✓ Model loaded successfully
✓ Configuring glass material
✓ Configuring pod material
✓ Model positioned and scaled
```

**Fallback to Local:**
```
Primary load failed: [error]
Trying fallback: model_root.glb
✓ Model loaded successfully
```

---

## 🎨 Features

### Landing Page
- **AI News Ticker** - Auto-updates every 10 minutes from TechCrunch
- **Interactive 3D Model** - Glass materials with dispersion effects
- **Personal Avatar** - 300×300px placeholder (below name)
- **Thin Sidebar Navigation** - 60px wide, minimal design
- **Modal** - "Where am I?" with typing effect

### Archive Page
- 6 media categories with placeholders:
  - Showreels
  - Artwork
  - Experiments
  - Documentation
  - Talks & Presentations
  - Collaborations

### Research Page
- Full photogrammetry blog post
- Technical documentation

---

## 📁 File Structure

```
portfolio/
├── index.html                    # Landing page (main entry)
├── archive.html                  # Media library
├── photogrammetry_blog1.html    # Research blog
├── model_root.glb               # 3D model (4.7MB) ⚠️ REQUIRED
├── Ella_Musaieva_resume.pdf     # CV/Resume
├── README.md                     # This file
└── .gitignore                    # Git ignore rules
```

---

## 🐛 Troubleshooting

### Model Not Loading

**Check Console (F12):**
```
✗ Model loading failed: [error message]
```

**Solutions:**

1. **Verify file exists:**
   - Check `model_root.glb` is in repository root
   - File name is exact: `model_root.glb` (case-sensitive)

2. **Check GitHub config:**
   ```javascript
   username: 'ellamusaieva',  // Must match your GitHub username
   repo: 'portfolio',          // Must match repository name
   branch: 'main',             // Check if it's 'main' or 'master'
   ```

3. **Verify GitHub URL manually:**
   - Visit: `https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/model_root.glb`
   - Should download the file (4.7MB)

4. **Disable GitHub loading (use local only):**
   ```javascript
   const GITHUB_CONFIG = {
       enabled: false,  // ← Set to false
       // ... rest doesn't matter
   };
   ```

### News Ticker Not Updating

**Check Console:**
```
🤖 AI News Agent running - updates every 10 minutes
✓ Fetched 8 fresh tech news
```

If you see "Using fallback news", the RSS API might be rate-limited. This is normal - it will show curated static news instead.

### Page Not Loading on GitHub Pages

1. Wait 5 minutes after enabling Pages
2. Check repository is **Public**
3. Ensure files are in root (not in subfolder)
4. Hard refresh: `Ctrl + Shift + R` (Windows) or `Cmd + Shift + R` (Mac)

---

## 🎯 Customization

### Update Personal Avatar

Replace the avatar placeholder in `index.html`:

```html
<div class="avatar-area">
    <!-- Option 1: Image -->
    <img src="avatar.jpg" alt="Ella Musaieva" 
         style="width: 100%; height: 100%; object-fit: cover;">
    
    <!-- Option 2: Your own 3D model -->
    <canvas id="avatarCanvas"></canvas>
</div>
```

### Change News Sources

Edit the `fetchNews()` function to use different RSS feeds:

```javascript
const response = await fetch(
    'https://api.rss2json.com/v1/api.json?rss_url=YOUR_RSS_FEED_URL'
);
```

Popular tech RSS feeds:
- TechCrunch: `https://techcrunch.com/feed/`
- The Verge: `https://www.theverge.com/rss/index.xml`
- Ars Technica: `https://arstechnica.com/feed/`
- Wired: `https://www.wired.com/feed/rss`

### Add Projects to Archive

Edit `archive.html` and uncomment the grid section:

```html
<div class="archive-grid">
    <a href="project1.html" class="archive-item">
        <div class="date">2024</div>
        <h3>Project Title</h3>
        <p>Description...</p>
        <div class="category">Category</div>
    </a>
    <!-- Add more -->
</div>
```

---

## 💻 Local Development

### Option 1: Python
```bash
python -m http.server 8000
# Visit http://localhost:8000
```

### Option 2: Node.js
```bash
npx serve
# Visit http://localhost:3000
```

### Option 3: VS Code
- Install "Live Server" extension
- Right-click `index.html`
- "Open with Live Server"

---

## 🌐 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

---

## 📞 Contact

- Email: ella@uttertosh.com
- Phone: 347-755-9236
- LinkedIn: [linkedin.com/in/ella-musaieva](https://linkedin.com/in/ella-musaieva)
- Twitter: [@uttertosh](https://twitter.com/uttertosh)

---

## 📄 License

© 2024 Ella Musaieva. All rights reserved.

---

## 🎯 Key Reminders

1. ✅ **Upload `model_root.glb`** to GitHub repository
2. ✅ **Update GitHub config** in `index.html`
3. ✅ **Enable GitHub Pages** in repository settings
4. ✅ **Repository must be Public** for Pages to work
5. ✅ **Check browser console** (F12) for debugging

**Your portfolio will be live in 5 minutes!** 🚀
