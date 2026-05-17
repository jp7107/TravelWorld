# Design Document: Travel and Tourism Website

## Overview

This design document specifies the technical architecture and implementation approach for a static travel and tourism website. The website will be built using pure HTML5 and CSS3 without frameworks or libraries, targeting academic assessment requirements (COM4014). The system consists of five interconnected pages showcasing travel destinations, providing service information, and collecting user feedback through a contact form.

### Design Goals

1. **Simplicity**: Clean, maintainable HTML/CSS codebase without framework dependencies
2. **Responsiveness**: Fluid layouts adapting to mobile (< 768px), tablet (768-1024px), and desktop (> 1024px) viewports
3. **Standards Compliance**: Zero validation errors for HTML5 and CSS3
4. **Accessibility**: WCAG-compliant markup with zero critical WAVE errors
5. **Cross-Browser Compatibility**: Consistent rendering across Chrome, Firefox, and Edge
6. **Deployability**: Simple file structure compatible with Arden hosting environment

## Architecture

### System Architecture

The website follows a **static multi-page architecture** with no server-side processing or client-side frameworks:

```
┌─────────────────────────────────────────────────────┐
│                    Browser                          │
│  ┌──────────────────────────────────────────────┐  │
│  │         HTML Pages (5 pages)                 │  │
│  │  - index.html (Home)                         │  │
│  │  - destinations.html                         │  │
│  │  - gallery.html                              │  │
│  │  - about.html                                │  │
│  │  - contact.html                              │  │
│  └──────────────────────────────────────────────┘  │
│                      ↓                              │
│  ┌──────────────────────────────────────────────┐  │
│  │         CSS Stylesheets                      │  │
│  │  - styles.css (main styles)                  │  │
│  │  - responsive.css (media queries)            │  │
│  └──────────────────────────────────────────────┘  │
│                      ↓                              │
│  ┌──────────────────────────────────────────────┐  │
│  │         Static Assets                        │  │
│  │  - images/ (optimized web images)           │  │
│  └──────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────┘
```

### File Structure

```
COM4014/
├── index.html
├── destinations.html
├── gallery.html
├── about.html
├── contact.html
├── css/
│   ├── styles.css
│   └── responsive.css
├── images/
│   ├── hero/
│   │   ├── home-hero.jpg
│   │   └── destinations-hero.jpg
│   ├── destinations/
│   │   ├── paris.jpg
│   │   ├── tokyo.jpg
│   │   ├── bali.jpg
│   │   └── new-york.jpg
│   ├── gallery/
│   │   ├── gallery-01.jpg
│   │   ├── gallery-02.jpg
│   │   └── ... (8-12 images)
│   └── icons/
│       ├── logo.svg
│       └── favicon.ico
└── README.txt (image credits)
```

## Components and Interfaces

### 1. Navigation Component

**Purpose**: Provide consistent site-wide navigation across all pages

**HTML Structure**:
```html
<nav class="main-nav" role="navigation" aria-label="Main navigation">
  <div class="nav-container">
    <div class="logo">
      <a href="index.html" aria-label="Home">
        <img src="images/icons/logo.svg" alt="TravelWorld Logo">
      </a>
    </div>
    <ul class="nav-menu">
      <li><a href="index.html" class="active">Home</a></li>
      <li><a href="destinations.html">Destinations</a></li>
      <li><a href="gallery.html">Gallery</a></li>
      <li><a href="about.html">About</a></li>
      <li><a href="contact.html">Contact</a></li>
    </ul>
  </div>
</nav>
```

**CSS Approach**:
- Desktop: Horizontal flexbox layout with inline menu items
- Tablet: Horizontal layout with reduced spacing
- Mobile: Vertical stacked menu (no hamburger icon required, pure CSS solution)

**Active State Indication**:
- Each page adds `class="active"` to its corresponding nav link
- CSS styling: `border-bottom: 3px solid #007bff` for active link

### 2. Hero Section Component

**Purpose**: Provide visual impact and page context on Home and Destinations pages

**HTML Structure**:
```html
<section class="hero" role="banner">
  <div class="hero-image">
    <img src="images/hero/home-hero.jpg" alt="Beautiful tropical beach destination">
  </div>
  <div class="hero-content">
    <h1>Discover Your Next Adventure</h1>
    <p class="hero-subtitle">Explore breathtaking destinations around the world</p>
    <a href="destinations.html" class="cta-button">Explore Destinations</a>
  </div>
</section>
```

