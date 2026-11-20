# Access & gap audit — INHA Reporting Inventory
Run 2026-11-20 against Judy's Google Drive. This is the deliverable Morgan asked for:
*"check to see if we have edit privileges or flag any that we don't."*

## Caveat on "edit privileges"
The Drive connector reports `canEdit: false` on nearly every file **including ones Judy owns and
edited today**, so that flag reflects the connector's read-only scope, not real access. What IS
verified below: whether each asset resolves (reachable yes/no), who owns it, where it lives
(shared drive vs. personal Drive), and when it was last touched and by whom.
Per-file role (writer vs. reader) still needs a permissions check — see "Still to run".

---

## FINDING 1 — The inventory under-reports what is alive
Several assets the workbook lists as retired, missing, or "not found in the app" were **edited
today**. They are being actively maintained; they just aren't connected to anything.

| Asset | Inventory says | Actually |
|---|---|---|
| **Maintenance Bookkeeping Operations** `1fPxMHoHhzWUfx8bQdkWLQxLddosAgmdWiu3fi8yrcRY` | "Prior dashboard, no longer in use" | **Modified today 08:17 by Karen Herring.** Owner: Judy |
| **Pro Requests — [per pod]** (8+ sheets, see list below) | Source for doc/transaction requests + overdue tasks: "Not found in the app" | **All modified today 11:35 by Karen Herring.** Owner: Karen |
| **MBO Data Source** `18yUjT6BjAAU5HTBoBxChbMfM5skNCS08QBwdfZWJ5VM` | MBO status "unknown — does it even function?" | **Modified today 16:16 by Armando Gonzalez Monteza.** Owner: Judy |
| **BK Correction Trackers** (per BK, Oct cycle) | AI QA "pull method unclear / drifted" | **Modified today 15:52–15:58 by Jared Maranga.** On shared drive |
| **Weekly Manager Checkdown** (per manager) | "Gone dark" | Judy's modified 2026-11-14; Karen's 2026-11-07. Semi-live |
| **Advisory Gauges** | Active and good | Confirmed — modified today 16:53 by Judy |
| **Payroll ACE Model** / **Payroll QA Spiff Tracker** | Active | Confirmed — both modified today 16:04 |

**So the answer to "where did the old metrics go" is often: nowhere. They are still being produced
by hand, into sheets, by the managers.** That is a materially different problem from "the metric
was lost in the migration", and it changes what the consolidation work actually is.

## FINDING 2 — One dead link in the workbook
`1VGnt4xnniWERRHhjTilzcskrOC6C_OV7eEWpe_eg79U` — **Requested entity was not found.**
Sits in the Notes column of a Tax Advisor "Team-level engagement view" row. Either deleted or Judy
has no access. Needs chasing with Karen/Shelby.

## FINDING 3 — Missing links now resolved
These were named in the workbook with no URL, or named only in transcripts. All found:

| Asset | File ID | Owner |
|---|---|---|
| Payroll ACE Model | `15LqxT-Y3Io45mRLSx5QJII3vt00ByrC_SkSgRg5JwMI` | **Amparo DeLeon** (Noah last edited) |
| Payroll QA Spiff Tracker | `1mrMt8KyANXQTIiyUe-Jn25MIcNZtEKPA9gd8Wxrpl_U` | **Shelby Schimetz** |
| Tax Manager Reports (feeder behind the tax app) | `1GFw9KpzmSbbMDyMvKqrfUSgYayf05gcVsVo5mn1oeWY` | **Shelby Schimetz** |
| [Source] INHA ACE Outline | `1FldTP0SlDbJPcNGog58pfBo0f3J613M-Kqx3ej7Cpwc` | **Morgan Knox** |
| Maintenance Bookkeeping Operations | `1fPxMHoHhzWUfx8bQdkWLQxLddosAgmdWiu3fi8yrcRY` | Judy |
| MBO Data Source | `18yUjT6BjAAU5HTBoBxChbMfM5skNCS08QBwdfZWJ5VM` | Judy |
| Weekly Manager Checkdown — Judy | `1rbRN79lr9jeeHtPjKx841HmI_1ALbI5Q6Ta76o8ZoLE` | Judy |
| Weekly Manager Checkdown — Karen | `1oulKMMxMHeU5E9R5VoJGLC8hWkUZ-yreUkxLOAXy-mQ` | Judy |
| Cleaners Key Performance Metrics 2026 YTD | `1t965yPpuj1PGM-fJVaqj2m6k028ghAWg47zQmCj-gz8` | **Tara Young** |
| INHA Pro Requests by Org (Feb snapshots) | `1GryJFC3...`, `1MONstkD...` | Judy |

