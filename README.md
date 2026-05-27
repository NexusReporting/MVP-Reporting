# Project Nexus

**Measurement Dashboard** for a VMware migration demand generation program.

Single-file HTML dashboard hosted on GitHub Pages. No build step, no dependencies, no server. Update the JSON data block, push to main, and the live dashboard reflects the changes.

## Live URL

`https://nexusreporting.github.io/Nexus/`

Password protected. Contact the project lead for access.

## What it does

Tracks the full lifecycle of a demand generation pilot: lead sourcing through content syndication, marketing automation and qualification, AI outbound calling, and partner opportunity delivery. Designed for a mixed audience of program operators, functional leadership, and external stakeholders.

**11 tabs covering:**

- **Summary** / KPI tiles, weekly volume trend, pickup rate, open measurement gaps
- **Targets and Pace** / Quarterly PO burndown, velocity tracking, pipeline feed vs target, revenue model
- **Funnel and Age** / Lifecycle stage counts, stage dwell time, attrition rates, qualification gates
- **AI Calls (NLPearl)** / Attempt and connect volume, pickup rate, call signal distribution, SLA compliance, industry benchmarks
- **Campaign Reporting** / Audience intelligence across job function, revenue size, employee count, industry, VM environment size, migration timeline, migration drivers, decision role, geographic distribution, campaign pacing
- **Email** / Consent and link testing status, industry benchmarks (pre-launch)
- **Web** / Adobe Analytics tagging status, implementation checklist, industry benchmarks (pre-launch)
- **Improvement Plan** / Governance cadence overview and CIP structure
- **Lead Scoring** / Eloqua fit vs activity scoring matrix, weight configuration, decay rules
- **Metric Register** / Full catalog of program metrics with MET IDs, calculations, sources, and priority tiers
- **Glossary** / Searchable reference for all program terms, acronyms, systems, and key metrics

## Features

- **Password gate** / Client-side prompt on page load. Session-persisted so refresh does not re-prompt.
- **Light and dark theme** / Toggle in the topbar. Defaults to light.
- **Edit mode** / Click Edit Mode to make data fields editable inline. All changes are tracked in a changelog. Save and Export downloads a new versioned HTML file with updated data baked in.
- **Collapsible insight notes** / 23 analyst notes throughout the dashboard, collapsed by default with a toggle to expand. Hidden entirely on mobile.
- **Chart tooltips** / Hover any canvas chart to see exact data point values.
- **Print support** / Print Tab button in the footer. Print stylesheet hides navigation and expands the active tab to full page width. Notes auto-expand in print view.
- **Mobile responsive** / Hamburger nav, single-column reflow, and adaptive typography below 768px. Further compacted at 480px.
- **Persistent data footer** / Fixed bar at the bottom showing the data-as-of date, version number, and print button.
- **Search** / Topbar search filters sidebar navigation by keyword match across all tabs.
- **Glossary search** / Dedicated search within the glossary tab for fast term lookup.

## How to update data

All dashboard data lives in a single JSON block inside `index.html`. Search for `NEXUS DASHBOARD - DATA BLOCK` to find it.

The block is split into named sections: `meta`, `funnel`, `targets`, `calls`, `campaign`, `gaps`, `chart_trend`, `chart_pickup`, and `chart_age`. Each field is annotated with its source system and where it renders.

**Weekly update process:**

1. Open `index.html` in any text editor
2. Update the values in the JSON block
3. Commit and push to `main`
4. GitHub Pages redeploys automatically (usually under 2 minutes)

Alternatively, use Edit Mode in the live dashboard to update fields visually, then Save and Export to download the updated file.

## Architecture

Single self-contained HTML file. No external JS libraries. No build tooling.

- **CSS custom properties** for theming (light/dark token swap on `[data-theme]`)
- **Vanilla JS** for navigation, chart rendering, search, edit mode, and tooltips
- **Canvas 2D** for all charts (trend, pickup, age, calls, burndown, velocity, cumulative, VM size, timeline, states)
- **Google Fonts CDN** for DM Sans, DM Mono, and Bebas Neue (the only external dependency)

## File structure

```
index.html    # Dashboard (single file, everything included)
README.md     # This file
```

## Requirements

A modern browser. Chrome, Firefox, Safari, or Edge. No IE support.

GitHub Pages configured to deploy from `main` branch, root directory.
