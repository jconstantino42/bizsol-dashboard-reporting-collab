# EOD rundown for Morgan — 20 Nov 2026

## Verified state of the tracker (read directly, not self-reported)
| | Rows |
|---|---|
| Access confirmed by a manager | **33 of 50** |
| Legitimately n/a (no view exists, or they're our rows) | 8 — rows 28, 41, 46–51 |
| **Genuinely outstanding** | **9 — rows 15–23** |

Breakdown of who did what:
- **Tara / Bookkeeping (rows 2–14)** — all 13 rows ticked for both Judy and Morgan access. Row
  content confirmed on 8 of 13; the last five she's ticked access but not content.
- **Shelby / Tax (rows 24–27, 29–32, 44–45)** — 10 rows, signed.
- **Noah / Payroll (rows 33–40, 42–43)** — 10 rows, signed.

## The one block left, and it needs a decision
**Rows 15–23 — Bookkeeping Advisor and Engagement Specialist. Nobody owns them.**
Karen isn't ramped. Shelby says only the two Tax Manager items are hers, which is accurate. So nine
rows have no respondent — and they're not trivial ones. They include whether a specialist's activity
can be separated from the advisor they're assisting, and what an Engagement Specialist owes at all
given it's a new role. Needs Morgan to name an owner.

## Closed today
- **Tax Manager Reports** — the top gap. Shelby granted both of us writer.
- **The "dead" link in row 23** — never dead. It's the Tax Manager Database; we just had no access.
- **DNU: Add-Ons Operating Models V2** — resolved without going to Roberto. Ken had linked the *old*
  op model; the current ones are in Omni and up to date. That cold ask is cancelled.
- **Payroll** — Noah done, and he wants to take ownership of the Payroll ACE Model off Amparo.

## Found today, worth Morgan's attention
1. **The tax engagement activity data exists.** Morgan's read was that tax advisors' engagement work
   "isn't covered anywhere." It is — the Tax ACE SF Reports Refresh holds 7,332 email rows, 1,237
   calls, 1,237 texts, 2,738 meetings held, 1,236 tax OB cases. Exactly the Salesforce rep activity
   she asked for. Nobody had mapped it until today.
2. **The zero-data problem was a stale copy**, as she suspected. The Tax Manager DB is a real
   application database — 10,531 task rows, 404,292 audit log rows, projects, peer reviews, stage
   history.
3. **First end-to-end feeder chain anyone has described**: Salesforce → Armando Monteza's source doc
   → Tax ACE / Comm Dashboard, with Tax Manager Reports feeding in.
4. **The Tax Manager is four components, not one** — Apps Script, Database sheet, Report Export, and
   a GitHub repo.
5. **That repo is on a personal GitHub account** — `shelbyschimetz-rgb/HCP-Tax-Manager-Database`,
   outside the HCP org. Source code tied to a personal account.
6. **Armando owns the SF source doc**, not Shelby. We have read only on it.

## Still outstanding
- Rows 15–23 — no owner (decision needed)
- **Karen** — hasn't actioned yet; verified Morgan is still not on the Pro Requests sheets
- **Ken** — his own shared-drive access, on return
- Writer on Armando's SF source doc
- The GitHub repo move into the org
- Tara's row-content confirmation on rows 10–14
