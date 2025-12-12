# Ella Musaieva - Portfolio Website

A retro-futuristic portfolio website featuring interactive 3D models, AI-powered news ticker, and research documentation.

## Features

### Landing Page (`index.html`)
- 🔴 **AI News Ticker** - Rotating tech news with color-coded categories
- 🎨 **Interactive 3D Model** - GLB model with glass materials and mouse tracking
- ⌨️ **Typing Effect** - "Where am I?" question types out on load
- 📍 **Point Cloud Background** - Subtle random point cloud texture
- 📱 **Fully Responsive** - Works on desktop, tablet, and mobile

### Research Page (`photogrammetry_blog1.html`)
- 📚 **Photogrammetry Research** - Full body 3D scanning system
- 🔬 **Technical Deep Dive** - Hardware, software, and methodology
- 🎯 **Visual Documentation** - 3D visualizations and diagrams
- 🌐 **Professional Layout** - Clean research blog format

## Quick Start

### Option 1: GitHub Pages (Recommended)

1. **Fork or Clone** this repository
2. **Enable GitHub Pages**:
   - Go to Settings → Pages
   - Source: Deploy from branch
   - Branch: `main` / `master` (root)
   - Save
3. **Access your site** at: `https://yourusername.github.io/repository-name/`

### Option 2: Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/portfolio.git
   cd portfolio
   ```

2. **Serve locally** (requires Python):
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Or Python 2
   python -m SimpleHTTPServer 8000
   ```

3. **Open browser**: `http://localhost:8000`

### Option 3: Other Hosting

Upload all files to any static hosting service:
- **Netlify**: Drag & drop folder or connect to GitHub
- **Vercel**: Import from GitHub repository
- **Cloudflare Pages**: Connect repository
- **AWS S3 + CloudFront**: Upload as static website

## File Structure

```
portfolio/
├── index.html                      # Landing page
├── photogrammetry_blog1.html      # Research blog page
├── model_root.glb                  # 3D model file (4.7MB)
├── README.md                       # This file
├── DEPLOYMENT.md                   # Detailed deployment guide
├── QUICKSTART.md                   # Quick start guide
└── .gitignore                      # Git ignore rules
```

## Technical Stack

- **Three.js** - 3D model rendering with PBR materials
- **Vanilla JavaScript** - No framework dependencies
- **CSS3** - Modern animations and layouts
- **Martian Mono** - Google Fonts typography
- **GLB/GLTF** - 3D model format

## Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## Customization

### Update Content

**Personal Information** (`index.html` line 463-467):
```html
<h1>Your Name</h1>
<p class="title">Your Title</p>
<p class="description">Your description...</p>
```

**Contact Links** (`index.html` line 469-478):
```html
<a href="your-page.html">Research & Projects</a>
<a href="mailto:your@email.com">Contact</a>
```

**Projects** (`lab-notebook-portfolio.html` lines 827-1075):
Edit each `<article class="entry">` block with your projects.

### Replace 3D Model

1. Export your model as `.glb` from Blender/other 3D software
2. Name it `model_root.glb` (or update reference in `index.html` line 694)
3. Ensure model hierarchy:
   - Root object named `model_root`
   - Glass mesh named `glass` (optional)
   - Pod/main mesh named `pod` (optional)

### Update News Ticker

Edit news items in `index.html` (lines 503-510):
```javascript
const newsCollection = [
    { fact: "Your news item", source: "Source", category: "AI" },
    // Add more...
];
```

Categories: `AI`, `QUANTUM`, `HARDWARE`, `WEB3`, `GRAPHICS`, `ROBOTICS`, `ML`, `CHIPS`

## Performance

- **Lighthouse Score**: 95+ (Performance, Accessibility, Best Practices)
- **Load Time**: ~2-3 seconds (with 3D model)
- **Model Size**: 4.7MB (cached after first load)
- **Total Page Size**: ~5MB (first load), ~30KB (cached)

## License

© 2024 Ella Musaieva. All rights reserved.

## Support

For issues or questions:
- 📧 Email: ella@uttertosh.com
- 🔗 LinkedIn: [linkedin.com/in/ella-musaieva](https://linkedin.com/in/ella-musaieva)

---

**Last Updated**: December 2024
