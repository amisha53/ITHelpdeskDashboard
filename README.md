# IT Help Desk Performance Dashboard

Semester-over-semester analysis of IT support ticket data from SEMO computer labs. Built to help supervisors identify resolution bottlenecks, track technician workload, and make staffing decisions.

## What it does

- Tracks 1,200+ tickets per semester across 5 lab locations
- KPI cards: total volume, avg resolution time, first-contact resolution rate, daily volume
- Ticket log with search/filter by category, status, and technician
- Timesheet view showing per-staff shift logs, hours worked, and ticket counts
- Trend charts: weekly volume, resolution time over the semester, day-of-week patterns
- Semester toggle to compare Fall 2023 vs Spring 2024

## Files

| File | Description |
|------|-------------|
| `dashboard.html` | Self-contained dashboard, no build step needed |
| `data/tickets_fall2023.csv` | Raw ticket export, Fall 2023 (anonymized) |
| `data/tickets_spring2024.csv` | Raw ticket export, Spring 2024 (anonymized) |
| `data/shifts_fall2023.csv` | Staff shift log, Fall 2023 |
| `data/shifts_spring2024.csv` | Staff shift log, Spring 2024 |

## How to run

Just open `dashboard.html` in a browser. No server or dependencies needed.

```bash
open dashboard.html
```

To host it:
- Drop `dashboard.html` into any static host (Netlify, GitHub Pages, etc.)
- Or serve locally: `python -m http.server 8000`

## KPIs tracked

- Total ticket volume by week and category
- Avg resolution time (hrs) by issue type
- First-contact resolution rate
- Technician workload distribution
- Top recurring issue types
- Lab location breakdown
- Day-of-week demand patterns

## Data notes

Student requester IDs are anonymized in the format `S0***XXX` per FERPA guidelines. Ticket data was exported from the SEMO IT ServiceDesk system at the end of each semester. All personal identifying information has been removed.

## Background

Built during my time as a Computer Lab Assistant in the IT Department at Southeast Missouri State University (Aug 2022 — May 2026). The dashboard was used by lab supervisors to review technician performance and plan shift coverage for the following semester.
