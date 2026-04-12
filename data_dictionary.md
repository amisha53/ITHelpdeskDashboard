# Data Dictionary — IT Help Desk Ticket Data

## Source

Exported from SEMO IT Department lab management system. Data covers Fall 2023 (August–December) and Spring 2024 (January–May). All user-identifying fields were removed prior to export.

---

## Field Definitions

| Column | Type | Description |
|--------|------|-------------|
| `ticket_id` | String | Unique identifier for each support ticket (format: `T-XXXXX`) |
| `submitted_date` | Date (YYYY-MM-DD) | Date the ticket was opened |
| `submitted_time` | Time (HH:MM) | Time of day the ticket was submitted (24-hour format) |
| `category` | Categorical | High-level issue classification. Values: `Hardware`, `Software`, `Network`, `Account/Access` |
| `subcategory` | Categorical | Specific issue type within the category |
| `priority` | Categorical | Ticket urgency. Values: `Low`, `Medium`, `High` |
| `assigned_to` | Categorical | Who handled the ticket. Values: `Lab Assistant`, `Escalated` |
| `status` | Categorical | Final ticket state. All records in this export are `Closed` |
| `resolution_time_min` | Integer | Time in minutes from ticket open to close |
| `reopened` | Boolean | Whether the ticket was reopened within 48 hours of closing |
| `semester` | Categorical | Academic semester the ticket belongs to. Values: `Fall 2023`, `Spring 2024` |

---

## Category / Subcategory Mapping

| Category | Subcategories |
|----------|---------------|
| Hardware | Printer, Monitor Display, Peripheral (Mouse/Keyboard), Workstation Won't Boot |
| Software | Application Crash, License Error, Browser/Plugin, Software Installation |
| Network | Wi-Fi Connectivity, Slow Connection |
| Account/Access | Password Reset, Network Drive Access |

---

## Notes

- `resolution_time_min` for escalated tickets includes time spent waiting for Tier 2 response
- Tickets submitted and closed in the same session are the majority of `Lab Assistant` records
- `reopened = TRUE` tickets were counted once in volume but excluded from the initial resolution rate calculation, then tracked separately as a reopen rate KPI
