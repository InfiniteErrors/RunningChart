# CLAUDE.md

## Project Overview

RunningChart is a Vue 3 web application — a pace chart calculator that helps runners find race finish times for 5K, 10K, Half Marathon, and Full Marathon distances. It supports kilometres and miles, Track Mode (400m splits), and Dreadmill Mode (speed in KPH/MPH).

## Tech Stack

- **Framework:** Vue 3 (Options API) — single production dependency
- **Build Tool:** Vite 5
- **Linting:** ESLint 8 + Prettier 3 with `eslint-plugin-vue`
- **No test framework configured**

## Commands

- `npm run dev` — Start development server
- `npm run build` — Production build
- `npm run preview` — Preview production build
- `npm run lint` — Run ESLint with auto-fix on `.vue` and `.js` files

## Project Structure

```
src/
├── main.js              # App entry point
├── App.vue              # Root component (mode toggles)
├── components/
│   ├── Chart.vue        # Pace grid wrapper
│   ├── km.vue           # Grid layout + unit selector (km/miles)
│   ├── kmPace.vue       # Kilometre pace row
│   └── milePace.vue     # Mile pace row
└── assets/
    └── pace2.svg
```

Component hierarchy: `App → Chart → km → kmPace / milePace`

## Code Conventions

- **Vue style:** Options API (`data()`, `methods`, `computed`, `props`)
- **Component names:** PascalCase for multi-word (`Chart.vue`), lowercase allowed for single-word (`km.vue`) — `vue/multi-word-component-names` rule is disabled
- **Props/methods/variables:** camelCase
- **CSS classes:** kebab-case
- **Styling:** Global (unscoped) `<style>` blocks, CSS Grid + Flexbox, responsive breakpoints at 600px, 500px, 445px, 360px
- **State management:** Local component `data()` only — no Vuex/Pinia
- **Data flow:** Props down, no event emission back up
- **Path alias:** `@` maps to `./src`

## Vue Best Practices

- **SFC order:** `<template>`, then `<script>`, then `<style>` — keep this order in all components
- **Directive shorthands:** Prefer `@click` over `v-on:click` and `:prop` over `v-bind:prop` — be consistent (some files still use the long form)
- **Props typing:** Use constructor types (`Boolean`, `Number`, `String`). Add `required: true` or `default` values when the component can't function without a prop
- **Computed over methods for derived state:** Use `computed` for values derived from reactive data (see `colClass` in `km.vue`). Use `methods` only when the logic needs arguments or triggers side effects
- **Use `const`/`let` instead of `var`** in all new code
- **Shared logic:** `kmPace.vue` and `milePace.vue` contain duplicate methods (`convertPace`, `convertTime`, `convertTime5k`, `toggleActive`) and identical styles — extract shared helpers if adding more duplication
- **`v-for` keys:** Always provide a unique `:key` — current usage of the `pace` value is correct since each pace is unique in the range
- **Keep templates simple:** Move complex expressions into `computed` properties or methods rather than inlining in the template
- **One-way data flow:** Props go down only. If a child needs to communicate up, use `$emit` and declare events in an `emits` option

## Key Colors

- Primary: `#FFC700` (golden yellow — normal mode)
- Track mode: `#FF1493` (deep pink)
- Dreadmill mode: `#00b4d8` (cyan)
- Dark mode background: `#1a1a2e`
