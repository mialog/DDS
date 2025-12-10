# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

DDS (Daekyo Design System) - A SCSS-based design system for responsive web layouts. This is a pure SCSS library with no build tools configured in the repository; compilation is handled externally.

## Architecture

### Entry Point
- `scss/common.scss` - Main entry file that imports all modules and defines global styles

### Directory Structure
```
scss/
├── common.scss          # Main entry, global resets, layout components (header, footer, sections)
├── _style.scss          # Page-specific styles and keyframe animations
├── abstracts/
│   ├── _variables.scss  # Design tokens: colors, spacing, typography, breakpoints
│   ├── _functions.scss  # Unit conversion: px(), rem(), vw()
│   └── mixins/
│       ├── _respond.scss    # Responsive breakpoint mixins
│       ├── _templete.scss   # Typography and radius mixins (responsive)
│       ├── _effect.scss     # Box shadow effects
│       └── _utils.scss      # Utility mixins (text-img, positioning, clearfix)
└── base/
    ├── _root.scss       # CSS custom properties generation
    ├── _fonts.scss      # @font-face definitions
    └── _normalize.scss  # Browser normalization
```

### Key Design Tokens (abstracts/_variables.scss)

**Breakpoints:**
- Mobile: 280px+
- Tablet: 768px+
- Desktop: 1025px+

**Color System:**
- Brand: `$brand-default` (#4169E1), `$brand-light`, `$brand-dark`, `$brand-point`
- Neutral scale: `$neutral-0` (white) through `$neutral-100` (near-black)
- Alpha variants: `$alpha-dark-*`, `$alpha-light-*`, `$alpha-brand-*`
- Semantic tokens: `$primary`, `$secondary`, `$tertiary`, `$text-*`

**Typography:**
- Primary font: Pretendard
- Font weights: 100-900 (use semantic names: `$font-weight-black`, `$font-weight-bold`, `$font-weight-medium`, `$font-weight-light`)

### Responsive Mixins (abstracts/mixins/_respond.scss)

```scss
@include respondToMin(mobile|tablet|desktop)   // min-width media query
@include respondToMax(mobile|tablet|desktop|min)  // max-width media query
@include respondToMinMax($min, $max)           // range media query
```

### Typography Mixins (abstracts/mixins/_templete.scss)

Responsive typography that scales across breakpoints:
```scss
@include font-display(large|medium|small)
@include font-header(large|medium|small|xsmall)
@include font-body(large|medium|small|xsmall)
@include font-action(large|medium|small)
@include text-header/text-title/text-body/text-label($size)  // non-responsive variants
@include template-radius(1-5|999)  // responsive border-radius
```

### Unit Functions (abstracts/_functions.scss)

```scss
px($size)   // returns #{$size}px
rem($size)  // returns #{$size / 10}rem (assumes 62.5% base font-size)
vw($target) // converts px to vw units
```

### Effect Mixins (abstracts/mixins/_effect.scss)

```scss
@include effect-small()      // subtle shadow
@include effect-big()        // prominent shadow
@include effect-floating()   // elevated element
@include effect-modal()      // modal shadow
@include effect-bottom-sheet()
@include effect-top()
```

## Conventions

- Use `@use` with namespaces (e.g., `@use "abstracts/variables" as *`)
- CSS custom properties are prefixed with `ds-` (configurable via `$variable-prefix`)
- Images are expected at `../images/` relative to compiled CSS
- Fonts are expected at `../fonts/` relative to compiled CSS
