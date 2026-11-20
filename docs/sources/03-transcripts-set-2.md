# Source 03 — Transcript set 2 (4 unique + 1 duplicate of Source 01)

## A. Judy + Karen Herring + Morgan (15:00) — tax/accrual sync

**Reporting-relevant:**
- Karen is **not ramped** on reporting and has delegated the inventory to Shelby. She has nothing to
  contribute yet. (She is still listed as respondent on 16 tracker rows.)
- Morgan: "Judy and I are probably best positioned to pull it all together for the sake of all the
  operations teams... get it stabilized so there's at least a good **template** that then you guys
  can own the underlying data for, and then flag if it needs adjustments, flag if there's challenges
  with the data."
- **Access**: Judy confirmed she has **collaborator edit access on the Supabase project** behind the
  accounting production app. Morgan needs adding. Reason given: "we're gonna need it if we're gonna
  **routinely query data from it for the report**." <- this is the sanctioned data path for the build.

**Parked to December — Accrual Reporting tool (separate project):**
- Problem: HCP revenue date is ambiguous — job date, scheduled date, completed date, invoice sent
  date, paid date; resends move it; pros can toggle their own default. "Housecall Pro is the source
  of truth for this revenue, and we keep moving that source of truth around."
- MVP shape: type in an org ID -> fetch revenue from Snowflake -> fetch GL / P&L / balance sheet ->
  blend into a workbook -> recalculate net income -> pull AR balance as of period end.
- Policy decision required: index on **job complete date**, with a stated asterisk that unmarked
  jobs won't appear and the pro is responsible for marking them.
- Design requirement worth stealing for the dashboards: **"a really, really clear audit trail"** —
  state the source of every substituted number, and highlight recalculated figures in a different
  colour with a note saying what they were recalculated from.
- Governance: must run through the **analytics handoff and review process** (a Claude skill Morgan
  is testing) because it is pro-facing and taxes get filed on it. Ashley has 1-2 urgent pros as MVP.

**Parked — advisory tooling vision (context for where this all goes):**
- Personalized rep brief / opportunity cards (already live for success advisors on F30): auto-pulls
  pro info, recent support history, recent cash-flow conversations, scripting, dynamic product pivot.
- **"Meeting brain"**: advisor Zoom calls -> Snowflake -> automated extraction for (a) QA/risk,
  (b) continuity of notes and follow-up tasks per pro. Would replace the manual tax meeting log.
- Benchmarking insights (Roland's build): how much HCP knows about a pro's business, compiled as
  advisory conversation guidance.
- Morgan's 12-month thesis: specialized roles (support, detach, account management, advisory,
  success) converge into a single **relationship owner** with all tools at their fingertips.

## B. Morgan / Rachel Shull / Patrick Schaefer / Judy (11:31) — AI build sync

- **N8N sandbox outage is ongoing and critical.** Will's position: "it's a sandbox, we're not worried
  about it, get your shit out of the sandbox." HCP doesn't own the monitoring infra in sandbox.
- **Judy is blocked on Snowflake grants** — cannot migrate workflows to the new instance until they
  land. ~100+ queries submitted for approval; Patrick's have no PII at all. Escalation path:
  Nick (data engineering) -> Will -> Sperry.
- Self-hosted instance will allow proper monitoring + criticality tiers. **L1 = pro-facing with
  immediacy, or production-halting.** AI reconciliation and AI QA have SLA flexibility.
- Engineering **RIF in the last 24 hours**; hiring campaign to follow; 3-6 months to ramp.
- Morgan's stated technical worry, directly relevant to this build:
  "I'm really concerned about hitting **drift** if I'm using Claude to analyze the data... I'm really
  concerned about the **underlying data being stable while it's running analysis on top of it**."
  Project assigned to Rachel: "optimal analytics pattern for lots of data sets."
- **Morgan owns the PRDs**: "I'll run through the scoping, and I will write out the PRDs and the
  design format of what I want the dashboards to look like with all of these reports, and then I can
  give you those docs, and then you and I can each process against them."
- Judy's assigned task: verify **edit access** across every inventoried report/sheet and flag any
  that are missing. "Use your Claude to double check."
- Deep work days blocked Wednesday + Friday. Judy off Black Friday. GitHub repo being set up.

