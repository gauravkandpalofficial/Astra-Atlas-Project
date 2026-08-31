# Astra Atlas — Week 5 Mini Web Application

A responsive **Mission Control Dashboard** that integrates the frontend skills developed throughout the Astra Atlas project.

## Features
- Static mission dataset loaded from `data/missions.json` using `fetch()`.
- Responsive dashboard layout for desktop, tablet and mobile screens.
- Mission statistics and destination activity visualization.
- Filtering by status and destination.
- Live text search and sorting by date, name or duration.
- Accessible semantic HTML, skip link, visible focus states, native controls and live status messages.
- Mobile navigation with `aria-expanded` state.
- Lightweight CSS-based chart with no third-party chart library.
- Deferred JavaScript loading and reduced-motion support.

## Run locally
Because the app fetches JSON, use a local web server rather than opening `index.html` directly with `file://`.

For example, with Python:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` and select the project folder if necessary.

## Project structure

```text
Astra-Atlas-Week-5/
├── index.html
├── styles.css
├── script.js
├── data/
│   └── missions.json
└── docs/
    └── WIREFRAME.md
```
