# Ticket Category Taxonomy

## Purpose

Consistent categorization is essential for accurate trend analysis. This document defines how incoming tickets are classified and how ambiguous cases are handled.

---

## Primary Categories

### Hardware
Any issue rooted in a physical device malfunction or failure.

| Subcategory | Examples |
|-------------|---------|
| Printer | Paper jams, offline printers, driver errors preventing print jobs |
| Monitor Display | Blank screen, resolution issues, display flickering |
| Peripheral (Mouse/Keyboard) | Unresponsive input devices, USB not recognized |
| Workstation Won't Boot | No POST, stuck on startup, blue screen on login |

### Software
Any issue with an installed application, license, or browser-based tool.

| Subcategory | Examples |
|-------------|---------|
| Application Crash | Unexpected closes, freezing mid-use (e.g., Office, SPSS, AutoCAD) |
| License Error | License server unreachable, activation expired, seat limit reached |
| Browser/Plugin | Extension conflicts, Java/Flash plugin issues, site won't load |
| Software Installation | Student needs software installed, missing from lab image |

### Network
Issues related to connectivity — wired or wireless.

| Subcategory | Examples |
|-------------|---------|
| Wi-Fi Connectivity | Cannot connect to campus Wi-Fi, drops repeatedly |
| Slow Connection | Streaming/downloading extremely slow, timeouts in browser |

### Account/Access
Issues with authentication, credentials, or file system permissions.

| Subcategory | Examples |
|-------------|---------|
| Password Reset | Locked out of singleSignOn, forgot password, expired credentials |
| Network Drive Access | Cannot map network drive, permission denied on shared folder |

---

## Classification Rules

1. **Hardware vs. Software:** If the issue involves a specific application and the physical device is functioning, classify as Software. If the device itself is not working (even if it triggers a software error), classify as Hardware.

2. **Network vs. Software:** If the issue is site-specific or app-specific, classify as Software (Browser/Plugin). If the machine cannot reach any resource, classify as Network.

3. **Escalation flag:** Tickets assigned to "Escalated" are those that required Tier 2 or IT supervisor involvement. These are not a separate category — escalation is tracked in the `assigned_to` field.

4. **Ambiguous tickets:** When initial classification is uncertain, default to the category of the first reported symptom. A note is added in the ticket log.