## C. Morgan / Patrick / Rachel / Judy (11:03) — short standup
- Reconciliation workflow is the one critically impacted by the N8N outage.
- F30 pushed live; cards not generating due to N8N. F30 -> **F60** case change coming from onboarding.
- Manager-escalation PRD: Raena's BPA agents flag manager requests via call sentiment; gap is they
  don't read Intercom chats that never close.

## D. Judy + Morgan (16:30) — **the architecture conversation. Most important.**

**Status Judy gave:**
- Pulled in all old ACE models + known replacements, had Claude fill in the tracker; gaps now
  auto-highlight. Tara, Noah et al. reviewing. Majority already filled.
- Tara keeps offering to build it ("I'll have it built tomorrow") and has been told to stop —
  this is a data-collection exercise, not a build exercise.
- **MBO**: Karen owns it now; its triggers are still emailing and Judy can't switch them off.
  Judy wants to open it and check whether current reports captured everything it covered. Not done yet.

**Morgan's target architecture — stated explicitly:**
> "One dashboard per product. That has the drill-down views necessary for like the exec view,
> manager view, and then like a **production summary view that's very pipeline focused**, and then
> like the **rep performance views**."

Plus: "pull it all together, **reskin it, reformat it**, put it all in one consistent place, make sure
we do a thorough pass of **all of what data is being queried from where and how** and have that all
documented really, really thoroughly."

**THE GOVERNING RULE — parity before improvement:**
> "When we change a system or we change the data flow or we build a tool, we should start with:
> we rebuilt **the exact same report** with the new data. We didn't change anything in that report.
> ... If we can't do that, then that's a point that something is fundamentally wrong, or we need to
> be able to clearly [say] this part of the report is no longer relevant and it needs to be a very
> intentional conversation."
>
> "We don't ever turn on a new tool or a new process that breaks visibility. The **visibility needs
> to be doubled up and then we turn the old one off.**"
>
> "[The dashboard] needs to look like the old data, the consistent reporting that we had, that we
> were reading out on, that people were familiar with — and then where we want to go a little bit
> different or deeper is a different conversation."

**The failure story (why this rule exists):**
- Asana -> Apps Script was **not** a 1:1 swap. Nobody rebuilt the MBO on Apps Script data and ran it
  side by side against Asana before turning Asana off.
- Judy: "The build started going in vastly different directions and it was really difficult to keep
  track of who was managing what because we just kind of freaked out... everybody take a section and
  we'll fix it." Tara built into workbooks, dashboards, Apps Scripts.
- Judy's diagnosis of the rebuild loop: "We know what it means, and then we go to explain it, and
  we're like, okay, we don't know what it means. We'll rebuild it again."
- Morgan on the artifacts: "Tara built these artifacts and I was like, these artifacts don't make any
  fucking sense. I just need the same data that was in the slides — **this wasn't an invitation to
  completely have a makeover and revamp.**"
- What should have happened: take what was in the weekly slides, build a live dashboard that is
  *exactly* the same format and the same underlying data, just automated. Formatting changes are a
  separate, later, deliberate step.
- Compounding causes: Salesforce connectors banned -> everything pushed to Snowflake -> now the N8N
  migration. "This is tech debt. We change something, and now we have to rebuild something we had
  already built before."

**Organizational context (handle with care):**
- Tara felt attacked after a meeting with Sean, Shelby, Noah and Karen that neither Judy nor Morgan
  was in; she's highly reactive and overwhelmed. Morgan: "be really careful about the web app and
  not trying to go in and rapidly change stuff right now."
- Morgan is apprehensive about Shelby's ramp on accounting/tax; feedback given ~6 weeks ago on tax
  reports was never incorporated. No pre-read went to the tax ops sync with Sean.
- Karen doesn't know what reporting exists or existed.
- Sean asked "why are there so many reports across all this stuff?" Morgan's answer: because there is
  far more to manage here than in onboarding or support — a whole post-sale lifecycle of projects,
  production, people and roles.
- Morgan: "None of this is blame. Just put it on paper, and we're gonna fix it from here."

**Next steps named:** Morgan reads the tracker and sends async notes; Morgan writes the PRDs/design
format; both process against them on the deep work days. Claude usage budget raised to ~$3K each.