**Responsive Behavior**:
- Desktop: Full-width background image with centered overlay text
- Tablet: Reduced hero height (60vh → 50vh)
- Mobile: Stacked layout with image above text (40vh hero height)

### 3. Destination Card Component

**Purpose**: Display individual destination information on Destinations page

**HTML Structure**:
```html
<article class="destination-card">
  <img src="images/destinations/paris.jpg" alt="Eiffel Tower in Paris, France">
  <div class="card-content">
    <h3>Paris, France</h3>
    <p class="destination-description">
      Experience the romance of the City of Light with its iconic landmarks,
      world-class museums, and exquisite cuisine.
    </p>
    <ul class="destination-highlights">
      <li>Eiffel Tower</li>
      <li>Louvre Museum</li>
      <li>Notre-Dame Cathedral</li>
    </ul>
  </div>
</article>
```

**Layout**:
- Desktop: CSS Grid with 2 columns (`grid-template-columns: repeat(2, 1fr)`)
- Tablet: CSS Grid with 2 columns, reduced gap
- Mobile: Single column (`grid-template-columns: 1fr`)

### 4. Gallery Grid Component

**Purpose**: Display travel images in responsive grid layout

**HTML Structure**:
```html
<section class="gallery-grid">
  <figure class="gallery-item">
    <img src="images/gallery/gallery-01.jpg" alt="Sunset over Santorini, Greece">
    <figcaption>Santorini Sunset</figcaption>
  </figure>
  <!-- Repeat for 8-12 images -->
</section>
```

**Layout**:
- Desktop: CSS Grid with 3 columns (`grid-template-columns: repeat(3, 1fr)`)
- Tablet: CSS Grid with 2 columns
- Mobile: Single column

**Image Optimization**:
- Maximum width: 800px
- Format: JPEG with 80% quality
- Aspect ratio: 4:3 or 16:9 maintained via CSS

### 5. Contact Form Component

**Purpose**: Collect user feedback and contact information

**HTML Structure**:
```html
<form class="contact-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
  <div class="form-group">
    <label for="name">Full Name <span class="required">*</span></label>
    <input type="text" id="name" name="name" required aria-required="true">
  </div>
  
  <div class="form-group">
    <label for="email">Email Address <span class="required">*</span></label>
    <input type="email" id="email" name="email" required aria-required="true">
  </div>
  
  <div class="form-group">
    <label for="phone">Phone Number</label>
    <input type="tel" id="phone" name="phone">
  </div>
  
  <div class="form-group">
    <label for="destination">Interested Destination</label>
    <select id="destination" name="destination">
      <option value="">Select a destination</option>
      <option value="paris">Paris, France</option>
      <option value="tokyo">Tokyo, Japan</option>
      <option value="bali">Bali, Indonesia</option>
      <option value="newyork">New York, USA</option>
    </select>
  </div>
  
  <div class="form-group">
    <label for="message">Your Message <span class="required">*</span></label>
    <textarea id="message" name="message" rows="6" required aria-required="true"></textarea>
  </div>
  
  <button type="submit" class="submit-button">Send Message</button>
</form>
```

**Form Processing**:
- Action: Formspree.io (free form backend service)
- Method: POST
- No JavaScript validation required (HTML5 validation sufficient)

**Accessibility Features**:
- All inputs have associated `<label>` elements with `for` attribute
- Required fields marked with `required` attribute and `aria-required="true"`
- Visual indication of required fields with asterisk
- Proper input types (`email`, `tel`, `text`, `textarea`)

### 6. Footer Component

**Purpose**: Provide consistent site-wide footer with copyright and links

**HTML Structure**:
```html
<footer class="site-footer" role="contentinfo">
  <div class="footer-content">
    <div class="footer-section">
      <h4>Quick Links</h4>
      <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="destinations.html">Destinations</a></li>
        <li><a href="gallery.html">Gallery</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html">Contact</a></li>
      </ul>
    </div>
    <div class="footer-section">
      <h4>Contact Info</h4>
      <p>Email: info@travelworld.com</p>
      <p>Phone: +44 123 456 7890</p>
    </div>
    <div class="footer-section">
      <h4>Follow Us</h4>
      <p>Social media links (text-based)</p>
    </div>
  </div>
  <div class="footer-bottom">
    <p>&copy; 2024 TravelWorld. All rights reserved.</p>
    <p>Images sourced from Unsplash and Pexels (royalty-free)</p>
  </div>
</footer>
```

