# Dataset Publishing Feasibility Assessment

**Date:** 2026-07-18
**Scope:** All 29 open issues in `openwashdata/data` (issue tracker snapshot as of 2026-07-18)

This document reviews every open dataset idea in the issue tracker and assesses
the feasibility of publishing each one as an openwashdata R data package,
following the established workflow (tidy data + `washr` + documentation website).

Feasibility is assessed along four dimensions:

- **Access** — is the raw data actually obtainable?
- **Permission** — do we have (or can we get) consent / a redistribution-compatible license?
- **Effort** — tidying, documentation, and engineering work required.
- **Status** — how far along the work already is.

---

## Summary

| Tier | Issues | Count |
|------|--------|-------|
| A — Ready or nearly ready (act now) | #17, #22, #4, #3 | 4 |
| B — Feasible, blocked only on author consent | #49, #43, #47, #40, #44, #41, #38, #46 | 8 |
| C — Feasible, needs scoping/license check | #23, #12, #24, #54, #57/#10, #27, #11, #18 | 8 |
| D — Low feasibility or low priority as-is | #30, #19, #14, #13, #15, #8 | 6 |
| E — Scheduled for later / housekeeping | #58, #6 | 2 |

Headline numbers: **4 datasets could be closed out or published with days of
effort**, and **8 more are technically ready but wait only on author
confirmation** — consent follow-up, not data work, is the main bottleneck in
the pipeline.

---

## Tier A — Ready or nearly ready

These have data in hand, permission resolved (or resolvable trivially), and
work already started. Highest return on effort.

### #17 — UNHCR WASH data dashboard
- **Status:** Package already exists at `openwashdata/unhcrwash`, pulling data
  via the dashboard's download link (built Nov 2024). Maintainer approved the
  approach in the thread.
- **Feasibility: HIGH.** Remaining work: automate refresh with GitHub Actions
  (proposed in-thread), finish documentation, publish. This issue could likely
  be closed after a final review of the package.

### #22 — BASEflow & Waste Advisors KAP survey (Malawi)
- **Status:** Work moved to `openwashdata/chckapmalawi` in 2023. Last open item
  (May 2024): *fix the citation*. Anonymisation requirement was known and
  handled in the package workflow.
- **Feasibility: HIGH.** Remaining work is a citation fix and a close-out check.

