# 🔧 TROUBLESHOOTING - Model Not Loading

## Quick Test

1. Upload `test-model.html` to your GitHub repository
2. Visit: `https://elleyale.github.io/portfolio/test-model.html`
3. Check the black status box - it will tell you exactly what's working

## Expected Output (When Working)

```
🔍 Model Loading Test
Repository: elleyale/portfolio
---
✓ Three.js scene initialized
Attempting: GitHub Raw
URL: https://raw.githubusercontent.com/elleyale/portfolio/main/model_root.glb
Loading: 25%
Loading: 50%
Loading: 75%
Loading: 100%
✓ SUCCESS loading from GitHub Raw
✓ Model positioned and scaled
```

## If GitHub Raw Fails

```
Attempting: GitHub Raw
URL: https://raw.githubusercontent.com/...
✗ Failed: [error message]
---
Attempting: Local
URL: model_root.glb
Loading: 100%
✓ SUCCESS loading from Local
✓ Model positioned and scaled
```

This means it's loading from the local file (which is fine!)

## Common Issues & Fixes

### Issue 1: CORS Error
**Error:** `CORS policy: No 'Access-Control-Allow-Origin'`

**Fix:**
This shouldn't happen with `raw.githubusercontent.com`, but if it does:
1. Make sure repository is **Public**
2. Check you're using the raw URL, not the regular GitHub URL
3. Clear browser cache

### Issue 2: 404 Not Found
**Error:** `Failed to load resource: the server responded with a status of 404`

**Checklist:**
- [ ] File is named exactly `model_root.glb` (case-sensitive)
- [ ] File is in repository root (not in a folder)
- [ ] Repository name is exactly `portfolio`
- [ ] Your GitHub username is exactly `elleyale`
- [ ] Branch is `main` (not `master`)

**Test manually:**
Visit: https://raw.githubusercontent.com/elleyale/portfolio/main/model_root.glb

Should download 4.89 MB file. If you get 404, the file isn't accessible.

### Issue 3: File Too Large
**Error:** `Request entity too large`

The model is 4.89 MB which should be fine. GitHub allows files up to 100 MB.

### Issue 4: Network Error
**Error:** `NetworkError` or `Failed to fetch`

**Possible causes:**
1. Browser blocking the request (check console)
2. Repository is Private (must be Public)
3. Network firewall blocking raw.githubusercontent.com

**Fix:**
Disable GitHub loading in `index.html`:
```javascript
const GITHUB_CONFIG = {
    enabled: false,  // ← Set to false
    // rest doesn't matter
};
```

This forces local loading only.

## Debugging Steps

### Step 1: Test Raw URL Manually
Visit in browser:
```
https://raw.githubusercontent.com/elleyale/portfolio/main/model_root.glb
```

✓ Downloads file → GitHub hosting works
✗ Error 404 → File not accessible

### Step 2: Check Console (F12)
Open your portfolio and press F12:

**Look for:**
```
Model loading configuration:
Primary: GitHub → https://raw.githubusercontent.com/...
Fallback: Local → model_root.glb
Attempting to load: [URL]
```

**Successful load:**
```
✓ Model loaded successfully
✓ Configuring glass material
```

**Failed load:**
```
✗ Primary load failed: [error]
Trying fallback: model_root.glb
```

### Step 3: Use Test Page
1. Upload `test-model.html`
2. Visit it on GitHub Pages
3. Read the status messages
4. It will try both URLs and tell you which works

## Solutions

### Solution A: Use Local Loading Only
Edit `index.html`:
```javascript
const GITHUB_CONFIG = {
    enabled: false,  // Disable GitHub
    // rest ignored
};
```

Upload to GitHub. Model will load from local file.

### Solution B: Force GitHub URL
If you're sure the file is there, you can test the exact URL:

```javascript
loader.load(
    'https://raw.githubusercontent.com/elleyale/portfolio/main/model_root.glb',
    onModelLoaded,
    onProgress,
    onError
);
```

### Solution C: Use GitHub LFS
If file size is an issue (it shouldn't be):
1. Install Git LFS: `git lfs install`
2. Track GLB files: `git lfs track "*.glb"`
3. Commit and push

## Quick Fixes Applied

In this package, I've already fixed:
- ✓ Removed Cloudflare email obfuscation script
- ✓ Fixed contact email to: mailto:ella@uttertosh.com
- ✓ Renamed "Archive" to "Works & Archive"
- ✓ Pre-configured GitHub settings for elleyale/portfolio
- ✓ Added test-model.html for debugging

## Still Not Working?

1. **Try test-model.html first** - it will tell you exactly what's wrong
2. **Check browser console** (F12) - errors are descriptive
3. **Test the raw URL manually** - verify file is accessible
4. **Set `enabled: false`** - use local loading as fallback

## Contact Link Fixed

The contact link now correctly points to:
```html
<a href="mailto:ella@uttertosh.com">
```

No more Cloudflare obfuscation!

## Files to Upload

Make sure these are in your repository:
- index.html (with fixes)
- archive.html (renamed to Works & Archive)
- model_root.glb (4.89 MB)
- test-model.html (for debugging)
- All other files

---

**If model loads in test-model.html but not in index.html:**
This means the test page works but something in index.html is interfering. Open both in browser and compare console outputs.
