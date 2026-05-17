# TravelWorld - Travel & Tourism Website

A responsive travel and tourism website built with pure HTML5 and CSS3, showcasing beautiful destinations from around the world.

## 📋 Project Overview

This is an academic project (COM4014) that demonstrates modern web development practices including:
- Semantic HTML5 markup
- Responsive CSS3 design
- Accessibility compliance (WCAG 2.1 Level AA)
- Mobile-first approach
- Cross-browser compatibility

## 🌟 Features

- **5 Complete Pages**: Home, Destinations, Gallery, About, Contact
- **Fully Responsive**: Optimized for mobile, tablet, and desktop devices
- **Accessible**: WCAG 2.1 Level AA compliant with proper ARIA labels
- **Modern Design**: Clean, professional layout with smooth animations
- **Contact Form**: HTML5 form with validation (Formspree integration)
- **Image Gallery**: 12 stunning travel photos from around the world
- **No Frameworks**: Pure HTML/CSS implementation (no Bootstrap, React, etc.)

## 📁 Project Structure

```
COM4014/
├── index.html              # Home page
├── destinations.html       # Destinations showcase
├── gallery.html           # Photo gallery
├── about.html             # About us page
├── contact.html           # Contact form
├── README.md              # This file
├── README.txt             # Image credits
├── css/
│   ├── styles.css         # Main stylesheet
│   └── responsive.css     # Responsive media queries
└── images/
    ├── destinations/      # Destination images (via Unsplash API)
    ├── gallery/          # Gallery images (via Unsplash API)
    ├── hero/             # Hero section images (via Unsplash API)
    └── icons/
        └── logo.svg      # Website logo
```

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Edge, Safari)
- A text editor (VS Code, Sublime Text, etc.)
- Internet connection (for Unsplash images)

### Installation

1. **Download or clone the project**
   ```bash
   # If using git
   git clone <repository-url>
   
   # Or simply download the ZIP file
   ```

2. **Open the project**
   - Navigate to the `COM4014` folder
   - Open `index.html` in your web browser

3. **That's it!** The website should load with all images from Unsplash.

### Local Development

Simply open any HTML file in your browser:
- Double-click `index.html` to view the home page
- Use the navigation menu to browse other pages
- No server required for basic functionality

### Form Setup (Optional)

To make the contact form functional:

