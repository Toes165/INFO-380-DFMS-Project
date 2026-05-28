# DFMS Design Notes (INFO-380)

Per-screen documentation for the **Ops Manager** prototype in `dfms_dashboard_v2.html`.

Each screen supports: task completion, clear data presentation, action hierarchy, and error prevention or recovery.

---

## US-01 — Mission Control Dashboard

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Monitor fleet health, faults, missions, and alerts; decide whether to recommend or dispatch |
| **User story** | **US-01** — Single mission-control view for system status and prioritized action |
| **Data shown** | KPIs, alerts, live map, recent missions, sync/handoff footer |
| **Data updated** | Filters and date range (session); navigation only |
| **Primary** | Recommend Drone |
| **Secondary** | Filters, View all, KPI drill-through |
| **Error prevention** | Severity colors; SLA column; weather alert before dispatch |

---

## US-02 — Drone Fleet (Fleet Overview)

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Review readiness; select drone for dispatch or detail |
| **User story** | **US-02** — See all drones and readiness |
| **Data shown** | ID, status, battery, location, sync; side panel |
| **Data updated** | Search, filters, selection |
| **Primary** | Dispatch (Available only) |
| **Secondary** | Recommend, View |
| **Error prevention** | Dispatch hidden unless Available; battery colors; site weather |

---

## US-03 — Recommend Drone (action)

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Get system recommendation for best available drone |
| **User story** | **US-03** — Recommend optimal drone before dispatch |
| **Data shown** | Recommendation toast (ID, site, battery) |
| **Data updated** | None (advisory only) |
| **Primary** | Recommend Drone (dashboard / fleet toolbar) |

---

## US-04 — Dispatch Mission (modal)

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Confirm dispatch after safety interlocks |
| **User story** | **US-04** — Dispatch with safety checks |
| **Data shown** | Mission summary; battery/weather/concurrent checklist |
| **Data updated** | Status → In Progress |
| **Primary** | Confirm Dispatch |
| **Secondary** | Cancel |
| **Error prevention** | Warning banner; dimmed confirm if weather bad; checklist pass/fail |

**Data-entry layout:** Read-only summary → Safety interlocks → Cancel | Confirm

---

## US-05 — Turbine Status

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Assess turbine health; dispatch inspection |
| **User story** | **US-05** — Turbine health at a glance |
| **Data shown** | ID, site, health, inspection date, fault count, assigned drone |
| **Data updated** | Filters; panel on row select |
| **Primary** | Dispatch |

---

## US-06 — Open Faults

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Triage faults; dispatch or hand off to maintenance |
| **User story** | **US-06** — Review and route open faults |
| **Data shown** | Turbine, severity, type, detected, status, assignee |
| **Data updated** | Filters; Create Fault Report → maintenance queue |
| **Primary** | Dispatch |
| **Secondary** | Review, Create Fault Report |

---

## US-07 — Mission Control (all missions)

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Track SLA; dispatch pending; abort in-progress |
| **User story** | **US-07** — Full mission lifecycle visibility |
| **Data shown** | Mission table; weather strip in panel |
| **Data updated** | Dispatch / abort flows |
| **Primary** | Dispatch |
| **Destructive** | Abort → US-08 modal |

---

## US-08 — Abort Mission (modal)

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | End mission with documented audit trail |
| **User story** | **US-08** — Abort with required reason and comment |
| **Data collected** | Abort reason (select); manager comment (textarea) |
| **Data updated** | Status → Aborted |
| **Primary** | Confirm Abort (destructive) |
| **Secondary** | Cancel |
| **Error prevention** | Required fields; error toasts; cancel = no change |

**Data-entry layout:** Reason → Comment → Cancel | Confirm Abort

---

## US-09 — System Settings

| | |
|---|---|
| **Role** | Ops Manager |
| **Task** | Configure sync, alerts, dispatch rules, display |
| **User story** | **US-09** — Tune control-room settings |
| **Data shown** | Toggles, intervals, thresholds, role badge |
| **Data updated** | Sync, alerts, dispatch rules, theme, map default |
| **Primary** | Save Changes |
| **Error prevention** | Grouped cards; 0–100 bounds on numbers |

---

## Role-specific views

Only **Ops Manager** is implemented. Maintenance receives faults via handoff; no separate maintenance UI in this prototype (per assignment: separate screens only when permissions/actions differ).

---

## Global action hierarchy

1. **Primary** — Recommend, Dispatch, Confirm Dispatch, Save  
2. **Secondary** — View, Review, Cancel, filters  
3. **Destructive** — Abort, Confirm Abort
