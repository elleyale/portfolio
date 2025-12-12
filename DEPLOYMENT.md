# Deployment Guide

Complete step-by-step instructions for deploying your portfolio website.

## 🚀 Quick Deploy to GitHub Pages (5 minutes)

### Step 1: Upload to GitHub

1. **Create a new repository** on GitHub:
   - Go to https://github.com/new
   - Repository name: `portfolio` (or any name)
   - Description: "Personal portfolio website"
   - Public or Private (your choice)
   - ✅ Add a README file
   - Create repository

2. **Upload files**:
   - Click "Add file" → "Upload files"
   - Drag all files from this folder:
     - `index.html`
     - `lab-notebook-portfolio.html`
     - `model_root.glb`
     - `README.md`
     - `.gitignore`
   - Commit changes

### Step 2: Enable GitHub Pages

1. Go to **Settings** (top menu)
2. Scroll to **Pages** (left sidebar)
3. Under "Build and deployment":
   - Source: **Deploy from a branch**
   - Branch: **main** (or master)
   - Folder: **/ (root)**
4. Click **Save**

### Step 3: Access Your Site

- Wait 1-2 minutes for deployment
- Your site will be live at:
  ```
  https://YOUR-USERNAME.github.io/portfolio/
  ```
- Check the green deployment badge at the top of the Pages settings

### Custom Domain (Optional)

1. Buy a domain (Namecheap, Google Domains, etc.)
2. In GitHub Pages settings, add your custom domain
3. Update DNS records:
   ```
   Type: CNAME
   Name: www
   Value: YOUR-USERNAME.github.io
   ```
4. Enable HTTPS in GitHub Pages settings

---

## 🌐 Alternative Hosting Options

### Netlify (Easiest)

1. **Via GitHub**:
   - Go to https://app.netlify.com
   - "New site from Git"
   - Connect to GitHub
   - Select repository
   - Build settings: (leave empty for static site)
   - Deploy site

2. **Via Drag & Drop**:
   - Go to https://app.netlify.com/drop
   - Drag the entire folder
   - Instant deployment!

**Custom domain**: Settings → Domain management → Add custom domain

---

### Vercel

1. Go to https://vercel.com
2. "New Project"
3. Import from GitHub
4. Select repository
5. Deploy

**Custom domain**: Settings → Domains → Add domain

---

### Cloudflare Pages

1. Go to https://pages.cloudflare.com
2. "Create a project"
3. Connect to GitHub
4. Select repository
5. Build settings:
   - Build command: (leave empty)
   - Output directory: (leave empty)
6. Deploy

**Custom domain**: Automatically handles Cloudflare domains

---

### AWS S3 + CloudFront (Advanced)

1. **Create S3 Bucket**:
   - Name: `your-portfolio-bucket`
   - Enable "Static website hosting"
   - Upload all files

2. **Configure Bucket Policy**:
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Sid": "PublicReadGetObject",
       "Effect": "Allow",
       "Principal": "*",
       "Action": "s3:GetObject",
       "Resource": "arn:aws:s3:::your-portfolio-bucket/*"
     }]
   }
   ```

3. **Create CloudFront Distribution**:
   - Origin: Your S3 bucket
   - Viewer Protocol: Redirect HTTP to HTTPS
   - Default Root Object: `index.html`

4. **Access via CloudFront URL**:
   - `https://d111111abcdef8.cloudfront.net`

---

## 🔧 Testing Before Deployment

### Local Testing

**Option 1: Python**
```bash
python -m http.server 8000
# Visit http://localhost:8000
```

**Option 2: Node.js**
```bash
npx serve
# Visit http://localhost:3000
```

**Option 3: VS Code**
- Install "Live Server" extension
- Right-click `index.html` → "Open with Live Server"

### Check Before Going Live

- ✅ All links work (internal navigation)
- ✅ 3D model loads correctly
- ✅ News ticker is scrolling
- ✅ "Where am I?" typing effect works
- ✅ Modal opens and closes
- ✅ Responsive on mobile (Chrome DevTools)
- ✅ All images/assets load
- ✅ Contact links are correct

---

## 🎨 Post-Deployment Customization

### Update Personal Info

1. **Landing Page** (`index.html`):
   - Lines 463-467: Name, title, description
   - Lines 469-478: Navigation links
   - Line 473: Email address
   - Lines 524-533: Footer social links

2. **Research Page** (`lab-notebook-portfolio.html`):
   - Line 828: Header text
   - Lines 855-1075: Project entries
   - Lines 1078-1105: Research interests
   - Lines 1133-1165: Contact section

### Add Google Analytics (Optional)

Add before closing `</head>` tag:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### SEO Optimization

Add to `<head>` section:
```html
<!-- Meta Tags -->
<meta name="description" content="Your portfolio description">
<meta name="keywords" content="creative technologist, 3D, immersive media">
<meta name="author" content="Your Name">

<!-- Open Graph (Social Media) -->
<meta property="og:title" content="Your Name - Portfolio">
<meta property="og:description" content="Your description">
<meta property="og:image" content="https://yoursite.com/preview.jpg">
<meta property="og:url" content="https://yoursite.com">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Your Name - Portfolio">
<meta name="twitter:description" content="Your description">
<meta name="twitter:image" content="https://yoursite.com/preview.jpg">
```

---

## 🐛 Troubleshooting

### Model Not Loading
- Check browser console (F12)
- Ensure `model_root.glb` is in the same directory as `index.html`
- File must be exactly `model_root.glb` (case-sensitive on some hosts)

### Page Not Loading on GitHub Pages
- Wait 2-5 minutes after enabling
- Check repository is Public (or have GitHub Pro for private)
- Ensure `index.html` is in root directory

### News Ticker Not Moving
- Check browser console for errors
- Ensure JavaScript is enabled
- Try hard refresh (Ctrl+Shift+R / Cmd+Shift+R)

### Mobile Display Issues
- Test in Chrome DevTools responsive mode
- Check viewport meta tag is present
- Ensure all CSS media queries are working

---

## 📊 Performance Optimization

### Optimize 3D Model (Optional)
```bash
# Install gltf-pipeline
npm install -g gltf-pipeline

# Compress model
gltf-pipeline -i model_root.glb -o model_root_compressed.glb -d
```

### Enable Caching
Add `.htaccess` (Apache) or configure headers:
```apache
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresByType model/gltf-binary "access plus 1 month"
  ExpiresByType text/html "access plus 1 hour"
</IfModule>
```

---

## 🔄 Updating Your Site

### Method 1: Direct GitHub Edit
1. Navigate to file on GitHub
2. Click pencil icon (Edit)
3. Make changes
4. Commit changes
5. Wait 1-2 minutes for redeployment

### Method 2: Git Command Line
```bash
# Clone repository
git clone https://github.com/YOUR-USERNAME/portfolio.git
cd portfolio

# Make changes to files

# Commit and push
git add .
git commit -m "Update portfolio content"
git push origin main
```

---

## 💡 Tips

- **Backup**: Keep original files in a separate folder
- **Version Control**: Use meaningful commit messages
- **Testing**: Always test locally before pushing
- **Mobile First**: Test on actual mobile devices
- **Accessibility**: Check color contrast and keyboard navigation
- **Performance**: Monitor load times with Lighthouse

---

## 📞 Need Help?

- GitHub Pages Docs: https://pages.github.com/
- Three.js Docs: https://threejs.org/docs/
- MDN Web Docs: https://developer.mozilla.org/

**Contact**: ella@uttertosh.com
