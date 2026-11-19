# Source 02 — "INHA Reporting Inventory: Accounting, Tax and Payroll" (Google Sheet)

https://docs.google.com/spreadsheets/d/1eI6WeLny-XUzaijZRl2apBCV4pK0nGrKDS8NTzpNepg/edit?gid=101#gid=101
Tabs: Start Here | Reporting Tracker (48 rows) | Metrics We Used to Report | Systems & Sources
Snapshot read: 2026-11-19

## Tracker status rollup (48 rows)
| Status | Count-ish | Where |
|---|---|---|
| Active and good | ~17 | Tax app, Tax ACE Model, Advisory Gauges, Payroll ACE, Intercom, SF Retention |
| Active but incomplete | ~22 | Most of Bookkeeping; all Engagement Specialist rows; payroll pod views |
| Does not exist | 3 | TA account management; payroll capacity; primary-vs-assistant attribution |
| Needs a new reporting view (cross-function) | 5 | Cross-role ACE, MBO, AI QA pipeline, consolidated view, retired-views register |

## Systems registry (candidate sources of truth)
| System | Holds | Status |
|---|---|---|
| **Vercel app** — In-House Accounting Operations (Supabase + Vercel) | BK Dashboard, PM Back Office, Advisor Back Office, Reporting (PM+), Launches, Delivery Readiness, Detached & DAO. Work types: Current Cycle, Maintenance (1,614), Quarterly (107), Historical (97), Special Project | Live, main build. Feeds mid-build; several pages PM+ gated |
| **Tax app** (Apps Script) — Tax Manager Database | Tax return projects: volume, stage, on-time, caseload + round-robin assignment | Live, separate build |
| **Tax Team ACE Model** (Apps Script, "Communication Dashboard") | Tax advisor + Sr Tax Preparer ACE | Live, needs refresh for changed role scopes |
| **Advisory Gauges** (SQL-backed Sheet -> Apps Script dashboard) | Engagement: pros engaged, show-up rates Zoom/chat/call/text, reschedules, cancels. Tabs: Advisory Summary, WIP Delivery, _ENGAGEMENT, _DEMOS, _WEEKLY, _MONTHLY, Worklist, targets, absence | Live; roster currency to confirm |
| **INHA Detach Tracker** (Sheet) | Detach signals, attribution snapshot, reason rules, reconciliation, book by month | Live |
| **Salesforce** | Rep activity: calls, SMS, demo records; BizSol Multi-Product Onboarding Overview; Retention dashboards (BizSol / Accounting / Payroll) | Live; likely source of truth for engagement activity |
| **Intercom** | Payroll + Accounting + Tax Performance support dashboard (live data) | Live, "no gap" |
| **Payroll ACE Model** (Sheet) | Onboarding / Support / Data Migration summary metrics, pod TL roll-up | Live but fragile: old formulas, many authors, breaks; payroll-only (no Acctg/Tax); manual Intercom exports |
| **Payroll QA Spiff Tracker** (Sheet) | Payroll QA dashboard (human QA, parallel to AI QA) | Live, good |
| **Omni** | Op model reporting | Stays put; central view must be able to reference it |
| **Asana** | Prior project/delivery tracking, complexity points, pending feed | Retired — source of most of the loss |
| **AI QA** | QA scores / pass rates | Pull method drifted; being re-established with Tara |
| **MBO** | Historically held much of this reporting | Status unknown — open question |
| **Standalone artifacts** (Claude artifacts) | Tax Readout, Retention artifact | Ad hoc, to be consolidated |