**Pro Requests family** (all owner Karen Herring unless noted):
Soraya Volcy & Dustin Edwards `1tTCdwuNuKxHebzmdEf4svjksxTVF1mUFTqbxkK0PPEg` ·
Caitlin McManus & Shai Bacani `1ZAQsbzsypwesmFWmh2iksn34Icnj8usWt3DjlGudg5Y` ·
Mauricio Pantoja Ramon `1WBQc14CUWSvdzcLqPR5oY88QO9l41ZOctx8zGKgnzVM` ·
Kandyse Bertrand & Jared Maranga `1Fj63MwuYNl7gpzZMMzBul-KI6wZK7wRbaTo6uAicBho` ·
Lisa Horner & Vaughn Merry `1u42r_jPeM8dWm8vOEtcw4oxa5PJIuAid7lUDxl_QX50` ·
Caleb Wireman & Anna Espinosa `1D6VUzUD8yf_SKrv6v5fJr2q2cmNhxBo8eA5Rh7X_Pfk` ·
Dustin Edwards `1KzbbkcwnL_4Tc9DFXpfN8QeBPPOZzQYDTeAWgp2GXJM` ·
Lucia Maynez `1WPXDcLf261yrmNUXZGFjcVl-JqAKdKaC7FuZ9juYZnI`

## FINDING 4 — Key-person risk is the real structural problem
Most of these live in **individual people's personal Drive** (`visibility: UNLISTED_TO_DOMAIN`,
single named owner), not on a shared drive:

- **Shelby Schimetz** owns Payroll QA Spiff Tracker *and* Tax Manager Reports
- **Amparo DeLeon** owns the Payroll ACE Model — not Noah, who actually runs off it
- **Karen Herring** owns the entire Pro Requests family
- **Tara Young** owns the Cleaners metrics
- **Roberto Romero** owns DNU: Add-Ons Operating Models V2 (used by Retention)
- **Morgan Knox** owns the INHA ACE Outline

Only **Advisory Gauges**, the **INHA Detach Tracker** and the **BK Correction Trackers** sit on
shared drives (`0ALZE-nI56aZSUk9PVA`). Everything else is one offboarding away from disappearing.
For a consolidation project whose whole point is "one consistent pipeline", this is the finding
that matters most — and it is a concrete, cheap fix (move to a shared drive).

## FINDING 5 — Duplicate sprawl
Confirms Morgan's "everyone building their own things": `Copy of Payroll ACE Model for Accounting`,
`Copy of Weekly Manager Checkdown` (x2), `Copy of Maintenance Bookkeeping Operations - April 24`,
`Copy of Cleaners Operations Hub`, `Copy of Cleaners Operations Hub for Judy`, two identically
named `INHA Pro Requests by Org _Untitled Page_Table`, `Tracis [Source] INHA ACE Outline`.
Each copy is a candidate for someone reading a stale number.

## FINDING 6 — The workbook captures surfaces, not feeders
The inventory lists dashboards people *look at*. It does not list what feeds them. Still unmapped:
- The spreadsheet(s) bound to the two unidentified Apps Script dashboards on the Start Here tab
  ("confirm which is advisory and which is detach")
- The SQL behind Advisory Gauges
- The Supabase tables behind the Vercel app
- The "engineering data tab" and "Asana pending feed" named on the Metrics tab
- The "linked delivery dashboard" that fed timely delivery and QA average — still never named

For a consolidation, the feeders are the thing that matters. The surfaces get rebuilt.

## Still to run
1. **Per-file role check** (`get_file_permissions`) on the ~25 assets, to answer Morgan's edit-rights
   question properly rather than by inference.
2. Resolve the two unidentified Apps Script dashboard URLs and find their bound sheets.
3. Open the MBO Data Source and check it against the current reports — Judy flagged this as not yet
   done, and it may answer several tracker rows outright.

---

# VERIFIED ACCESS MATRIX (per-file permission lists, 2026-11-20)

| Asset | Judy | Morgan | Owner / where |
|---|---|---|---|
| **Tax Manager Reports** (feeder behind tax app) | 🔴 none (domain reader) | 🔴 none (domain reader) | Shelby Schimetz, personal Drive |
| **DNU: Add-Ons Operating Models V2** | 🔴 comment only | 🔴 comment only | Roberto Romero, personal Drive |
| **Pro Requests** family (8 sheets) | ✅ writer | 🔴 none (domain reader) | Karen Herring |
| **MBO Data Source** | ✅ owner | 🔴 none (domain reader) | Judy |
| Tax sheet `1VGnt4x...` (Notes, row 22) | 🔴 link dead | — | unknown |
| Advisory Gauges / Detach Tracker / BK Correction Trackers | ✅ organizer | ✅ organizer | INHA shared drive `0ALZE-nI56aZSUk9PVA` |
| Payroll ACE Model | ✅ writer | ✅ writer | Amparo DeLeon |
| Payroll QA Spiff Tracker | ✅ writer | ✅ writer | Shelby Schimetz |
| [Source] INHA ACE Outline | ✅ writer | ✅ owner | Morgan Knox |
| Maintenance Bookkeeping Operations | ✅ owner | ✅ writer | Judy |
| Cleaners Key Performance Metrics | ✅ writer | ✅ writer | Tara Young |

