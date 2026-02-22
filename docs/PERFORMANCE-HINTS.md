# Performance Hints Documentation

## Overview
This document describes the performance optimizations added to the Helix landing page for faster initial load times and improved resource loading efficiency.

## Changes Made

### 1. Preconnect for External Origins
Early connections to external domains for faster font loading:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```
- **fonts.googleapis.com**: Connection for font stylesheet
- **fonts.gstatic.com**: Connection for font files (with `crossorigin` for CORS)

### 2. DNS-Prefetch for Third-Party Domains
DNS resolution hints for domains users may navigate to:
```html
<link rel="dns-prefetch" href="https://github.com">
<link rel="dns-prefetch" href="https://discord.com">
```
These resolve DNS early for smoother navigation to external links.

### 3. Preload Critical Assets
High-priority loading for render-critical resources:
```html
<link rel="preload" href="css/styles.css" as="style">
<link rel="preload" href="images/dashboard-overview.png" as="image" type="image/png">
```
- **css/styles.css**: Critical stylesheet loaded with highest priority
- **dashboard-overview.png**: Hero image in showcase section (above fold)

### 4. Lazy Loading for Below-Fold Images
Native lazy loading added to images not visible on initial viewport:

| Image | Location | Loading |
|-------|----------|---------|
| dashboard-overview.png | Showcase (hero) | **eager** (above fold) |
| dashboard-overview.png | Screenshots gallery | `lazy` |
| condo-context.png | Screenshots gallery | `lazy` |
| agents-overview.png | Screenshots gallery | `lazy` |
| search-view.png | Screenshots gallery | `lazy` |

## Performance Benefits

1. **Faster First Contentful Paint (FCP)**
   - Preconnect eliminates DNS/TLS handshake delays for fonts
   - Preload ensures critical CSS loads with highest priority

2. **Faster Largest Contentful Paint (LCP)**
   - Hero image is preloaded for immediate availability
   - Browser can fetch the hero image while parsing HTML

3. **Reduced Initial Page Weight**
   - 4 below-fold images (~360KB combined) deferred until needed
   - Only critical resources loaded on initial page load

4. **Improved Core Web Vitals**
   - LCP improvement from preloaded hero image
   - Lower cumulative layout shift (CLS) since critical image dimensions are known

## Files Modified
- `index.html` - Added performance hints in `<head>` and `loading="lazy"` attributes

## Validation
Test with:
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - Check "Performance" score
- [WebPageTest](https://www.webpagetest.org/) - Verify waterfall and preload effectiveness
- Chrome DevTools Network tab - Confirm preload priority and lazy loading