## Key links
- Vercel app: https://in-house-accounting-operations-housecallpro-infosys.vercel.app/work/maintenance (also /bk-dashboard)
- Advisory Gauges: https://docs.google.com/spreadsheets/d/1rSQSaWe-0puEfxnljHc0XlnGuvKG31w3ysYO-unZWRs/edit
- INHA Detach Tracker: https://docs.google.com/spreadsheets/d/11JZ4NjJl-Zfw8T8zSy1WWkMRFPXaoO7oEeoUZoobQ3Q/edit
- Tax Manager Database: https://script.google.com/a/macros/housecallpro.com/s/AKfycbxB-1_PJv3etBhHIzX2qbzLBAXGZAJlYafCC4N-M--3fJ6wfow6foBSMLMfpxJdTmVrbQ/exec#/reports
- Tax Team ACE Model: https://script.google.com/a/macros/housecallpro.com/s/AKfycbz6mdm-CAoQLAW-VDHXPQi_fQfkQqN6zFOJu0Ctj4drQh759ccfCjSS7hil0l4kUssu/exec
- Intercom support: https://app.intercom.com/a/apps/h6f82l2e/reports/custom-reports/report/9230183
- SF Onboarding: https://housecallpro.lightning.force.com/lightning/r/Dashboard/01ZPD000001VNZF2A4/view
- SF Retention: .../01ZPD000001LE0z2AG/view, .../01ZPD000001MCd32AG/view, .../01ZPD000000G3oL2AS/view

## Roles x deliverables (the grid the prototype has to express)
- **Bookkeeping** — Bookkeeper / Sr Bookkeeper: maintenance delivery, quarterly, historical, launches/special project, AI QA, capacity & assignment, ACE. Pod TL: whole-pod roll-up. Pods: Financial Keepers, Home Sheet Home, Big Balance Theory, Retained Earners. TLs: Anna Espinosa, Jared Maranga, Shai Bacani, Vince Pino. 14 Sr BKs.
- **Tax & Engagement** — Bookkeeping Advisor (engagement only; Soraya Volcy, Kandyse Bertrand, Caleb Wireman); Engagement Specialist (doc collection + engagement; Ericah Aninon, Josh Abat); Tax Advisor EA (engagement + tax return projects + account mgmt TBD; Ashley Lauderman, Cherrie Groves, Dashonnon Heffker); Sr Tax Preparer (return prep).
- **Payroll & Onboarding** — Payroll Onboarding Specialist (2 pods: Ivy Mapacpac 7, Anna Flores 6); Payroll Support Specialist (2 pods: Leshlie Cruz 6, Ivanna Santos 6); Sr Specialist QA (Richie Ramirez, Meg Castelo, Jhay Cadiz); Data Operations (Kryzel Elipane, Mica Olalo); hybrid roles (Nicky Santos, Mark Manalo; Angie acctg+tax support).
- **Retention** — Retention Specialist (rep + team).

## The named holes (what the prototype must make visible)
1. **Timely delivery split** — "delivered by the 5th / by the 10th" per BK. Lost with Asana. Check Delivery Readiness.
2. **Capacity target** — load per BK exists; nominal capacity never populated, in old build *and* new.
3. **Pro requests metrics** — doc open requests, uploads waiting, transaction open requests/feedback waiting, overdue tasks per BK. Not found in the app.
4. **Unplanned OOO days YTD** — not found.
5. **Pod-level QA** — PM Back Office has no QA; may sit in Reporting (PM+), unconfirmed.
6. **Quarterly + Historical QA feeds** — read "feed pending".
7. **Tax-side engagement** — advisor reports cover only the bookkeeping side of a pro's account.
8. **Primary vs assistant attribution** — advisor and engagement specialist activity mixed in the same reports.
9. **Engagement Specialist throughput** — no per-rep measure of how much each clears, how fast.
10. **Ops Slides concise view** — outreach vs goal, touchpoints vs goal, attendance, timely delivery, QA, detach, CSAT. No longer exists as a single view.
11. **Weekly Manager Checkdown** — compliance per BK, team health score/grade, 4-week trend, 1:1 coverage. Gone dark.
12. **Payroll capacity** — does not exist.
13. **Cross-role ACE view** — has never existed. Headline gap.
14. **Payroll ACE covers payroll only** — no Accounting/Tax; TL view across all 3 products missing.
