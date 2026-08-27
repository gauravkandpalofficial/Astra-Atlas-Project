# Astra Atlas — Week 4 Performance Optimization Report

## 1. Project Overview

Astra Atlas is a responsive space-exploration landing page developed as a continuation of the previous project weeks. The Week 4 challenge focuses on improving front-end performance without removing the accessibility and interactive features implemented during Week 3. The page uses semantic HTML, responsive CSS, CSS-generated space illustrations, mission tabs, a mission briefing dialog, mobile navigation and an accessible newsletter demonstration.

## 2. Objective

The objective of Week 4 was to identify front-end performance bottlenecks, apply practical optimization techniques, and compare the project before and after optimization. The optimization work prioritizes faster initial rendering, reduced JavaScript blocking, less off-screen rendering work, and smaller production assets while keeping the existing visual design and functionality intact.

## 3. Initial Audit Findings

The original project was already lightweight and did not contain external image files, video files, frameworks, or third-party JavaScript libraries. Its visual space illustrations are produced with CSS gradients and shapes. Therefore, adding image lazy loading would not provide a real benefit and would unnecessarily complicate the page.

The main opportunities identified from code inspection were:

1. The JavaScript file was loaded without an explicit `defer` attribute.
2. The page used readable source assets directly rather than separate production/minified assets.
3. Several lower-page sections were rendered even though they were initially outside the viewport.
4. The page does not require code splitting because the JavaScript bundle is small and the site has no large feature modules.

## 4. Optimizations Implemented

### 4.1 Deferred JavaScript loading

The original entry point loaded `script.js` normally. The optimized page loads the production script with `defer`. This allows the browser to continue parsing the HTML while the script is downloaded and then execute it after document parsing.

### 4.2 JavaScript production asset

A minified `script.min.js` file was generated from the existing JavaScript source and is now loaded by the production page. The readable `script.js` file is retained for maintainability.

### 4.3 CSS production asset

The optimized page loads `styles.min.css`, while the readable `styles.css` source remains available. The stylesheet was already highly compact, so the resulting size reduction is intentionally small rather than being overstated.

### 4.4 Reduced off-screen rendering

`content-visibility: auto` was applied to the lower-page Notes, About, Subscribe and Footer sections. Intrinsic sizes were supplied to reserve reasonable layout space. This allows the browser to skip some rendering work for content that is initially outside the viewport while preserving page layout.

### 4.5 Image optimization decision

The page contains no `<img>` elements and no external raster image assets. The Moon, Mars, Earth and star-field visuals are CSS-generated. Consequently, `loading="lazy"`, responsive image formats and image compression were not artificially introduced. This keeps the implementation lightweight and avoids optimizing a problem that does not exist.

### 4.6 Caching strategy

CSS and JavaScript remain separate static assets so a browser or CDN can cache them independently of the HTML document. Long-term cache headers are deployment-server settings and cannot be reliably configured from HTML/CSS/JavaScript alone. A production host should serve versioned static assets with appropriate cache-control headers.

## 5. Before-and-After Asset Comparison

The following values are measured directly from the project files and do not depend on an external Lighthouse server.

| Asset | Before | After | Change |
|---|---:|---:|---:|
| JavaScript source | 4,110 B | 3,823 B production asset | 287 B / 7.0% smaller |
| CSS source | 10,940 B | 10,901 B production asset | 39 B / 0.4% smaller |
| HTML | 8,860 B | 8,874 B | +14 B |
| Loaded app assets (HTML + production CSS + production JS) | 23,667 B | 23,598 B | 69 B / 0.3% smaller |

The HTML increased slightly because it now references production asset filenames and the `defer` attribute. The important comparison is the assets actually requested by the optimized page.

## 6. External Performance Measurement

The assignment requires Google PageSpeed Insights or Lighthouse measurements. The final project should be served from a public URL before recording these scores.

### Baseline — original Week 3 version

- Performance: **Record Lighthouse/PageSpeed result here**
- First Contentful Paint (FCP): **Record result here**
- Largest Contentful Paint (LCP): **Record result here**
- Total Blocking Time (TBT): **Record result here**
- Cumulative Layout Shift (CLS): **Record result here**
- Speed Index: **Record result here**

### Optimized — Week 4 version

- Performance: **Record Lighthouse/PageSpeed result here**
- First Contentful Paint (FCP): **Record result here**
- Largest Contentful Paint (LCP): **Record result here**
- Total Blocking Time (TBT): **Record result here**
- Cumulative Layout Shift (CLS): **Record result here**
- Speed Index: **Record result here**

### Important measurement note

External PageSpeed/Lighthouse scores were not fabricated for this report. They depend on the public URL, browser version, network conditions and audit environment. The project was optimized from the actual source code, while the external score fields above should be populated by running the required audit on the final hosted version.

## 7. Testing Performed

The project was checked for preservation of the existing interactive behavior and accessibility-oriented implementation. The following functionality should be verified after hosting:

- Mobile navigation opens and closes correctly.
- Escape closes the mobile navigation.
- Mission tabs can be changed with mouse and keyboard controls.
- Mission briefing buttons open the dialog and return focus correctly.
- Newsletter validation displays feedback for an invalid email.
- Valid newsletter submission displays the success message.
- Responsive layout works at narrow viewport widths.
- Reduced-motion preferences continue to disable non-essential animation and smooth scrolling.

## 8. Challenges Encountered

The main challenge was avoiding unnecessary optimization. The project does not use large images or third-party libraries, so common recommendations such as image compression and code splitting would not have addressed real bottlenecks. The optimization therefore concentrated on script scheduling, production asset delivery, off-screen rendering and small JavaScript efficiency improvements.

Another challenge is that performance scores are environment-dependent. A Lighthouse score from one run should not be presented as a permanent property of the website. For that reason, the final submission separates reproducible file measurements from the required hosted Lighthouse/PageSpeed measurements.

## 9. Conclusion

The Week 4 Astra Atlas revision applies practical front-end performance techniques while preserving the project's visual design, responsiveness and accessibility features. JavaScript is now deferred and delivered through a smaller production asset, CSS is provided as a production asset, and lower-page rendering work is reduced with `content-visibility`. The project also avoids unnecessary image and code-splitting optimizations because its current architecture does not contain those bottlenecks.

The final step for the submitted hosted version is to run Google PageSpeed Insights or Chrome Lighthouse and record the actual before-and-after metrics in this report. This provides measurable evidence of the performance change without inventing results.