## Data Models

### Page Structure Model

Each HTML page follows this consistent structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="[Page-specific description]">
  <title>[Page Title] | TravelWorld</title>
  <link rel="stylesheet" href="css/styles.css">
  <link rel="stylesheet" href="css/responsive.css">
  <link rel="icon" type="image/x-icon" href="images/icons/favicon.ico">
</head>
<body>
  <header>
    <!-- Navigation Component -->
  </header>
  
  <main>
    <!-- Page-specific content -->
  </main>
  
  <footer>
    <!-- Footer Component -->
  </footer>
</body>
</html>
```

### CSS Organization Model

**styles.css** (Main stylesheet):
```css
/* 1. CSS Reset and Base Styles */
/* 2. Typography */
/* 3. Layout Containers */
/* 4. Navigation Component */
/* 5. Hero Component */
/* 6. Card Components */
/* 7. Form Components */
/* 8. Gallery Components */
/* 9. Footer Component */
/* 10. Utility Classes */
```

**responsive.css** (Media queries):
```css
/* Mobile First Approach */

/* Tablet: 768px and up */
@media screen and (min-width: 768px) {
  /* Tablet-specific overrides */
}

/* Desktop: 1024px and up */
@media screen and (min-width: 1024px) {
  /* Desktop-specific overrides */
}

/* Large Desktop: 1440px and up */
@media screen and (min-width: 1440px) {
  /* Large screen optimizations */
}
```

### Color Palette Model

```css
:root {
  /* Primary Colors */
  --primary-blue: #007bff;
  --primary-dark: #0056b3;
  --primary-light: #66b3ff;
  
  /* Neutral Colors */
  --white: #ffffff;
  --light-gray: #f8f9fa;
  --medium-gray: #6c757d;
  --dark-gray: #343a40;
  --black: #000000;
  
  /* Accent Colors */
  --accent-orange: #ff6b35;
  --accent-green: #28a745;
  
  /* Semantic Colors */
  --error-red: #dc3545;
  --success-green: #28a745;
  
  /* Typography */
  --font-primary: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  --font-heading: Georgia, 'Times New Roman', serif;
  
  /* Spacing */
  --spacing-xs: 0.5rem;
  --spacing-sm: 1rem;
  --spacing-md: 1.5rem;
  --spacing-lg: 2rem;
  --spacing-xl: 3rem;
}
```

### Typography Scale Model

```css
/* Base font size: 16px */
body {
  font-size: 1rem; /* 16px */
  line-height: 1.6;
}

h1 { font-size: 2.5rem; }   /* 40px */
h2 { font-size: 2rem; }     /* 32px */
h3 { font-size: 1.5rem; }   /* 24px */
h4 { font-size: 1.25rem; }  /* 20px */
p  { font-size: 1rem; }     /* 16px */
small { font-size: 0.875rem; } /* 14px */

/* Mobile adjustments */
@media screen and (max-width: 767px) {
  h1 { font-size: 2rem; }    /* 32px */
  h2 { font-size: 1.75rem; } /* 28px */
  h3 { font-size: 1.25rem; } /* 20px */
}
```

## Responsive Design Strategy

### Breakpoint System

| Device Category | Viewport Width | Layout Strategy |
|----------------|----------------|-----------------|
| Mobile | < 768px | Single column, stacked navigation, full-width images |
| Tablet | 768px - 1023px | 2-column grids, horizontal navigation, optimized spacing |
| Desktop | 1024px - 1439px | Multi-column grids, full navigation, standard spacing |
| Large Desktop | ≥ 1440px | Max-width container (1200px), centered content |

### Mobile-First Approach

Base styles target mobile devices, with progressive enhancement for larger screens:

1. **Mobile Base** (default styles):
   - Single column layouts
   - Full-width elements
   - Larger touch targets (min 44x44px)
   - Simplified navigation
   - Reduced font sizes

2. **Tablet Enhancement** (768px+):
   - 2-column grids where appropriate
   - Horizontal navigation
   - Increased spacing
   - Larger typography

3. **Desktop Enhancement** (1024px+):
   - 3-column grids
   - Full-featured navigation
   - Maximum spacing
   - Largest typography
   - Hover effects

### Responsive Images Strategy

**HTML Implementation**:
```html
<img src="images/destinations/paris.jpg" 
     alt="Eiffel Tower in Paris, France"
     loading="lazy">
