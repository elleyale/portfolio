# 🌌 Gaussian Splat Setup Guide

## Current Status

Your portfolio now has a **Gaussian Splat viewer** on the landing page!

**Location:** Below the avatar section
**Theme:** Space / Cosmic
**Status:** Placeholder active (waiting for your space.ply file)

---

## What You See Now

A beautiful space-themed placeholder with:
- Cosmic gradient background
- Animated stars
- Nebula effects
- "SPACE GAUSSIAN SPLAT" text

**Controls:**
- Drag to rotate (simulated)
- Scroll to zoom (simulated)
- Reset View button
- Auto Rotate toggle

---

## How to Add Your Real Space Splat

### Step 1: Prepare Your Splat File

**Supported formats:**
- `.ply` (Point Cloud with Gaussian data) - **Recommended**
- `.splat` (Compressed Gaussian Splat)

**File naming:**
- Name it: `space.ply` or `space.splat`
- Size: Keep under 50MB for web (compress if needed)

**Where to get space splats:**
1. Your own captures (if you have scanning equipment)
2. Download from: https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/
3. Or use Luma AI to create one: https://lumalabs.ai/

### Step 2: Upload to GitHub

Upload `space.ply` to your repository root:
```
elleyale/portfolio/
├── index.html
├── space.ply        ← Add this file
├── model_root.glb
└── ...
```

### Step 3: Update Configuration

Edit `index.html`, find the `SPLAT_CONFIG` section (around line 590):

**Option A: Local file (if uploaded to repo)**
```javascript
const SPLAT_CONFIG = {
    enabled: true,
    source: 'space.ply',  // Your file name
    githubUrl: null,
    autoRotate: false,
    rotateSpeed: 0.2
};
```

**Option B: GitHub raw URL**
```javascript
const SPLAT_CONFIG = {
    enabled: true,
    source: 'space.ply',
    githubUrl: 'https://raw.githubusercontent.com/elleyale/portfolio/main/space.ply',
    autoRotate: true,  // Enable auto-rotate
    rotateSpeed: 0.2
};
```

### Step 4: Upgrade to Full Renderer

The current implementation is a placeholder. To render actual Gaussian Splats, you have two options:

#### Option A: Use antimatter15/splat (Simple & Fast)

Add before the closing `</body>` tag:
```html
<script src="https://cdn.jsdelivr.net/npm/gsplat3d@latest/dist/gsplat.min.js"></script>
<script>
    const viewer = new GSplat.Viewer({
        canvas: document.getElementById('splatCanvas'),
        cameraPosition: [0, 0, 5]
    });
    
    viewer.loadFromUrl('space.ply').then(() => {
        document.getElementById('splatLoading').style.display = 'none';
        console.log('✓ Space splat loaded');
    });
</script>
```

#### Option B: Use PlayCanvas SuperSplat (Professional)

1. Visit: https://playcanvas.com/supersplat
2. Upload your `space.ply`
3. Get embed code
4. Replace the viewer section

---

## Recommended Space Splats

### Free Downloads:

1. **NASA Space Station (Interior)**
   - Search: "ISS Gaussian Splat"
   - Size: ~30MB
   
2. **Space Nebula (Abstract)**
   - Create with AI tools
   - Or download from Sketchfab

3. **Custom Space Scene**
   - Use Luma AI to capture
   - Or create synthetic space scene

### Best File Size for Web:

- **Good:** 10-30 MB (fast loading)
- **Acceptable:** 30-50 MB (moderate)
- **Large:** 50-100 MB (slow, consider compression)

---

## Current Placeholder Features

While you prepare your splat file, the placeholder includes:

✅ **Visual:**
- Cosmic gradient background
- Animated starfield (200 stars)
- Purple and blue nebula effects
- Professional typography

✅ **Interactive:**
- Mouse drag tracking
- Zoom controls
- Reset view button
- Auto-rotate toggle

✅ **Responsive:**
- Desktop: 600px height
- Tablet: 400px height
- Mobile: 300px height

---

## File Organization

```
portfolio/
├── index.html           # Main page with splat viewer
├── space.ply           # Your Gaussian Splat file (add this)
├── model_root.glb      # 3D pod model (already there)
├── avatar.jpg          # Your avatar (optional)
└── ...
```

---

## Testing

### Step 1: Check Console
Open browser console (F12) and look for:
```
🌌 Gaussian Splat viewer initialized
📁 To add your space splat:
   1. Upload space.ply to GitHub repository
   2. Update SPLAT_CONFIG.source or SPLAT_CONFIG.githubUrl
   3. Replace SimpleSplatViewer with full splat renderer
```

### Step 2: Verify Placeholder
- Should see cosmic background
- Stars should be visible
- Text should read "SPACE GAUSSIAN SPLAT"

### Step 3: Test Controls
- Drag should work (even in placeholder)
- Scroll zoom should work
- Buttons should toggle

---

## Upgrading to Real Splat Renderer

Once you have `space.ply`:

### Quick Integration (antimatter15/splat)

1. **Add library:**
```html
<script src="https://cdn.jsdelivr.net/npm/gsplat3d@latest/dist/gsplat.min.js"></script>
```

2. **Replace SimpleSplatViewer:**
```javascript
const viewer = new GSplat.Viewer({
    canvas: document.getElementById('splatCanvas'),
    cameraPosition: [0, 0, 5],
    cameraTarget: [0, 0, 0],
    up: [0, 1, 0]
});

// Load from GitHub
const url = 'https://raw.githubusercontent.com/elleyale/portfolio/main/space.ply';
viewer.loadFromUrl(url).then(() => {
    console.log('✓ Space splat loaded successfully');
    document.getElementById('splatLoading').style.display = 'none';
    document.getElementById('splatControls').style.display = 'flex';
    
    // Auto-rotate
    function animate() {
        if (autoRotate) {
            viewer.camera.rotateY(0.002);
        }
        requestAnimationFrame(animate);
    }
    animate();
});
```

---

## Performance Tips

1. **Compress large splats:**
   - Use: https://antimatter15.com/splat/ to compress
   - Target: 20-30 MB for web

2. **Lazy load:**
   - Only load when user scrolls to section
   - Or load on user click

3. **Show preview:**
   - Keep placeholder until splat loads
   - Add progress bar

---

## Alternative: Use Video Instead

If Gaussian Splat is too large, you can use a video of the splat:

```html
<video autoplay loop muted playsinline>
    <source src="space-splat.mp4" type="video/mp4">
</video>
```

Benefits:
- ✅ Smaller file size
- ✅ Guaranteed compatibility
- ✅ No rendering overhead

---

## Next Steps

1. **Find or create** your space Gaussian Splat file
2. **Upload** `space.ply` to GitHub repository
3. **Update** SPLAT_CONFIG in index.html
4. **Choose** renderer library (gsplat3d or SuperSplat)
5. **Test** and optimize

**For now, the beautiful placeholder is live and looks great!** 🌌✨

Want me to help integrate a specific splat file? Just provide the URL or file!