**Also noted on the INHA shared drive:** `n8n-local-development@inha-n8n.iam.gserviceaccount.com`
holds writer and `n8n_business_process_automation@housecallpro.com` holds reader — confirming the
N8N pipeline writes into this drive, which matters given the sandbox migration. **Ken Hogue is
commenter only** on that drive, and he is the named respondent for the Retention rows.

## Written back to the workbook (2026-11-20)
- Reporting Tracker column H filled for rows 33, 35–38, 41, 42 (Payroll ACE Model, Payroll QA
  Spiff Tracker) and row 46 (MBO Data Source).
- New **"Access & Gaps"** tab added at index 2, carrying the action list, the alive-but-disconnected
  finding, the recovered links, the ownership risk and the unmapped feeders.

## Correction (2026-11-20)
An earlier pass mis-mapped the tracker's row numbering: the grid has **50 data rows (2–51)**, not 49,
and Bookkeeping runs to row 14, not 13. Several Link cells were written one row early as a result,
overwriting the Salesforce onboarding dashboard on row 33 and the Intercom support report on row 35.
Both were restored from the original read, and H33:H47 was rewritten against a verified A30:C51
row map. Nothing outside rows 33–47 was touched.

## Sign-off mechanism (final)
Per-row, in the Reporting Tracker itself — not a separate tab:
- **M** Judy has access (checkbox) · **N** Morgan has access (checkbox) · **O** Row content confirmed
  (checkbox) · **P** Confirmed by · **Q** Manager note / blocker
- **R** Re-check result — filled by Judy and Morgan after re-running the access audit, so a tick that
  isn't true gets caught.
- Rows with no link (17, 28, 41, 46, 48–51) are pre-marked n/a.
The separate "Manager Sign-Off" tab built earlier was deleted; two sign-off surfaces would have been
the same disease this project exists to cure.

---

# ROUND 1 RESULTS — 2026-11-20 afternoon

## Resolved
| Item | Was | Now |
|---|---|---|
| **Tax Manager Reports** | Neither Judy nor Morgan could open it — top gap | ✅ Both writer (Shelby) |
| **Tax Manager Database** (`1VGnt4x...`, the "dead" link in row 23 Notes) | Assumed deleted | ✅ Never dead — we simply had no access. Both writer |
| **DNU: Add-Ons Operating Models V2** | Comment-only, needed Roberto | ✅ Resolved without him. Ken had dropped in the **old** op model; the current ones are in Omni and up to date. **Do not send Roberto the ask.** |
| **Payroll rows 33–43** | Unverified | ✅ Noah completed M–Q. Google assets verified independently; Intercom/Salesforce on his word |

## New findings from Shelby's reply
1. **The Tax Manager is four components, not one** — Apps Script project, Database sheet, Report
   Export sheet, and a GitHub repo. The tracker had it as a single app.
2. **The GitHub repo is on a personal account** — `github.com/shelbyschimetz-rgb/HCP-Tax-Manager-Database`,
   outside the HCP org. Same key-person risk as the personal Drives but sharper: it is source code,
   and it leaves with the account. Needs moving into an org repo.
3. **A feeder nobody had named, and it is not Shelby's** — the Tax ACE / Comm Dashboard reads from a
   Salesforce source doc (`1mr-cg6yLlfLdls6ebbaFa2dMsz2eIqFftdN486kYkUQ`) owned by **Armando
   Monteza**. Judy and Morgan have **read only**. Shelby's "you have access to everything I own" is
   accurate — this one is not hers.
4. **First end-to-end feeder chain anyone has described**: Salesforce → Armando's source doc → Tax
   ACE / Comm Dashboard, with Tax Manager Reports also feeding in.
5. **Still open — the zero-data question.** Morgan's copy of the Tax Team ACE Model showed no data.
   Shelby sent links but did not say whether a newer populated version exists. Until that is
   answered, the tax rows marked "Active and good" stay unverified.

## Outstanding
Tara (Bookkeeping, 12 rows) · Karen (Pro Requests access for Morgan, MBO triggers) · Ken
(shared-drive access, on return) · writer on Armando's SF source doc · the zero-data answer from
Shelby · moving the GitHub repo into the org.
