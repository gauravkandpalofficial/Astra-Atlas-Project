# Astra Atlas — Week 4 Performance Optimization

A performance-focused revision of the Astra Atlas space-exploration landing page from Week 3.

## What changed

- Added `defer` to the JavaScript entry point so script execution does not block HTML parsing.
- Added production `script.min.js` and `styles.min.css` assets while keeping readable source files for development.
- Reduced JavaScript transfer size through minification while preserving the original interactions.
- Reduced off-screen rendering work with `content-visibility: auto` and intrinsic-size reservations on lower-page sections.
- Kept the existing CSS-generated space illustrations instead of introducing large raster images; image lazy-loading is therefore not applicable to this version.
- Preserved the Week 3 accessibility features, including semantic HTML, keyboard support, visible focus, status messaging and reduced-motion support.

## Files

- `index.html` — optimized page structure and production asset loading.
- `styles.css` — readable source stylesheet.
- `styles.min.css` — production/minified stylesheet loaded by the page.
- `script.js` — readable source JavaScript.
- `script.min.js` — production/minified JavaScript loaded by the page.
- `ACCESSIBILITY_REPORT.md` — Week 3 accessibility documentation.
- `PERFORMANCE_REPORT.md` — Week 4 performance analysis and optimization report.

## Performance testing

For the required external audit, open the final project through a public URL and run it in Google PageSpeed Insights or Chrome Lighthouse. Record the mobile and/or desktop results in `PERFORMANCE_REPORT.md`.

The optimization report also includes reproducible file-size comparisons and clearly identifies which optimizations were applicable to this project.
