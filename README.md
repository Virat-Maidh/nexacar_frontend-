# Frontend Assignment — "Engineered for Passion" (Interactive Prototype)

A pixel-close, **interactive** recreation of the provided Figma prototype (car showcase /
performance page), built with **Next.js (App Router) + TypeScript + Tailwind CSS**, including
light/dark theming and animated left/right navigation that swaps the center content — matching
the two prototype states shown (Home view and Performance/Stats view).

> The original brand logo/photography from the Figma file were not reused verbatim — the
> wordmark was rebuilt generically ("NEXTCAR — DRIVE NEXT") and the car photography was
> replaced with original flat illustrations, since third-party brand assets and photos can't
> be redistributed. Layout, spacing, colors, typography, iconography, and interaction/motion
> follow the reference closely.

## What's interactive

- **Left rail** (3 circular buttons):
  - **Gauge icon** → swaps the center circle to the **Performance/Stats view**
    (352 Top Speed, 3.2 Sec 0-100, 620 HP, 2,450 KM Oil Change, 780 Torque, 520 KM Range),
    matching the second reference screenshot.
  - **Home icon** (default active) → shows the **Home view** with a "Click for Home" tooltip,
    matching the first reference screenshot.
  - **Rupee icon** → shows a simple pricing callout.
  - Clicking an item highlights it in red, shows its tooltip beside it, and cross-fades the
    center content.
- **Right rail** (3 circular buttons): Chat, Documents (shows an **"Explore timeline"**
  tooltip, as in the reference), and License — each toggles its own tooltip independently of
  the left rail.
- **Top bar**: back button, download/share/confirm action icons, and a light/dark toggle
  (persisted to `localStorage`).
- **Bottom lap timeline**: wavy dashed path with LAP 01–05 markers; LAP 03 ("Technical
  Section") is the active/highlighted step, matching the reference.

## Tech Stack

- **Next.js 14** (App Router)
- **React 18** + TypeScript
- **Tailwind CSS** (utility-first styling, `darkMode: 'class'`)
- Inline SVG icons and illustrations (no external icon/image dependency)
- Tailwind keyframe animations for entrance motion, tooltip pop-ins, and cross-fading the
  center stage between views

## How to Run

```bash
cd frontend
npm install
npm run dev
```

Open http://localhost:3000.

Production build:

```bash
npm run build
npm start
```

## Project Structure

```
src/
  app/
    layout.tsx        # root layout, Google Fonts
    page.tsx           # page composition + interaction state
    globals.css         # Tailwind directives + base styles
  components/
    Logo.tsx               # wordmark + generic car outline icon
    BackgroundRings.tsx      # concentric ring / starfield backdrop
    Hero.tsx                  # "ENGINEERED FOR PASSION" headline
    SpotlightBeam.tsx          # vertical light-cone above the center circle
    HomeScene.tsx                # rooftop illustration (Home view)
    StatsScene.tsx                 # garage illustration (Stats view)
    CenterStage.tsx                  # circular stage, swaps views + stat callouts
    SideNav.tsx                        # left/right circular nav with tooltips
    ThemeToggle.tsx                      # light/dark pill toggle
    LapJourney.tsx                        # bottom wavy lap timeline (LAP 01–05)
    icons.tsx                              # inline SVG icon set
  hooks/
    useTheme.ts                             # theme state + localStorage persistence
```

## Responsiveness & Theming

- Fully responsive down to mobile; side navigation rails collapse below the `md` breakpoint
  so the layout stays usable on small screens, while the hero, center stage, and lap timeline
  reflow.
- Dark mode is the default (matching the reference) with light mode available via the
  top-right toggle; the choice persists across visits.

## Assumptions / Decisions

- The Figma prototype-viewer chrome (file name, "Finish update" bar, browser tabs, pagination)
  is not part of the actual page and was excluded.
- Real car photography from the Figma file was substituted with original illustrations for
  the same reason brand logos weren't copied — happy to wire in real photo assets (just drop
  images into `public/` and swap the `<HomeScene />` / `<StatsScene />` components for
  `<img>` tags) if licensed images are supplied.
- Right-rail buttons (Chat, Documents, License) show contextual tooltips on click since the
  reference didn't specify deeper destinations for them; Documents shows "Explore timeline"
  exactly as captured in the reference screenshot.
# nexacar_frontend-
# nexacar_frontend-
