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

## Key Colors

- Primary: `#FFC700` (golden yellow — normal mode)
- Track mode: `#FF1493` (deep pink)
- Dreadmill mode: `#00b4d8` (cyan)
- Dark mode background: `#1a1a2e`
