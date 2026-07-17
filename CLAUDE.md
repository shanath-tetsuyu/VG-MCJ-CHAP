# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

Static HTML/CSS/JS **UI prototypes** for the MicroJobber (MJ) portal — a volunteer job management system for Active Ageing Centres (AAC) and Senior Care Centres (SCC) in Singapore. These prototypes are the source of truth for design decisions before the production React app is built.

**Domain glossary:**
- **MJ / MicroJobber** — a trained volunteer who takes on jobs (chaperone, befriending, home assessment, centre assistant)
- **AAC** — Active Ageing Centre (admin side; uses the portal)
- **SCC** — Senior Care Centre (initiates jobs for their elderly clients)
- **C4Me** — the mobile app used by MJs to grab and check in to jobs
- **CARES** — legacy system that SCC staff use; integrates with the MJ API

## Running / Viewing

No build step. Open any HTML file directly in a browser, or serve the repo statically:

Live hosted versions follow the pattern:
```
https://shanath-tetsuyu.github.io/VG-MCJ-CHAP/v1/
https://shanath-tetsuyu.github.io/VG-MCJ-CHAP/v2/
https://shanath-tetsuyu.github.io/VG-MCJ-CHAP/v3/portal/index.html
```

## Active Version

**`v3/portal/`** is the current working prototype. `v1/` and `v2/` are historical iterations — do not edit them. When the user says "the portal", they mean `v3/portal/`.

## External Dependencies (CDN only — no npm)

All libraries are loaded from CDN. Do not add `package.json` or install anything:

| Library | Version | Used for |
|---|---|---|
| Bootstrap | 5.3.3 | Layout utilities, buttons |
| Bootstrap Icons | 1.11.3 | All icons (`bi-*`) |
| jQuery | 3.7.0 | DataTables requirement |
| DataTables | 1.13.7 | Job listing table in `index.html` |
| DM Sans | (Google Fonts) | Typography |

## Page Architecture

Every portal page shares the same shell:

```
#wrapper (flex row)
├── #sidebar  — purple nav (220px, collapsible)
└── #page-content (flex column)
    ├── .topbar  — 48px top bar with sidebar toggle + title
    └── .main
        └── .layout (flex row)
            ├── .left-scroll  — scrollable main content area
            └── .right-panel  — 290–316px fixed right panel (not on all pages)
```

The sidebar toggle collapses the sidebar by toggling `.sidebar-collapsed` on `#sidebar`.

## Shared CSS — `v3/portal/index.css`

All pages in `v3/portal/` link to `../portal/index.css`. This file owns:
- CSS custom property tokens (the full colour palette)
- Sidebar, sidebar-nav, sidebar-link, sidebar-sublink styles
- Topbar shell

**Do not redefine tokens or sidebar styles inline** — reference them via `var(--token)`. Each page has its own `<style>` block only for page-specific components.

### Design Tokens

```css
/* Greens */  --g / --gm / --gl / --gb
/* Amber */   --am / --al / --ab
/* Red */     --rm / --rl / --rb
/* Blue */    --bm / --bl / --bb
/* Purple */  --pm / --pl / --pb   ← brand primary (sidebar, buttons)
/* Ink */     --ink / --ink2 / --ink3 / --ink4
/* Surface */ --s (white) / --bg (off-white) / --bdr / --bdr2
/* Radius */  --r (10px) / --rl2 (16px)
```

Colour naming convention: `m` = midtone (text), `l` = light (background fill), `b` = border.

## Mock Data Pattern

There is no backend. All data lives in inline `<script>` blocks as JS arrays/objects at the top of each page:

- `JOB_DATA[]` — job listings (`index.html`, `job_detail.html`)
- `WAITLIST_DATA{}` — waitlist entries keyed by job ID
- `AP_DATA[]` — accounts payable records (`finance.html`)
- `MJ_DATA[]` — MJ profiles (`v1_mj_listing.html`, `proto2_v3_mj_profile.html`)

When adding new pages that need related data (e.g. a job detail page), duplicate the relevant mock arrays into the new page rather than importing across pages.

## Page Inventory (`v3/portal/`)

| File | Purpose |
|---|---|
| `index.html` | Dashboard — KPI cards, job listing table with DataTables, manage-assignment modal |
| `proto1_v3_publish.html` | Publish new job form |
| `proto2_v3_mj_profile.html` | Individual MJ profile |
| `v1_mj_listing.html` | MJ registry list |
| `v1_aic_report.html` | AIC operational report |
| `finance.html` | AP listing, payment breakdown modal |
| `attendance.html` | Attendance tracking |
| `settings.html` | Fee tables, business rules |
| `job_detail.html` | Full job detail view (URL param `?id=MJ-2026-xxx`) |

## Business Logic in Prototypes

Key logic already implemented in JS (replicate faithfully in the React app):

**Billable hours rounding** (`finance.html` → `calcBillableHours`):
- Minimum 1 hour always applies (including no-shows)
- First hour: always billed as 1 hr
- After first hour: remainder ≥ 30 min rounds up to next full hour; < 30 min stays

**Job status flow**: `Open → Taken → In Progress → Completed` or `Open → At Risk → Cancelled`; `Re-opened` when an assigned MJ cancels

**Home Assessment** jobs require 2 confirmed MJs (not 1); confirmed MJ names are visible to all eligible MJs on the C4Me listing

## Coding Rules
Do not use emojis
