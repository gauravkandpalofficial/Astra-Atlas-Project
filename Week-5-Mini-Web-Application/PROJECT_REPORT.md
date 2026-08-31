# Astra Atlas — Week 5 Final Project Integration Report

## 1. Project Overview

Week 5 brings together the frontend skills developed across the Astra Atlas project into a small, interactive web application. The final product is a **Mission Control Dashboard** that presents a static space-mission dataset through summary cards, an interactive data table, filters, search, sorting and a destination activity chart. The dashboard was designed as a natural extension of the Astra Atlas space-exploration theme while moving from a presentation-focused landing page to a data-focused application.

## 2. Requirements and Wireframe

The application requirements were translated into a simple wireframe with four main areas: a navigation/header, a mission-control hero section, an overview area containing key statistics, an interactive mission explorer, and an insights section. The wireframe is included in `docs/WIREFRAME.md`. The layout follows a clear information hierarchy so users can understand the overall dataset before exploring individual records.

## 3. Data and Dynamic Display

Mission information is stored in `data/missions.json` rather than being hard-coded into the HTML. JavaScript uses the Fetch API to load the JSON file and then calculates dashboard statistics such as total missions, active missions, completed missions and the number of participating countries. The same dataset powers the mission table and destination chart. This separation of data and presentation makes the application easier to update without changing the HTML structure.

## 4. Interactivity

The mission explorer provides filtering by status and destination, live text search and sorting by latest launch, oldest launch, mission name or mission duration. The result count updates as the user changes filters. A CSS-based bar chart summarizes mission counts by destination. A mobile navigation control also changes its visible state and exposes that state through `aria-expanded`.

## 5. Responsive Design

The interface uses CSS Grid, flexible sizing and media queries to adapt from large desktop displays to narrow mobile screens. The statistics and insight panels collapse appropriately, controls become a single-column layout on smaller screens, and the wide data table remains usable through horizontal scrolling rather than forcing the page itself to overflow.

## 6. Accessibility Improvements

Accessibility was treated as part of the application design. The project includes a skip link, semantic headings and sections, native buttons, links, form controls and a real HTML table with column headers. All interactive controls have visible keyboard focus states. Dynamic result and data-loading messages use live status regions so important updates can be announced by assistive technologies. The mobile menu communicates its expanded/collapsed state with `aria-expanded`. The project also includes `prefers-reduced-motion` support to reduce non-essential animation for users who request less motion.

## 7. Performance Enhancements

The application was intentionally kept lightweight. JavaScript is loaded with `defer`, there are no external charting libraries or large image assets, and the visualization is produced with HTML and CSS. The static JSON file keeps the data small and separate from the document. DOM updates are limited to the table and chart areas that actually change. The design also avoids unnecessary dependencies, which reduces network requests and JavaScript execution compared with using a large UI or chart framework for the same functionality.

## 8. Testing

The dashboard was reviewed for desktop and mobile responsive behaviour, filter and search interactions, sorting, data loading, empty filter results, keyboard navigation, focus visibility, mobile menu state, reduced-motion behaviour and JSON error handling. The application should be served through a local HTTP server or GitHub Pages because browsers restrict `fetch()` requests to local JSON files when a page is opened directly with the `file://` protocol.

## 9. Challenges Encountered

The main challenge was integrating dynamic data without making the application unnecessarily complex. A third-party chart library could have provided more chart types, but it would also add dependency weight for a simple visualization. A custom CSS bar chart was therefore selected. Another consideration was preserving the accessibility and performance standards established in earlier Astra Atlas weeks while introducing more JavaScript-driven behaviour.

## 10. Conclusion

The Week 5 Mission Control Dashboard demonstrates the integration of responsive design, JavaScript interactivity, JSON data handling, accessibility and performance optimization in a single mini web application. It provides a practical progression from the earlier Astra Atlas landing page into a usable data dashboard. The final application is organized, responsive, dependency-light and designed to be understandable for both users and future developers.