```

**CSS Implementation**:
```css
img {
  max-width: 100%;
  height: auto;
  display: block;
}

/* Maintain aspect ratio */
.destination-card img {
  width: 100%;
  height: 250px;
  object-fit: cover;
  object-position: center;
}
```

**Optimization Guidelines**:
- Hero images: 1920x1080px, JPEG 80% quality
- Destination cards: 800x600px, JPEG 80% quality
- Gallery images: 800x600px, JPEG 80% quality
- Icons/logos: SVG format (scalable)

### Responsive Navigation Strategy

**Desktop** (1024px+):
```css
.nav-menu {
  display: flex;
  flex-direction: row;
  gap: 2rem;
}
```

**Tablet** (768px - 1023px):
```css
.nav-menu {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  font-size: 0.9rem;
}
```

**Mobile** (< 768px):
```css
.nav-menu {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.nav-menu li {
  border-bottom: 1px solid #e0e0e0;
}

.nav-menu a {
  display: block;
  padding: 1rem;
}
```

## Error Handling

### HTML Validation Errors

**Prevention Strategy**:
1. Use semantic HTML5 elements (`<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`)
2. Ensure proper nesting (no `<div>` inside `<p>`, etc.)
3. Close all tags properly
4. Use valid attribute values
5. Include required attributes (`alt` for images, `for` in labels, `action` in forms)

**Validation Process**:
- Validate each page using W3C HTML Validator (https://validator.w3.org/)
- Fix all errors before deployment
- Document validation results with screenshots

### CSS Validation Errors

**Prevention Strategy**:
1. Use valid CSS3 properties and values
2. Avoid vendor prefixes unless necessary (modern browsers support standard properties)
3. Use proper syntax (semicolons, colons, brackets)
4. Avoid typos in property names
5. Use valid color formats (hex, rgb, rgba, named colors)

**Validation Process**:
- Validate stylesheets using W3C CSS Validator (https://jigsaw.w3.org/css-validator/)
- Fix all errors before deployment
- Warnings are acceptable (e.g., vendor prefixes)

### Accessibility Errors

**Prevention Strategy**:
1. **Images**: All `<img>` tags must have meaningful `alt` attributes
2. **Forms**: All inputs must have associated `<label>` elements
3. **Headings**: Maintain proper hierarchy (h1 → h2 → h3, no skipping)
4. **Color Contrast**: Ensure 4.5:1 ratio for normal text, 3:1 for large text
5. **Keyboard Navigation**: All interactive elements must be keyboard accessible
6. **ARIA**: Use ARIA labels where appropriate (`role`, `aria-label`, `aria-required`)

**Testing Process**:
- Test each page using WAVE tool (https://wave.webaim.org/)
- Fix all critical errors (red icons)
- Address warnings where possible (yellow icons)
- Document results with screenshots

### Browser Compatibility Issues

**Prevention Strategy**:
1. Use standard CSS properties (avoid experimental features)
2. Test in all three required browsers (Chrome, Firefox, Edge)
3. Avoid browser-specific CSS
4. Use CSS Grid and Flexbox (supported in all modern browsers)
5. Avoid deprecated HTML elements

**Fallback Strategy**:
- CSS Grid with Flexbox fallback (not needed for modern browsers)
- Standard web fonts with system font fallbacks
- Progressive enhancement approach

### Form Submission Handling

**Error States**:
1. **Empty Required Fields**: Handled by HTML5 `required` attribute
2. **Invalid Email Format**: Handled by `type="email"` validation
3. **Form Submission Failure**: Formspree.io provides error page

**Success State**:
- Formspree.io redirects to success page
- Optional: Create custom `thank-you.html` page

## Testing Strategy

Since this is a static HTML/CSS website with no complex logic or data transformations, **property-based testing is not applicable**. The testing strategy focuses on validation, visual regression, cross-browser compatibility, and accessibility compliance.

### 1. HTML Validation Testing

**Objective**: Ensure all HTML pages pass W3C validation with zero errors

**Process**:
1. Navigate to https://validator.w3.org/
2. Validate each page by URL (after deployment) or file upload
3. Fix all errors reported
4. Capture screenshots showing "Document checking completed. No errors or warnings to show."
5. Repeat for all 5 pages

**Success Criteria**:
- Zero HTML errors for all pages
- Zero HTML warnings (preferred but not required)

### 2. CSS Validation Testing

**Objective**: Ensure all stylesheets pass W3C CSS validation with zero errors

**Process**:
1. Navigate to https://jigsaw.w3.org/css-validator/
2. Validate each CSS file by direct input or URL
3. Fix all errors reported
4. Capture screenshots showing "Congratulations! No Error Found."
5. Document any warnings (acceptable for vendor prefixes)

**Success Criteria**:
- Zero CSS errors for all stylesheets
- Warnings documented and justified

### 3. Accessibility Testing

**Objective**: Ensure all pages pass WAVE accessibility evaluation with zero critical errors

**Process**:
1. Navigate to https://wave.webaim.org/
2. Test each page by URL
3. Review errors (red icons), alerts (yellow icons), and features (green icons)
4. Fix all critical errors:
   - Missing alt text
   - Missing form labels
   - Insufficient color contrast
   - Heading hierarchy issues
5. Capture screenshots showing zero errors
6. Document before/after corrections

**Success Criteria**:
- Zero critical accessibility errors (red icons)
- Warnings addressed where feasible
- All images have alt text
- All forms have proper labels
- Heading hierarchy is logical
- Color contrast meets WCAG AA standards (4.5:1 for normal text)

### 4. Responsive Design Testing

**Objective**: Verify correct layout rendering across mobile, tablet, and desktop viewports

**Process**:
1. Use browser DevTools to test responsive breakpoints
2. Test each page at:
   - Mobile: 375px width (iPhone SE)
   - Tablet: 768px width (iPad)
   - Desktop: 1440px width (standard laptop)
3. Verify:
   - Navigation adapts correctly
   - Images scale appropriately
   - Text remains readable
   - No horizontal scrolling
   - Grid layouts adjust to correct column counts
4. Capture screenshots at each breakpoint

**Success Criteria**:
- All pages render correctly at all three breakpoints
- No layout breaking or overflow issues
- Touch targets are minimum 44x44px on mobile
- Text is readable without zooming

### 5. Cross-Browser Compatibility Testing

**Objective**: Ensure consistent rendering across Chrome, Firefox, and Edge

**Process**:
1. Test all 5 pages in:
   - Google Chrome (latest version)
   - Mozilla Firefox (latest version)
   - Microsoft Edge (latest version)
2. Verify:
   - Visual consistency (colors, spacing, fonts)
   - Functional consistency (navigation, forms, links)
   - No browser-specific rendering issues
3. Capture screenshots from each browser

**Success Criteria**:
- Visual appearance is consistent across all three browsers
- All functionality works in all three browsers
- No browser-specific errors in console

### 6. Form Functionality Testing

**Objective**: Verify form validation and submission work correctly

**Process**:
1. Test HTML5 validation:
   - Submit form with empty required fields (should show validation message)
   - Submit form with invalid email format (should show validation message)
   - Submit form with valid data (should submit successfully)
2. Test form submission to Formspree.io
3. Verify success/error handling

**Success Criteria**:
- Required field validation works
- Email format validation works
- Form submits successfully with valid data
- User receives confirmation of submission

### 7. Image Optimization Testing

**Objective**: Ensure images are properly optimized for web delivery

**Process**:
1. Check image file sizes (should be < 500KB for hero images, < 200KB for other images)
2. Verify image formats (JPEG for photos, SVG for logos/icons)
3. Test image loading performance
4. Verify lazy loading works (images load as user scrolls)

**Success Criteria**:
- All images are optimized for web
- Page load time is acceptable (< 3 seconds on 3G)
- Images have appropriate dimensions

### 8. Link Testing

**Objective**: Verify all internal and external links work correctly

**Process**:
1. Click every navigation link on every page
2. Verify correct page loads
3. Check that active state indicator updates correctly
4. Test any external links (if present)

**Success Criteria**:
- All internal links navigate to correct pages
- Active state indicator shows current page
- No broken links (404 errors)

### 9. Manual Visual Inspection

**Objective**: Ensure overall design quality and consistency

**Process**:
1. Review each page for:
   - Visual consistency (colors, fonts, spacing)
   - Content alignment
   - Image quality
   - Typography hierarchy
   - White space usage
2. Compare against design mockups (if available)

**Success Criteria**:
- Design is visually consistent across all pages
- Content is well-organized and readable
- No visual glitches or artifacts

### Testing Documentation Requirements

All testing must be documented in the testing report (STUxxxx_testing.docx/pdf) with:
- Screenshots demonstrating each test type
- Before/after screenshots for error corrections
- Browser testing evidence (screenshots from Chrome, Firefox, Edge)
- Device testing evidence (screenshots at mobile, tablet, desktop sizes)
- Validation results (HTML, CSS, WAVE)
- Summary of issues found and resolved

---

## Implementation Notes

### Development Workflow

1. **Setup Phase**:
   - Create folder structure
   - Set up base HTML template
   - Create CSS reset and base styles

2. **Component Development Phase**:
   - Build navigation component
   - Build footer component
   - Build hero component
   - Build card components
   - Build form component
   - Build gallery component

3. **Page Assembly Phase**:
   - Create index.html (Home)
   - Create destinations.html
   - Create gallery.html
   - Create about.html
   - Create contact.html

4. **Responsive Implementation Phase**:
   - Add mobile styles
   - Add tablet media queries
   - Add desktop media queries
   - Test at all breakpoints

5. **Validation Phase**:
   - HTML validation
   - CSS validation
   - Accessibility testing
   - Browser testing
   - Fix all errors

6. **Deployment Phase**:
   - Upload to Arden hosting
   - Test live URL
   - Verify all assets load correctly

### Best Practices

1. **HTML**:
   - Use semantic elements
   - Maintain proper heading hierarchy
   - Include all required meta tags
   - Use descriptive alt text
   - Associate labels with form inputs

2. **CSS**:
   - Use CSS custom properties for colors and spacing
   - Follow mobile-first approach
   - Use Flexbox and Grid for layouts
   - Avoid !important declarations
   - Keep specificity low
   - Group related styles together

3. **Images**:
   - Optimize before uploading
   - Use appropriate formats (JPEG for photos, SVG for graphics)
   - Include alt text for all images
   - Use lazy loading for below-fold images
   - Maintain consistent aspect ratios

4. **Accessibility**:
   - Test with keyboard navigation
   - Ensure sufficient color contrast
   - Use ARIA attributes where appropriate
   - Provide skip links for screen readers
   - Test with WAVE tool

5. **Performance**:
   - Minimize CSS file size
   - Optimize images
   - Use lazy loading
   - Minimize HTTP requests
   - Avoid inline styles

### Deployment Checklist

- [ ] All HTML files validated (zero errors)
- [ ] All CSS files validated (zero errors)
- [ ] All pages tested with WAVE (zero critical errors)
- [ ] All pages tested in Chrome, Firefox, Edge
- [ ] All pages tested at mobile, tablet, desktop sizes
- [ ] All images optimized and include alt text
- [ ] All links tested and working
- [ ] Form tested and working
- [ ] README.txt with image credits included
- [ ] Files uploaded to COM4014 folder on Arden hosting
- [ ] Live URL tested and working
- [ ] Specification document completed
- [ ] Testing report completed with screenshots
- [ ] website.zip package created

---

## Conclusion

This design provides a comprehensive blueprint for implementing a standards-compliant, accessible, and responsive travel and tourism website using pure HTML5 and CSS3. The architecture prioritizes simplicity, maintainability, and compliance with academic assessment requirements while delivering a professional user experience across all devices and browsers.

The testing strategy ensures quality through systematic validation, accessibility testing, and cross-browser verification, with all results documented for academic submission. The modular component approach allows for efficient development and easy maintenance, while the mobile-first responsive strategy ensures optimal display across all viewport sizes.

