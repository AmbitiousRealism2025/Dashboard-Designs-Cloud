# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a dashboard design tournament project where multiple AI design agents create competing single-file HTML dashboard demos across 8 distinct visual themes. The project structure is designed for rapid scenario-based dashboard creation using pure HTML/CSS with minimal JavaScript.

## Architecture

### Directory Structure

The project uses a flat folder structure with 8 theme-specific directories at the root:

```
Dashboard-Design-Info/          # Core documentation and specifications
├── 01-dashboard-structure-and-elements.md
├── 02-dashboard-html-template-example.md
├── 03-dashboard-variant-themes.md
└── starter-prompt.md

1-executive-boardroom/          # Theme folders (8 total)
2-modern-startup-pitch/
3-minimalist-analytical/
4-dark-ops-command-center/
5-financial-analyst-cfo-mode/
6-customer-journey-cx-studio/
7-project-portfolio-kanban-overview/
8-workshop-discovery-session-dashboard/
```

Each theme folder is designed to contain 5 HTML files (one per design agent):
- `explorer.html` - Experimental systems UX specialist
- `darno.html` - Data-first analytical UX specialist
- `teeqa.html` - Playful product UI specialist
- `zeeqa.html` - Minimalist aesthetic specialist
- `atlas.html` - Operational command & multi-stakeholder UX specialist

### Design System Philosophy

**Single-File Architecture**: All dashboards are self-contained HTML files with inline `<style>` and `<script>` blocks. No external dependencies, build tools, or frameworks are used.

**Common Layout Skeleton**:
- `<header>` - Global brand + page context + actions
- `<aside>` - Navigation/filters sidebar
- `<main>` - Dashboard content (KPIs, charts, tables, insights)
- `<footer>` - Metadata and timestamps

**Core Components** (reusable across all themes):
1. KPI/Metric cards with value, delta, sparkline, status
2. Chart/visual placeholders with CSS-only effects
3. Data tables with sorting UI and status pills
4. Filter & control components
5. Insight/narrative blocks
6. Alert/status banners

## Theme Specifications

The `Dashboard-Design-Info/03-dashboard-variant-themes.md` file is the **canonical source** for all theme requirements. Each theme has specific:

- **Vibe & Use Case** - Target audience and scenario
- **Color Palette** - Background, accent, semantic colors
- **Typography** - Font families and sizing approach
- **Visual Treatments** - Shadows, borders, gradients, effects
- **Layout Emphasis** - Which sections to prioritize
- **Microanimations** - Hover states, transitions, subtle motion

### Theme Summary

1. **Executive Boardroom** - Sober, C-suite ready, minimal flash
2. **Modern Startup Pitch** - Energetic SaaS aesthetic, gradient-forward
3. **Minimalist Analytical** - Grayscale + single accent, ultra clean
4. **Dark Ops Command Center** - Dark with glowing accents, monitoring-focused
5. **Financial Analyst/CFO Mode** - Institutional, tabular, numeric rigor
6. **Customer Journey/CX Studio** - Warm, human-centric, lifecycle-based
7. **Project Portfolio/Kanban** - Card metaphors, project status emphasis
8. **Workshop/Discovery Session** - Sticky-note aesthetic, facilitation-first

## Design Agent Personas

When generating dashboards, maintain these distinct design signatures:

- **Explorer** - Risk-tolerant, bold compositions, experimental layouts
- **Darno** - Precision-focused, dense data, executive readability
- **Teeqa** - Brand-forward, vibrant colors, polished SaaS feel
- **Zeeqa** - Reduction-focused, whitespace, typographic discipline
- **Atlas** - Complex status layouts, multi-role perspectives, ops-ready

## Development Guidelines

### HTML File Requirements

Every generated HTML file must include:

```html
<!-- Agent: [AgentName] | Theme: [ThemeName] | Intent: [One-sentence design intent] -->
```

The agent name must be visibly displayed in the UI (header/footer) for easy identification during review.

