# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.4.0] - 2026-11-23

### Added

- **Date picker panel styling** — HubSpot's new `.hsfc-DatePickerField` calendar shipped unstyled. It now matches the form theme, meets WCAG AA contrast (text 4.5:1, borders and focus rings 3:1), and uses 40px+ targets (44px on touch). New `--color-hs-form-datepicker-*` and `--size-hs-form-datepicker-day` variables, listed in `theme-template.css`.
- **Date picker accessibility script** — `role="dialog"` and an accessible name on the panel; `aria-haspopup`, `aria-expanded` and `aria-controls` on the input; `aria-selected` on the chosen day and `aria-current="date"` on today. Tab and Shift+Tab cycle inside the open panel. Focus returns to the input after a date is chosen or Escape is pressed (it previously dropped to `<body>`). Alt+ArrowDown reopens a dismissed panel. The panel closes if focus leaves it by other means.
- **Reverse-form date picker** — on `.hs-form-reverse` forms the panel is dark with light text and an inverted selected day. New `--color-hs-form-reverse-datepicker-*` variables.

### Fixed

- **Date picker month changes** — react-day-picker kept the outgoing month in the DOM because its exit animation was never defined, which duplicated the month and year selects and the day grid in the Tab order. Short enter/exit animations now let it remove the old month; reduced-motion users get a 1ms duration so the removal still fires.

### Upgrade notes

- If you self-host the files (for example in the HubSpot file manager), upload `styles.css` and `index.cdn.js` together. The new JS depends on the new CSS for the month-change fix.
- Static assets served from a CDN or file manager are typically cached for days. Version the asset URLs (`styles.css?v=1.4.0`) so visitors pick up the change.

## [1.1.0] – [1.3.1]

Changes accumulated across the 1.1.0 through 1.3.1 releases. They were not itemised per release at the time, so they are grouped here.

### Added

- **Theme template file** (`theme-template.css`) — copy-ready file with all CSS variables organized by component, published with the package
- **CSS Variables Reference** in README with collapsible sections showing cascade relationships
- **`.nvmrc`** file specifying Node 24.14.1
- **CSS minification** via cssnano (~30% smaller CSS output)
- **Export for theme-template** — can now import via `@fahlgren-mortine/hubspot-form-usability-enhancements/theme-template`
- Documentation: `docs/DEVELOPMENT.md` — build process, local dev workflow, publishing guide
- Documentation: `docs/why-no-tailwind.md` — rationale for pure CSS approach

### Changed

- **Internal refactor**: Extracted shared logic to `src/core.js` for consistency between npm and CDN builds
- **Node requirement raised to ≥20** (from ≥18) due to @rollup/plugin-terser v1.0.0
- **@rollup/plugin-terser upgraded to v1.0.0** — fixes serialize-javascript vulnerability
- Replaced `concurrently` with `nodemon` for simpler dev watch mode
- Switched from Tailwind CSS to pure PostCSS with `postcss-nested` for CSS nesting
- Improved checkbox/radio error border styling
- Updated copilot-instructions to use function names instead of hardcoded line numbers

### Fixed

- **WCAG AA Compliance**: Progress bar elements now receive unique IDs to prevent duplicate ID violations
- **WCAG AA Compliance**: Primary color contrast ratio improved to 4.5:1 minimum for white text
- Removed stray `console.log()` in validation error handling
- Fixed incorrect `@theme` directive references in README (Tailwind v4 artifact)
- Fixed misleading environment variable documentation in examples.js
- Resolved all npm audit vulnerabilities (was 5, now 0)

### Removed

- Tailwind CSS dependency and all `@apply`/`@theme` usage
- `concurrently` dev dependency

## [1.0.1] - 2026-03-14

### Fixed

- CSS fixes for form field styling
- Minor style adjustments

## [1.0.0] - 2026-03-14

### Added

- Initial production release
- React hydration support with two-phase initialization
- WCAG 2.1 AA compliant validation
- Character limit validation with counter UI
- File upload validation (type and size)
- Dark background support via `.hs-form-reverse` class
- CSS custom properties system for theming
- TypeScript type definitions
- ESM and CommonJS dual builds

### Removed

- All Tailwind CSS references from documentation

## [0.1.0-alpha.1] - 2026-03-01

### Added

- Alpha release for testing
- Core form enhancement functionality
- Basic validation system

## [0.1.0-alpha.0] - 2026-02-15

### Added

- Initial alpha release
- Basic HubSpot form detection and enhancement
- Character limit enforcement

[Unreleased]: https://github.com/FahlgrenMortineDigital/hubspot-form-usability-enhancements/compare/v1.4.0...HEAD
[1.4.0]: https://github.com/FahlgrenMortineDigital/hubspot-form-usability-enhancements/compare/v1.3.1...v1.4.0
[1.0.1]: https://github.com/FahlgrenMortineDigital/hubspot-form-usability-enhancements/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/FahlgrenMortineDigital/hubspot-form-usability-enhancements/compare/v0.1.0-alpha.1...v1.0.0
[0.1.0-alpha.1]: https://github.com/FahlgrenMortineDigital/hubspot-form-usability-enhancements/compare/v0.1.0-alpha.0...v0.1.0-alpha.1
[0.1.0-alpha.0]: https://github.com/FahlgrenMortineDigital/hubspot-form-usability-enhancements/releases/tag/v0.1.0-alpha.0