1. Go to [Formspree.io](https://formspree.io/)
2. Create a free account
3. Create a new form
4. Copy your form endpoint (e.g., `https://formspree.io/f/xyzabc123`)
5. Open `contact.html` and replace `YOUR_FORM_ID` with your actual endpoint:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

## 🎨 Pages Overview

### 1. Home Page (`index.html`)
- Hero section with call-to-action
- Welcome introduction
- Featured destinations preview (4 cards)

### 2. Destinations Page (`destinations.html`)
- Hero section
- 4 destination cards with details:
  - Paris, France
  - Tokyo, Japan
  - Bali, Indonesia
  - New York, USA

### 3. Gallery Page (`gallery.html`)
- 12 stunning travel photos
- Responsive grid layout (3 columns → 2 columns → 1 column)
- Image captions

### 4. About Page (`about.html`)
- Company story
- Mission statement
- Services offered
- Why choose us

### 5. Contact Page (`contact.html`)
- Contact form with validation
- Contact information (email, phone, office)
- Formspree integration

## 📱 Responsive Breakpoints

The website adapts to different screen sizes:

- **Mobile**: < 768px (single column layout)
- **Tablet**: 768px - 1023px (2 column layout)
- **Desktop**: 1024px+ (3 column layout)
- **Large Desktop**: 1440px+ (max-width container)

## ♿ Accessibility Features

- Semantic HTML5 elements (`<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`)
- ARIA labels and roles
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text for all images
- Keyboard navigation support
- Focus indicators for interactive elements
- Sufficient color contrast (WCAG AA compliant)
- Form labels associated with inputs
- Touch-friendly targets (minimum 44x44px on mobile)

## 🖼️ Images

All images are sourced from [Unsplash](https://unsplash.com/) via their Source API:
- **License**: Unsplash License (free for commercial and non-commercial use)
- **Attribution**: Photographer credits listed in `README.txt`
- **Delivery**: Images served directly from Unsplash CDN
- **Optimization**: Automatic optimization via Unsplash API parameters

### Image Parameters Used:
- Hero images: `w=1920&h=1080&fit=crop`
- Destination cards: `w=800&h=600&fit=crop`
- Gallery images: `w=800&h=600&fit=crop`

## 🌐 Browser Compatibility

Tested and working on:
- ✅ Google Chrome (latest)
- ✅ Mozilla Firefox (latest)
- ✅ Microsoft Edge (latest)
- ✅ Safari (latest)

## 🛠️ Technologies Used

- **HTML5**: Semantic markup, forms, accessibility features
- **CSS3**: Flexbox, Grid, custom properties, media queries, transitions
- **Unsplash API**: High-quality travel photography
- **Formspree**: Form submission handling (optional)

## 📝 Code Quality

- ✅ Valid HTML5 (W3C validated)
- ✅ Valid CSS3 (W3C validated)
- ✅ Zero accessibility errors (WAVE tested)
- ✅ Mobile-first responsive design
- ✅ Cross-browser compatible
- ✅ No JavaScript frameworks required
- ✅ Clean, maintainable code structure

## 🚢 Deployment

### Option 1: Arden Hosting (Academic)
1. Upload the entire `COM4014` folder to your Arden hosting account
2. Ensure files are in the correct directory structure
3. Access via your assigned URL

### Option 2: GitHub Pages
1. Create a GitHub repository
2. Upload all files
3. Enable GitHub Pages in repository settings
4. Access via `https://yourusername.github.io/repository-name/`

### Option 3: Netlify/Vercel
1. Create an account on [Netlify](https://netlify.com/) or [Vercel](https://vercel.com/)
2. Drag and drop the `COM4014` folder
3. Get instant deployment with custom URL

## 📊 Performance

- **Lightweight**: Minimal CSS, no JavaScript frameworks
- **Fast Loading**: Images served from Unsplash CDN
- **Optimized**: Lazy loading for gallery images
- **Efficient**: CSS Grid and Flexbox for layouts

## 🔧 Customization

### Change Colors
Edit CSS custom properties in `css/styles.css`:
```css
:root {
  --primary-blue: #007bff;
  --primary-dark: #0056b3;
  /* ... other colors ... */
}
```

### Add More Destinations
Edit `destinations.html` and add more destination cards following the existing pattern.

### Modify Layout
Edit `css/responsive.css` to adjust breakpoints and grid layouts.

## 📄 License

This project is created for academic purposes (COM4014 assignment).

Images are licensed under the [Unsplash License](https://unsplash.com/license).

## 👤 Author

**Student Project** - COM4014 Assignment
- Academic Institution: [Your Institution]
- Course: Web Development
- Year: 2024

## 🙏 Acknowledgments

- **Unsplash**: For providing high-quality, royalty-free travel photography
- **Photographers**: All credited in `README.txt`
- **Formspree**: For free form submission service
- **W3C**: For web standards and validation tools

## 📞 Support

For questions or issues:
- Check the code comments in HTML/CSS files
- Review the `README.txt` for image credits
- Validate HTML/CSS using W3C validators
- Test accessibility using WAVE tool

## 🎯 Assignment Requirements Met

- ✅ Minimum 5 pages (Home, Destinations, Gallery, About, Contact)
- ✅ One working form page with validation
- ✅ Responsive design (mobile, tablet, desktop)
- ✅ Pure HTML/CSS (no frameworks)
- ✅ Semantic HTML5 markup
- ✅ Accessibility compliant (WCAG AA)
- ✅ Cross-browser compatible
- ✅ Images with proper alt text
- ✅ Consistent navigation across all pages
- ✅ Professional design and layout

## 📚 Documentation

Additional documentation:
- `README.txt` - Image credits and licensing
- Code comments in HTML files
- CSS organized with clear sections

---

**Last Updated**: December 2024  
**Version**: 1.0.0  
**Status**: ✅ Production Ready
