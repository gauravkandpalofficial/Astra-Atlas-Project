# Accessibility Report: Astra Atlas Final Website

## Audit summary

A manual WCAG-oriented review was applied to the final combined site. The review checked landmarks, heading hierarchy, keyboard operation, focus visibility, form labels, live feedback, link purpose, responsive reflow, motion preferences and the ARIA state of dynamic controls. Lighthouse or WAVE may also be run after opening `index.html` in a browser for automated confirmation.

## Improvements included

- A skip link moves focus directly to the single `main` landmark.
- Semantic `header`, `nav`, `main`, `section`, `article`, `form`, `dialog` and `footer` elements communicate the document structure.
- Native buttons and links are used for interaction. The mobile navigation exposes its state with `aria-expanded` and closes with Escape.
- Mission Explorer follows the tab pattern through `tablist`, `tab`, `tabpanel`, `aria-selected`, `aria-controls` and arrow-key navigation.
- Mission briefs use the native `dialog` element; focus returns to the opening button after the dialog closes. An in-page fallback appears if native dialog support is unavailable.
- Strong visible focus outlines are present for keyboard users. Text and controls have readable high-contrast colour combinations.
- The email form has a visible label, help text, required state and a polite live-region status message. Invalid input receives a clear message and focus returns to the field.
- The page reflows into a single column on small screens, and `prefers-reduced-motion` disables movement.

## Standards supported

These choices support WCAG 2.1/2.2 goals including semantic information structure (1.3.1), text contrast (1.4.3), reflow (1.4.10), keyboard operation (2.1.1), skip navigation (2.4.1), focus visibility (2.4.7), labels/instructions (3.3.2), status messages (4.1.3) and reduced motion (2.3.3).

## Test checklist

1. Tab through all controls and confirm the focus outline is always visible.
2. Use keyboard arrows, Home and End in the Mission Explorer.
3. Open and close every briefing dialog with keyboard and pointer controls.
4. Test the menu below 760px wide, including Escape to close it.
5. Submit the email form with invalid and valid values.
6. Enable a reduced-motion preference and reload the page.
