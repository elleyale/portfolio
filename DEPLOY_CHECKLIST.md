# 🚀 DEPLOYMENT CHECKLIST

## Pre-Deployment (Do This FIRST)

### 1. Extract the ZIP
- [ ] Extract `portfolio.zip` to a folder
- [ ] Verify all 8 files are present:
  - `index.html` (30KB)
  - `archive.html` (12KB)
  - `photogrammetry_blog1.html` (47KB)
  - `model_root.glb` (4.7MB) ⚠️ **CRITICAL**
  - `Ella_Musaieva_resume.pdf` (598KB)
  - `README.md`
  - `MODEL_SETUP.md`
  - `.gitignore`

### 2. Edit index.html BEFORE Uploading

**IMPORTANT:** Configure GitHub model loading first!

1. Open `index.html` in text editor
2. Find line ~835 (search for `GITHUB_CONFIG`)
3. Update these values:

```javascript
const GITHUB_CONFIG = {
    enabled: true,
    username: 'YOUR-GITHUB-USERNAME',  // ← CHANGE THIS
    repo: 'YOUR-REPO-NAME',            // ← CHANGE THIS
    branch: 'main',                    // Keep as 'main'
    modelPath: 'model_root.glb'        // Keep this
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

4. Save `index.html`

---

## GitHub Setup

### 3. Create Repository
- [ ] Go to https://github.com/new
- [ ] Name: `portfolio` (must match config above)
- [ ] Visibility: **Public** (required)
- [ ] Click "Create repository"

### 4. Upload Files
- [ ] Click "uploading an existing file"
- [ ] Drag ALL 8 files (including `.gitignore`)
- [ ] Verify `model_root.glb` is in the list (4.7MB)
- [ ] Commit: "Initial portfolio"

### 5. Verify Model File
- [ ] In repository, click `model_root.glb`
- [ ] File should show "4.89 MB"
- [ ] Click "Raw" button
- [ ] URL should be: `https://raw.githubusercontent.com/username/repo/main/model_root.glb`
- [ ] Browser should download the file

### 6. Enable GitHub Pages
- [ ] Settings → Pages
- [ ] Source: **Deploy from a branch**
- [ ] Branch: **main**
- [ ] Folder: **/ (root)**
- [ ] Click **Save**
- [ ] Note the URL shown (https://username.github.io/repo/)

---

## Testing (Wait 3 Minutes After Enabling Pages)

### 7. Test Your Site
- [ ] Visit: `https://YOUR-USERNAME.github.io/YOUR-REPO/`
- [ ] Press **F12** to open console

### 8. Check Console Output

You should see:
```
🤖 AI News Agent running - updates every 10 minutes
Model loading configuration:
Primary: GitHub → https://raw.githubusercontent.com/...
Fallback: Local → model_root.glb
Attempting to load: https://raw.githubusercontent.com/...
Three.js initialized
✓ Fetched 8 fresh tech news
Loading: 100%
✓ Model loaded successfully
✓ Configuring glass material
✓ Configuring pod material
✓ Model positioned and scaled
```

✓ **If you see this = SUCCESS!**

---

## Troubleshooting

### Model Not Loading

**Console shows:**
```
✗ Primary load failed
Trying fallback: model_root.glb
✗ Model loading failed
```

**Fix:**
1. Check `model_root.glb` is uploaded
2. Verify GitHub config matches your username/repo
3. Test raw URL manually
4. Check repository is Public

**Quick Fix:** Disable GitHub loading:
```javascript
const GITHUB_CONFIG = {
    enabled: false,  // ← Set to false
    // ...
};
```

### News Ticker Shows "Initializing..."

- Wait 10 seconds
- Hard refresh: Ctrl+Shift+R
- Check console for errors

### Page Shows 404

- Wait 5 minutes (Pages takes time)
- Check Pages is enabled
- Verify files in root (not subfolder)

---

## Post-Deployment

### 9. Final Checks
- [ ] 3D model loads and rotates
- [ ] News ticker shows tech headlines
- [ ] "Where am I?" types out
- [ ] All 4 sidebar tabs work
- [ ] Modal opens and closes
- [ ] Footer social links work
- [ ] Mobile responsive (test on phone)

### 10. Optional Customizations
- [ ] Add personal avatar (300×300px image)
- [ ] Update Archive page with projects
- [ ] Add more research posts
- [ ] Customize news sources

---

## Console Debug Commands

Open browser console (F12) and run:

```javascript
// Check if model is loaded
console.log('Model loaded:', model !== null);

// Check news ticker
console.log('News count:', currentNews.length);

// Force news update
fetchNews();

// Check GitHub config
console.log(GITHUB_CONFIG);
```

---

## Emergency Fallback

If nothing works:

1. Use local-only mode:
   ```javascript
   enabled: false
   ```

2. Or download and test locally:
   ```bash
   python -m http.server 8000
   # Visit http://localhost:8000
   ```

3. Check README.md for detailed troubleshooting

---

## Success Criteria ✓

Your portfolio is live when:
- [ ] Site loads at GitHub Pages URL
- [ ] Console shows no errors
- [ ] 3D model visible and rotating
- [ ] News ticker scrolling with tech headlines
- [ ] All navigation working
- [ ] Mobile responsive

**All checked? Congratulations! 🎉**

Your portfolio is live and ready to share!

Share URL: `https://YOUR-USERNAME.github.io/YOUR-REPO/`
