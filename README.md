# INFO-380 DFMS Project

**Drone Fault Management System (DFMS)** — Mission control prototype for wind-turbine inspection operations.

## Quick start

Open the interactive prototype in a browser:

```bash
open dfms_dashboard_v2.html
```

## Deliverables

| File | Purpose |
|------|---------|
| `dfms_dashboard_v2.html` | Clickable high-fidelity prototype (Ops Manager role) |
| `DESIGN_NOTES.md` | Per-screen design documentation for INFO-380 assignment |

## Primary role

All screens use the **Ops Manager** persona. Maintenance receives faults via handoff only; no separate maintenance UI in this prototype.

## User stories

| ID | Title |
|----|-------|
| US-01 | Monitor mission control dashboard |
| US-02 | View and filter drone fleet |
| US-03 | Recommend optimal drone for dispatch |
| US-04 | Dispatch drone to turbine / mission |
| US-05 | Monitor turbines and health |
| US-06 | Review and route open faults |
| US-07 | Manage mission lifecycle |
| US-08 | Abort in-progress mission with audit trail |
| US-09 | Configure alerts and dispatch rules |

See `DESIGN_NOTES.md` for per-screen task, data, actions, and error-prevention detail.
