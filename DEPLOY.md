# 🚀 Deploy to GitHub - Quick Guide

## ✅ Project Structure is Ready!

Your files are now in the root directory, ready for GitHub Pages.

```
root/
├── index.html              ✅ Home page
├── destinations.html       ✅ Destinations page
├── gallery.html           ✅ Gallery page
├── about.html             ✅ About page
├── contact.html           ✅ Contact page
├── README.md              ✅ Project documentation
├── README.txt             ✅ Image credits
├── .gitignore             ✅ Git ignore file
├── css/
│   ├── styles.css         ✅ Main stylesheet
│   └── responsive.css     ✅ Responsive styles
└── images/
    ├── destinations/      ✅ (empty - using Unsplash API)
    ├── gallery/          ✅ (empty - using Unsplash API)
    ├── hero/             ✅ (empty - using Unsplash API)
    └── icons/
        └── logo.svg      ✅ Logo file
```

## 📝 Git Commands to Push

Open Terminal in this folder and run these commands:

```bash
# Add all files to git
git add .

# Commit with a message
git commit -m "Restructure: Move files to root for GitHub Pages"

# Push to GitHub
git push origin main
```

## 🌐 After Pushing

1. **Go to your GitHub repository**: https://github.com/jp7107/TravelWorld

2. **Check GitHub Pages settings**:
   - Go to **Settings** → **Pages**
   - Verify:
     - Source: **Deploy from a branch**
     - Branch: **main**
     - Folder: **/ (root)**
   - Click **Save** if needed

3. **Wait 2-3 minutes** for deployment

4. **Visit your live site**:
   ```
   https://jp7107.github.io/TravelWorld/
   ```

## 🔧 If You Get Errors

### Error: "failed to push some refs"
```bash
# Pull first, then push
git pull origin main --rebase
git push origin main
```

### Error: "Your branch is behind"
```bash
# Pull and merge
git pull origin main
git push origin main
```

### Error: "Permission denied"
```bash
# Make sure you're logged in to GitHub
# You may need to set up SSH keys or use Personal Access Token
```

## ✨ What Changed

- ✅ All files moved from `COM4014/` to root directory
- ✅ Added `.gitignore` to exclude system files
- ✅ Removed unnecessary test files and documentation
- ✅ Clean structure ready for GitHub Pages

## 🎯 Your Live URL

After successful deployment:
```
https://jp7107.github.io/TravelWorld/
```

## 📱 Test Your Site

Once live, test:
- ✅ All 5 pages load correctly
- ✅ Navigation works
- ✅ Images load from Unsplash
- ✅ Responsive design works on mobile
- ✅ Contact form displays correctly

## 🐛 Troubleshooting

**404 Error?**
- Make sure `index.html` is in the root directory ✅ (Done!)
- Check GitHub Pages settings (branch: main, folder: root)
- Wait 2-3 minutes after pushing

**Images not loading?**
- Unsplash images should load automatically (they're external URLs)
- Check browser console for errors

**CSS not working?**
- Make sure `css/` folder is in root ✅ (Done!)
- Check that HTML files link to `css/styles.css` (not `COM4014/css/styles.css`)

## 🎉 You're Ready!

Just run the git commands above and your site will be live!