### #4 — Climate vulnerability & sanitation, rural Cambodia
- **Status:** Author (jamespharper) submitted the CSV directly and data is also
  on OSF (https://osf.io/dzt7v/). Package repo `openwashdata/climatevulnerabilitykhm`
  was set up in 2023 with tasks assigned; thread has been quiet since.
- **Feasibility: HIGH.** Data + author consent both present. Needs someone to
  resume the package work; the main risk is author responsiveness after the
  long pause.

### #3 — WHO/UNICEF JMP raw data
- **Status:** Funded work (`jmpinput` development repo exists), ownership was
  being handed to a named team member. Related prior art: `WASHNote/jmpwashdata`
  already packages household/hygiene raw sources.
- **Feasibility: HIGH.** In progress and funded. Main task is confirming
  current ownership and avoiding duplication with `jmpwashdata`.

---

## Tier B — Feasible, blocked on author consent (ds4owd capstone datasets)

All of these are student capstone datasets from the ds4owd-001 course. The data
already exists in course GitHub repos, the tidying effort is known (tidiness
labels), and the openwashdata team has published many similar ones (see the ~15
closed ds4owd issues). The **only blocker is author confirmation** — the data
belongs to the students/their organisations.

| Issue | Dataset | Tidiness | Consent status |
|-------|---------|----------|----------------|
| #49 | Hydrogeological dynamics / groundwater management | high | reached out, no reply |
| #43 | Household sanitation product deliveries, Cambodia 2019–20 | high | reached out, no reply |
| #47 | Flood losses & protection, small businesses | (none) | reached out, no reply |
| #40 | WASH in schools, Nigeria | low | reached out, no reply |
| #44 | Lab validation of portable microbial water-quality kit | low | **not yet contacted** |
| #41 | HWISE scale, Rwanda | mid | **author embargo** — asked to wait until their paper is published; will then share extended data. Follow-up flagged Jul 2026. |
| #38 | Field application of pit latrines | high | private repo — needs author engagement and a privacy review before anything can be published |
| #46 | WASH technology beneficiaries, Indonesia | high | **no email** — no way to contact author currently |

**Assessment:** Publishing any of these is technically straightforward (the
team has a proven pipeline for exactly this kind of dataset). Recommended
actions:

1. Contact the #44 author (never reached out — cheapest possible win).
2. Send one final follow-up round for #49, #43, #47, #40; if no response in
   ~2 months, close as "no consent" (mirroring how #42 was closed with a
   *don't publish* label).
3. #41: honor the embargo; re-check now (the July 2026 follow-up note is due).
4. #46: one attempt to find contact info via the capstone repo; otherwise close.
5. #38: requires an explicit conversation about why the repo is private —
   possible sensitive content; do not proceed without clearance.

---

## Tier C — Feasible but needs scoping, license check, or engineering decisions

### #23 — What a Waste Global Database (World Bank)
- **Access:** Downloadable from the World Bank data catalog. **Permission:**
  World Bank data is generally CC BY 4.0 — verify for this dataset.
- **Feasibility: HIGH, effort moderate.** Static 2019 dataset, great teaching
  value (explicitly noted in the issue). A good hackathon or student project.

### #12 — SFD data (~300 city shit-flow diagrams)
- **Access:** Available as JSON from the SuSanA SFD portal — machine-readable
  already. **Permission:** needs a license check / OK from SuSanA-SFD.
- **Feasibility: HIGH, effort low-moderate.** JSON→tidy conversion is
  mechanical; the dataset is well-bounded.

### #24 — Revenue & water production, 7 rural piped-water providers (2016–2020)
- **Access:** Preserved under **controlled access** in the Oxford Research
  Archive. **Permission:** the submitter is the data owner and came to us —
  strong signal of willingness.
- **Feasibility: MEDIUM-HIGH.** Exceptionally well-documented, high-value
  longitudinal dataset (~5,500 waterpoints). The open question is whether the
  controlled-access terms allow an openly licensed derivative; needs one
  conversation with the author. Thread has been dormant since 2023 — revive it.

### #54 — WASH glossaries compilation
- **Access:** PDFs are public. **Permission:** varies per source — note the WHO
  glossary precedent (#53, published as `glossarywho`) but also that at least
  one candidate source is **CC BY-NC-SA**, which constrains redistribution and
  must be tracked per source.
- **Feasibility: MEDIUM.** Open-ended, multi-source project rather than one
  dataset. A community contributor has already proposed an extraction tool
  (`extract_glossary`). Best treated as a rolling program: publish one glossary
  package per cleared source, replicating the `glossarywho` workflow.

### #57 + #10 — Water Point Data Exchange (WPDx) — *duplicates, consolidate*
- **Access:** Excellent — daily-updated CSV plus a Frictionless datapackage
  with schema. **Permission:** open data, provider was responsive by email.
- **Feasibility: MEDIUM, effort HIGH.** The blocker is engineering, not access:
  ~800k rows is too large to embed in an R package. The thread already
  identified the right approach — an API/lazy-loading wrapper package (like
  `jmpwashdata`-style access functions) rather than bundled data. Initial work
  exists (`openwashdata/whdxdata` is linked from #57). Recommend closing #10 as
  duplicate of #57 (or vice versa) and writing a short design decision (wrapper
  vs. PostgreSQL-backed subset) before more work.

### #27 — Sierra Leone WASH data portal
- **Feasibility: UNKNOWN → MEDIUM.** No exploration recorded in 2.5 years.
  Needs a 1-hour scoping pass: what's downloadable, in what format, under what
  license. Country-portal precedent exists (the closed Kenya #50 / Ghana #16
  issues show these can go either way).

### #11 — SIASAR (Global Rural Water and Sanitation Information System)
- **Feasibility: MEDIUM.** Multi-country monitoring platform; related Peru
  dataset (#36) was already handled. Needs scoping of export/API and license.

### #18 — whdxdata (WASH health data exchange)
- **Feasibility: UNKNOWN → MEDIUM.** Title-only issue from 2023. Overlaps with
  the `whdxdata` repo referenced in #57 — clarify whether this is the same
  effort; if so, merge threads.

---

## Tier D — Low feasibility or low priority as currently framed

### #30 — IMF World Economic Outlook Database
Official macro data with its own good access tools; **redistribution terms
need checking** and it is not WASH data. Value to openwashdata is as a
companion/teaching dataset at best. **LOW priority.**

### #19 — Water footprint database (2005–2011)
Data is old, machine-readability unconfirmed, license unclear, authors not yet
contacted, and the issue's own questions ("is there more up-to-date data?")
remain unanswered since 2023. **LOW** unless someone champions it.

### #14 — WRI Aqueduct
Openly licensed but primarily **geospatial raster/vector products** behind a
registration wall — a poor fit for the tidy-dataframe R package model without
significant design work. **LOW-MEDIUM.**

### #13 — Humanitarian Data Exchange
A *platform* hosting thousands of datasets, not a dataset. Not actionable as
framed. Either close or re-scope to specific HDX datasets worth packaging.
**NOT FEASIBLE AS-IS.**

### #15 — Humanitarian data resources
A link to a third-party list of resources — a discovery aid, not a dataset.
Convert into candidate issues for anything valuable on the list, then close.
**NOT FEASIBLE AS-IS.**

### #8 — Evaluation of FSTPs and STP co-treatment systems, India
Data locked in a PDF report; plan was to ask the publisher for the underlying
Excel. No progress since 2023. PDF table extraction is possible but costly and
error-prone. **LOW-MEDIUM** — one email to the publishing organisation decides
this; if no source files, recommend closing.

---

## Tier E — Scheduled / housekeeping

### #58 — CVEN 5999 SS26 capstone dataset
Deliberately parked until **September/October 2026** per the issue. High
feasibility when it wakes up (course-project pipeline, author already tagged).
No action needed now.

### #6 — Long list of potential data sources
Meta/tracking issue from 2023; most linked items now have their own issues.
Recommend closing or replacing with labels/a project board.

---

## Cross-cutting recommendations

1. **Consent follow-up is the pipeline's bottleneck.** Eight datasets (Tier B)
   need nothing but an author reply. A standard follow-up cadence (initial
   contact → reminder at 1 month → close at 3 months with a `no consent`
   resolution) would clear the backlog either way. The existing labels
   (`reached out`, `no email`, `don't publish`) already support this.
2. **Close-out pass:** #17, #22, and possibly #4 and #3 appear done or nearly
   done in their package repos; the tracker issues just never got closed.
   Aligning the tracker with reality makes the true backlog visible.
3. **Deduplicate:** #57/#10 (WPDx) and possibly #18/#57 (whdxdata) are the same
   work under different issues.
4. **Two structural decisions** would unblock the biggest-value items:
   - Large/refreshing datasets (WPDx #57/#10, UNHCR #17): adopt a standard
     pattern (API-wrapper package + scheduled GitHub Actions refresh) instead
     of embedded data.
   - Licensing rule of thumb: sources under NC/ND-style licenses (some
     glossaries in #54) need explicit handling before packaging; document the
     acceptable license list once and reuse it.
5. **Quick wins to schedule next:** contact the #44 author; revive the #24
   conversation (high-value dataset, willing owner); scope #12 (SFD JSON) and
   #23 (What a Waste) as well-bounded packaging projects suitable for
   students or a hackathon.
