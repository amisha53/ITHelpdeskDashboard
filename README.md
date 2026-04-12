# IT Help Desk Performance Dashboard

Semester-over-semester analysis of IT support tickets from SEMO computer labs. Built to help supervisors identify resolution bottlenecks and make staffing decisions.

## What it does

- Pulls ticket data from two semesters (Fall 2023, Spring 2024)
- Calculates KPIs: avg resolution time, first-contact resolution rate, ticket volume by category
- Generates trend lines and category breakdowns
- Outputs a formatted Excel dashboard used in weekly shift planning meetings

## Files

| File | Description |
|------|-------------|
| `data/tickets_fall2023.csv` | Raw ticket export, Fall 2023 |
| `data/tickets_spring2024.csv` | Raw ticket export, Spring 2024 |
| `dashboard_builder.py` | Cleans data, calculates KPIs, writes Excel output |
| `requirements.txt` | Python dependencies |

## How to run

```bash
pip install -r requirements.txt
python dashboard_builder.py
```

Output: `IT_Helpdesk_Dashboard.xlsx`

## KPIs tracked

- Avg resolution time (hrs) by category
- First-contact resolution rate
- Ticket volume by week
- Top 5 recurring issue types
- Technician workload distribution

## Background

Built during my time as a Computer Lab Assistant at SEMO's IT Department. Ticket data was anonymized and exported from our internal system. The dashboard is currently used by lab supervisors for shift scheduling.
