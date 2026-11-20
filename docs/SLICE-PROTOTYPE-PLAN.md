# Slice prototype plan — what to put in front of Morgan

Derived from Sources 01-03. Morgan has already specified the architecture and the governing rule.
The prototype's job is not to invent a design; it is to make her stated design concrete enough to
mark up, in a form that survives her rule and answers her stated fear.

## The three constraints that decide everything

1. **Parity before improvement.** "We rebuilt the exact same report with the new data. We didn't
   change anything in that report." A prototype that looks like a redesign repeats exactly the
   mistake Morgan spent ten minutes describing about Tara's artifacts. The prototype must be
   visibly *reconstruction-shaped*, not makeover-shaped.
2. **Provenance is a requirement, not polish.** Asked for twice — "a really, really clear audit
   trail... state what the source of that number is" (accrual tool) and "a thorough pass of all of
   what data is being queried from where and how, documented really, really thoroughly" (dashboards).
3. **Drift / unstable underlying data** is Morgan's named technical worry. Answer it in the design,
   not in conversation.

## The slice: one product x all four view levels

Morgan's target: *"one dashboard per product, with the drill-down views necessary for the exec view,
manager view, a production summary view that's very pipeline focused, and the rep performance views."*

**Slice on view level, not on product.** Build **Accounting / Bookkeeping** across **all four**
view levels. One product x four levels proves the template; one level x three products proves
nothing, because the template *is* the four levels.

**Why Accounting is the right first product:**
- Loudest pain, and the one under Sean's scrutiny.
- **Supabase is the only live data path Judy holds that is not blocked.** Snowflake grants are
  pending and N8N is down. Judy already has collaborator edit access, and Morgan has already
  sanctioned routine querying of it for the report.
- It is the one product where the slice does **not** require solving cross-system identity
  resolution — rep, org, work type and cycle all sit in one database. Cross-product joins are
  phase 2 and should not block the demo.
- The Tax rows in the inventory are the least reliable: Karen has delegated to Shelby and is not
  ramped, and Morgan has open concerns about that ramp. Don't build the demo on the softest data.

## The four design moves

**1. Every tile carries provenance.** Four fields on every metric, visible, not in a tooltip:
   `source system -> table/query -> as-of timestamp -> parity status`.

**2. Gaps render as first-class UI.** The 48-row inventory is the spec. Rows marked "Does not exist"
   or "Active but incomplete" render as labelled placeholder tiles stating the named gap and the
   candidate source — not as missing tiles. Morgan opens the exec view and reads
   "Timely delivery by the 5th / by the 10th — MISSING. Last seen in the linked delivery dashboard.
   Candidate source: Supabase, delivery date vs. cycle." That is the conversation she wants.

**3. A parity column.** For each metric: what the old report showed, what the new one shows, and
   whether they reconcile. Where the old number cannot be reproduced, say so explicitly. This
   operationalises her rule and makes the prototype politically safe — it is a reconstruction with
   a receipt, not a redesign.

**4. Pinned, versioned data.** Query a dated extract with row count and checksum shown on the page,
   not live queries underneath a long analysis. Put the as-of timestamp on every view. One design
   decision that directly answers the drift worry.

## Build order under time pressure

1. **Freeze the inventory as the spec.** Largely done — managers have filled it. Stop collecting.
2. **Lock the metric contract for Accounting.** ~15-20 metrics across the four view levels, each row
   carrying: metric | view level | old source | new source | query | parity status | gap note.
   *This table is the actual deliverable.* The dashboard is just its rendering.
3. **Pull one real pinned Supabase extract.** Dated, row-counted.
4. **Render the four views** as a single page, explicitly labelled as a spec/wireframe for Morgan's
   PRD, not as a build.
5. **Show Morgan before she writes the PRDs.** She said she'd write them; a concrete slice in front
   of her makes those PRDs much faster and costs Judy far less rework than guessing at them.

## Framing it for Morgan (matters as much as the build)

Say plainly: *this is the template, reconstructed from the old reports, with every number's source
stated and every gap named — mark it up and it becomes the PRD.* Do **not** present it as a new
design. The medium is not the problem — Tara's artifacts failed because they changed the content,
not because they were artifacts.

## Deliberately out of scope for the slice
- Tax and Payroll views (stamp out after the shape is approved)
- Cross-product joins and identity resolution
- MBO reconstruction (Judy still needs to open it; Karen owns it now and can't switch off its triggers)
- Anything requiring Snowflake grants or N8N
- Any change to the live Vercel app — Morgan explicitly asked for no rapid changes there right now