### CSS Patterns

- Use CSS custom properties (`--variable-name`) for color systems and spacing
- Include global transition rule: `* { transition: all 0.2s ease-out; }`
- Implement responsive breakpoints at 960px and 640px
- Use CSS Grid for main layout, Flexbox for component-level alignment

### Microanimations

Keep all animations subtle and performant:
- Hover: `transform: translateY(-2px)` with shadow increase
- Sparklines: CSS keyframe shimmer effects
- Alerts: Pulsing dots with `@keyframes pulse`
- Transitions: 0.18s - 0.2s duration, ease-out timing

### Component Patterns

**KPI Card Structure**:
```
.kpi-label (descriptive text)
.kpi-value (large number)
.kpi-delta (percentage change with color coding)
.kpi-meta (supporting context)
.sparkline (visual trend indicator)
```

**Chart Placeholder**:
Uses CSS gradients and borders to suggest visualization without requiring charting libraries. Includes gridlines and trend shapes created purely with CSS.

**Status Pills**:
Color-coded with semantic meanings:
- Green (`--success`) - On track, completed, OK
- Amber/Orange (`--warn`) - At risk, needs attention
- Red (`--danger`) - Critical, blocked, failed

## Working with This Repository

### Reading Documentation First

Before creating any dashboard variants:
1. Read `Dashboard-Design-Info/03-dashboard-variant-themes.md` for theme specs
2. Review `Dashboard-Design-Info/01-dashboard-structure-and-elements.md` for layout patterns
3. Reference `Dashboard-Design-Info/02-dashboard-html-template-example.md` as baseline

### File Naming Convention

- Theme folders use numeric prefixes: `1-`, `2-`, etc.
- HTML files use lowercase agent names: `explorer.html`, `darno.html`, etc.
- No spaces, no special characters in filenames

### Quality Standards

All dashboards must demonstrate:
- Valid HTML5 structure with semantic elements
- Responsive layout (works on laptop + tablet minimum)
- Clear visual hierarchy (context → KPIs → trends → details)
- Theme-accurate color palette and typography
- At least 2-3 chart placeholders and 1 data table
- Light tasteful microinteractions via CSS or simple JS

### Competition Framework

Dashboards are evaluated on:
1. **Visual coherence** with defined theme specifications
2. **UX clarity** and information hierarchy
3. **Realism** of layout and data representation
4. **Code quality** - clean, maintainable HTML/CSS
5. **Distinctiveness** - recognizable agent design signature across all 8 themes

## Common Use Cases

**Generating a New Dashboard**:
1. Identify target theme (1-8)
2. Select appropriate design agent persona
3. Apply theme specifications from `03-dashboard-variant-themes.md`
4. Use base layout from template example
5. Adapt colors, typography, and components to match theme
6. Save to correct theme folder with agent-name.html

**Comparing Designs**:
Open all 5 agent files from a single theme folder side-by-side to evaluate which best captures the theme requirements while maintaining the agent's signature style.

**Adapting for Business Scenarios**:
The template is designed to be flexible - swap KPI labels, chart types, and table data to match different business contexts (sales, ops, finance, marketing) without changing the core structure.

## Project Status & History

### Current State: First Round Only

**Note (2025-11-09):** Repository has been reverted to the first round of designs due to some agents not following instructions in the second iteration. A second attempt is currently being worked on in the cloud. This repository contains only the original 40 HTML files (5 agents × 8 themes) until the revised second round is completed and approved.

**Revert Details:**
- Reverted from commit `4b3f34a` back to `40e574c`
- Removed all `*2.html` files that did not meet quality standards
- Maintaining first-round designs as the current tournament baseline
- Second-round designs in progress with improved instruction adherence

## Notes

- This is a static HTML demonstration project, not a production application
- No build process, package managers, or external dependencies required
- Charts are CSS placeholders - can be replaced with Chart.js, ECharts, etc. in real implementations
- Focus is on visual design and UX hierarchy, not live data integration
