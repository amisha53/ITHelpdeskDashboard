# KPI Calculations — IT Help Desk Dashboard

## Overview

All KPIs are calculated in Excel using pivot tables, AVERAGEIFS, COUNTIFS, and named ranges. This document describes the logic behind each metric.

---

## KPI Definitions

### 1. Resolution Rate

**Definition:** Percentage of tickets resolved within the same shift (SLA target: under 60 minutes, not escalated)

**Excel Formula:**
```
= COUNTIFS(assigned_to, "Lab Assistant", status, "Closed", resolution_time_min, "<60") 
  / COUNTIFS(status, "Closed")
```

**Dashboard Threshold:**
- Green: >= 85%
- Yellow: 70–84%
- Red: < 70%

---

### 2. Average Handle Time (AHT)

**Definition:** Mean resolution time in minutes across all closed tickets for a given period

**Excel Formula:**
```
= AVERAGEIF(status, "Closed", resolution_time_min)
```

**Segment variants:**
- `AHT by Category`: AVERAGEIFS filtered on `category`
- `AHT by Semester`: AVERAGEIFS filtered on `semester`
- `AHT Escalated vs. Non-Escalated`: AVERAGEIFS filtered on `assigned_to`

---

### 3. Reopen Rate

**Definition:** Percentage of closed tickets that were reopened within 48 hours

**Excel Formula:**
```
= COUNTIF(reopened, TRUE) / COUNTIF(status, "Closed")
```

**Dashboard Threshold:**
- Green: < 5%
- Yellow: 5–10%
- Red: > 10%

---

### 4. Ticket Volume by Week

**Definition:** Total tickets submitted per ISO week number, used for trend line chart

**Approach:** Added a helper column `=WEEKNUM(submitted_date, 2)` then built a pivot table grouping by week and semester.

**Chart type:** Line chart with separate series per semester, linear trend line added via Excel chart options.

---

### 5. Category Breakdown

**Definition:** Distribution of tickets across Hardware, Software, Network, Account/Access

**Approach:** Pivot table with `category` as Row and COUNT of `ticket_id` as Value. Displayed as donut chart on dashboard with percentage labels.

**Semester filter:** Slicer connected to all pivot tables allows supervisor to toggle between semesters or view combined.

---

### 6. Peak Hours

**Definition:** Hour-of-day distribution (0–23) of ticket submissions

**Approach:**
- Helper column: `=HOUR(submitted_time)` to extract integer hour
- Pivot table: Row = hour, Value = COUNT of ticket_id
- Chart: Bar chart showing volume by hour, sorted 8 AM to 10 PM (lab operating hours)

---

## Semester Comparison Logic

To compare Fall 2023 vs. Spring 2024 side by side:
- All pivot tables include `semester` as a secondary row or column grouping
- A slicer on `semester` is connected to all pivot tables for one-click filtering
- Delta columns calculated as: `= Spring_value - Fall_value` with conditional formatting

---

## Conditional Formatting Rules

Applied to KPI summary cells using custom rules (Home > Conditional Formatting > New Rule):

| KPI | Red | Yellow | Green |
|-----|-----|--------|-------|
| Resolution Rate | < 0.70 | 0.70–0.84 | >= 0.85 |
| Avg Handle Time | > 60 min | 45–60 min | < 45 min |
| Reopen Rate | > 0.10 | 0.05–0.10 | < 0.05 |
| Escalation Rate | > 0.20 | 0.10–0.20 | < 0.10 |
