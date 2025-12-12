# 3D Model Setup Guide

## Quick Setup (3 Steps)

### 1. Upload model_root.glb to GitHub

Make sure `model_root.glb` is in your repository root:
```
your-repo/
├── index.html
├── model_root.glb  ← Must be here!
├── archive.html
└── ...
```

### 2. Edit index.html

Find line ~835 and update:

```javascript
const GITHUB_CONFIG = {
    enabled: true,
    username: 'YOUR-GITHUB-USERNAME',  // ← Replace with your GitHub username
    repo: 'YOUR-REPO-NAME',            // ← Replace with your repo name
    branch: 'main',                    // Keep as 'main' (or 'master' if needed)
    modelPath: 'model_root.glb'        // Keep as is
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

### 3. Test the URL

Visit this URL in your browser (replace with your details):
```
https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/model_root.glb
```

**Example:**
```
https://raw.githubusercontent.com/ellamusaieva/portfolio/main/model_root.glb
```

If it downloads a 4.7MB file → ✓ Success!

## Console Debugging

Open your deployed site and press **F12** to see:

### ✓ Working:
```
Model loading configuration:
Primary: GitHub → https://raw.githubusercontent.com/ellamusaieva/portfolio/main/model_root.glb
Fallback: Local → model_root.glb
Attempting to load: https://raw.githubusercontent.com/...
Loading: 25%
Loading: 50%
Loading: 75%
Loading: 100%
✓ Model loaded successfully
✓ Configuring glass material
✓ Configuring pod material  
✓ Model positioned and scaled
```

### ✗ Not Working:
```
Primary load failed: NetworkError
Trying fallback: model_root.glb
✗ Model loading failed: [error]
```

**If you see this:**
1. Check GitHub URL manually
2. Verify file uploaded
3. Check config matches your repo

## Disable GitHub (Use Local Only)

If GitHub hosting isn't working, disable it:

```javascript
const GITHUB_CONFIG = {
    enabled: false,  // ← Change to false
    // Rest doesn't matter
};
```

This will only load from local `model_root.glb` file.

## Model File Requirements

- **Name:** Exactly `model_root.glb` (case-sensitive)
- **Size:** ~4.7MB
- **Location:** Repository root
- **Format:** GLB/GLTF binary
- **Hierarchy:** 
  - Root: `model_root` (optional)
  - Glass mesh: `glass` (optional)
  - Pod mesh: `pod` (optional)

## Common Issues

### Issue: "Model not found"
**Solution:** Check file is uploaded and named correctly

### Issue: "CORS error"
**Solution:** Use GitHub raw URL, not regular GitHub file URL

### Issue: "Failed to fetch"
**Solution:** Repository must be Public (for raw.githubusercontent.com access)

### Issue: Model loads but looks wrong
**Solution:** Check model hierarchy - objects named `glass` and `pod` get special materials

## Testing Locally

Before deploying, test with local file:

```bash
# Serve locally
python -m http.server 8000

# Open browser
http://localhost:8000

# Check console - should load from local file
```

## Final Checklist

- [ ] `model_root.glb` uploaded to repository root
- [ ] GitHub username updated in `index.html`
- [ ] Repository name updated in `index.html`
- [ ] Branch name is correct ('main' or 'master')
- [ ] Repository is Public
- [ ] GitHub Pages is enabled
- [ ] Tested raw.githubusercontent.com URL manually
- [ ] Console shows successful load (F12)

**Once all checked → Model will load! 🎯**
