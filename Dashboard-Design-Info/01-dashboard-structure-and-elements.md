# Strategic Dashboard Design – Structure & Elements

This document summarizes the key structural and design elements of a flexible, single-file HTML dashboard that can be reused across different business scenarios.

---

## 1. Page-level structure

A flexible dashboard HTML file should assume:

- **Responsive layout**: works on laptop + tablet; mobile is simplified (collapsed sidebar, stacked cards).
- **Single-page app feel** (even if it’s static): sections swap, modals, filters update cards without full page reload (simple JS).
- **Clear hierarchy**: user sees (1) context, (2) key metrics, (3) trends, (4) details.

Base structure:

- `<header>`: global brand + page context  
- `<aside>`: navigation / filters  
- `<main>`: dashboard content (hero KPIs, charts, tables, details)  
- `<footer>`: metadata, last updated, small notes  

---

## 2. Core layout regions

### A. Top bar / header

Purpose: context + quick actions.

Elements to include:

- **Logo / Brand** (e.g., your consulting brand or client logo)
- **Dashboard title** (e.g., “Q4 Sales Performance Overview”)
- **Subheading / description** (one line: what this dashboard is for)
- **Date range selector** (even if static: “Jan 1–Mar 31, 2025” with calendar icon)
- **Profile / Persona area** (client name, product line, segment)
- **Key actions**:
  - Export (PDF, CSV – can be stubbed)
  - “Scenario” dropdown (e.g., Baseline / Optimistic / Conservative)
  - Theme toggle (light / dark)

### B. Left sidebar (primary navigation)

Even if the dashboard is one page, a sidebar helps mentally segment content:

- **Sections:**
  - Overview
  - Financials
  - Operations
  - Customers
  - Risks & Alerts
  - Notes / Action Items
- **Icons** for each item (for quick scanning)
- **Collapse button** (shrinks to icon-only on smaller screens)

You can reuse sidebar structure across use cases, just change labels.

### C. Main content layout

Common pattern: **Grid with three vertical zones**:

1. **Top: KPI strip**  
2. **Middle: Charts & key visuals**  
3. **Bottom: Tables, logs, text insights**  

Use a CSS grid like:

- Top row: 4 KPI cards  
- Middle: 2/3 width big chart + 1/3 supporting cards  
- Bottom: full-width table + side notes  

---

## 3. Essential components

### 1) KPI / Metric cards

These should be the first thing the eye hits.

Each card should have:

- Metric label (e.g., “Monthly Recurring Revenue”)
- Big value (e.g., `$125,430`)
- Delta badge (e.g., `+12.4% vs last month`)
- Small sparkline (tiny trend line)
- Status tag (e.g., “On Track”, “At Risk”)

You can define generic classes like `.kpi-card`, `.kpi-value`, `.kpi-delta`.

### 2) Charts / Visuals

Even if you don’t wire a real charting lib yet, plan for:

- **Primary chart** (line / bar / area)
- **Comparison chart** (e.g., segmented bar for product lines)
- **Heatmap or matrix** (e.g., performance by region vs segment)
- **Faux chart placeholders** (gradient background + SVG icons) for static templates

Later, you can swap in Chart.js, ECharts, etc.

### 3) Tables / Data grids

For business dashboards, tables are critical:

Include:

- Sorting UI (up/down caret icon even if static)
- Status chips in rows (e.g., “Pending”, “Completed”, “High Risk”)
- Pagination footer (Page 1 of 4, rows per page)
- A row highlighting rule (e.g., high-risk rows tinted)

Example use cases:

- Pipeline opportunities
- Top customers
- Project milestones
- Expense breakdowns

### 4) Filters & controls

Simple but powerful:

- Date range picker
- Dropdown(s) for:
  - Region / Segment / Department
  - Scenario (Baseline / Stretch / Worst-case)
- Toggle chips:
  - “Revenue | Profit | Cash Flow”
  - “All | New | Returning customers”

Filters can be purely visual in the template; JS wiring is optional per project.

### 5) Insight / narrative blocks

Because narrative is key in consulting, include a component such as **“Insights & Recommendations”**:

- Title: “Key Insights”
- Bullet list with **short, punchy statements**
- Highlight icons (💡, ⚠️, ✅) or pill tags for “Insight / Risk / Opportunity”
- A mini “Next Steps” box with 3 actions and owners

### 6) Alerts / status banners

At top of main content or above a table:

- Example: “3 critical issues require attention”
- Color-coded:
  - Red / amber / green
- Optional dismiss icon (X) for interactivity

### 7) Notes / comments area

A small panel for:

- Stakeholder comments
- Meeting notes
- Decisions made

---

## 4. Visual design system

You want something that feels professional but still “pops”.

### Color system

- **Neutral base**: off-white or dark grey background for the app chrome
- **Primary accent**: for key metrics and buttons (e.g., blue / teal / purple)
- **Semantic colors**: green (positive), red (negative), amber (warning)
- **Soft card backgrounds**: slightly elevated white / dark surfaces

### Typography

- Two-level type scale:
  - Larger, bold headings for sections and numbers
  - Clean sans serif for body text and labels

### Spacing & layout

- Consistent padding (e.g., 16px / 24px)
- Card grid: equal gaps, 12–24px
- Don’t cram charts; give them breathing room.

### Iconography

- Use a consistent icon pack (e.g., Feather / Heroicons SVG inline).
- Icons on:
  - Sidebar items
  - KPIs (small subtle icons)
  - Buttons (download, filter, refresh)

---

## 5. Microinteractions & motion

In a single HTML file with no heavy frameworks, focus on:

### Hover states

- **Cards**: slight lift, subtle shadow increase, small scale (`transform: translateY(-2px)`).
- **Buttons**: background color shift, maybe a tiny glow on primary actions.
- **Sidebar items**: background highlight, left border accent.

### Transitions

Global rule:

```css
* {
  transition: all 0.2s ease-out;
}
```

Then refine on specific components so it’s not overdone.

### “Live” details without real data

- Animating a small bar in the header that looks like loading (CSS-only keyframes).
- Pulsing badge for a new alert.
- Soft shimmering skeleton loader for chart placeholders if you want “data loading” vibe.

### Scroll interactions

- Sticky header that compresses slightly when you scroll (height shrinks, shadow increases).
- Section titles pinned so it’s clear which segment you’re in.

---

## 6. Data / content patterns for different business scenarios

Make the template flexible with **slot-like sections** you can rename:

### Financial dashboard

- KPIs: Revenue, Gross Margin, Net Profit, Cash Runway
- Charts: Revenue over time, Expense categories, Forecast vs actual

### Sales / CRM dashboard

- KPIs: New Leads, Opportunities, Win Rate, Avg Deal Size
- Charts: Funnel stages, Deals by rep, Pipeline over time

### Operations / Project dashboard

- KPIs: On-time delivery %, Open tasks, SLA breaches, Utilization
- Charts: Burndown, Capacity, Issue categories

### Marketing dashboard

- KPIs: Traffic, Conversion Rate, CAC, LTV
- Charts: Channel performance, Campaign lift

The HTML template stays the same; you swap labels and sample data per scenario.
