# P0-04 restricted mutable assignment-ledger template v0.1

> **STATUS: BLANK RESTRICTED TEMPLATE / NO-GO — NOT A LIVE LEDGER, PARTICIPANT RECORD, OR FIELDING AUTHORIZATION.** This file contains no real candidate or study ID. Before `GO`, a named human may instantiate only a visibly `SYN-` rehearsal copy to test the workflow; a live fieldwork instance requires the shared preflight and P0-04 authorization block to be `GO` for the same frozen materials.

Template version: **0.1**, 2026-09-24  
Document ID: **`P0-04-ASSIGNMENT-LEDGER-TEMPLATE`**  
Related material pack: **[`P0-04-MATERIAL-PACK` v0.1](P0-04-material-pack-v0.1.md)**  
Evidence status: **0 of 5 required eligible interviews; no assignment, exposure, deviation, or disposition is claimed**  
Production authority: **none; G0 remains closed**

## Purpose and separation rule

The material pack freezes the assignment design. This separate template is the source for a **restricted mutable instance** that can rehearse the workflow with visibly synthetic IDs or, only after authorization, record which precommitted row an eligible, consented interview start actually used. Keeping mutable study/order/disposition data here prevents routine updates from changing the digest of the frozen participant-facing pack.

Before any use, the named privacy/data owner must:

1. select `SYNTHETIC-REHEARSAL` or `LIVE-FIELDING`, then copy this blank template into `[REQUIRED: approved restricted operational location]` using `[REQUIRED: approved instance name and version]`;
2. record the frozen material-pack digest, blank-template digest, approved start-order choice, exact access group, retention/deletion rule, and instance identifier below;
3. confirm that the instance contains no name, contact information, candidate code, deletion token, screener narrative, report/incident narrative, boundary detail, or research answer; and
4. keep the mutable instance out of participant-facing packets, broadly shared folders, source-note exports, and immutable reports.

The blank template remains a controlled artifact. An instantiated ledger is mutable operational data under the shared preflight and is never itself treated as a frozen research stimulus or participant evidence. A `SYNTHETIC-REHEARSAL` instance uses only `SYN-` IDs, may support a documented preflight drill, can never be converted to live use, and never counts as participant evidence. A `LIVE-FIELDING` instance is prohibited until the same-version written P0-04 `GO` exists.

## Instance control block

~~~text
FORM P04-ASG-CTL — RESTRICTED MUTABLE INSTANCE CONTROL
Instance mode: SYNTHETIC-REHEARSAL / LIVE-FIELDING
Material-pack version/digest: [REQUIRED]
Blank assignment-template version/digest: [REQUIRED]
Mutable instance ID and approved restricted location: [REQUIRED]
Approved named access group: [REQUIRED]
Frozen first reveal-order ID: RVL-AB / RVL-BA
Frozen scenario schedule version/digest: [REQUIRED]
Frozen latency schedule version/digest: [REQUIRED]
Approved retention/deletion date and provider limits: [REQUIRED]
Named privacy/data owner verification and date/time PT: [REQUIRED]
P0-04 authorization record: [SYNTHETIC-REHEARSAL ONLY — NO GO CLAIMED /
  REQUIRED same-version written GO for LIVE-FIELDING]
~~~

## Row-consumption rules

- Assign the next unused `ASG-__` row only after eligibility, age/location re-attestation, comprehension `PASS`, affirmative consent, and deletion-token issuance/lookup verification all pass.
- In `SYNTHETIC-REHEARSAL` mode, simulate those gates with invented `SYN-` records, label every study/deviation ID `SYN-`, and record no real person or contact. Never rename or reuse the rehearsal instance for live fieldwork.
- In `LIVE-FIELDING` mode, verify the same-version written P0-04 `GO` before the first row assignment; absence, expiry, or mismatch is a hard stop.
- A row is consumed when substantive questioning or the first controlled stimulus begins. A withdrawal or halt after that point keeps the row and disposition; never recycle it to manufacture balance.
- A screen failure, consent failure, or pre-substantive withdrawal receives no exposure and does not consume a row. Record that outcome only in its approved screener/consent disposition, not in this ledger.
- `START` means the exact `RVL-AB` or `RVL-BA` choice frozen in the control block; `INVERSE` means the other reveal-order ID.
- Record planned and actual reveal, scenario, and latency order IDs. Any difference requires a `P04-DEV-__` identifier, minimum non-sensitive category, affected materials, immediate action, named reviewer, and disposition. Detailed incident content belongs only in the approved restricted incident system.
- Do not overwrite a consumed row. Corrections are append-only, dated, attributable, and linked by correction ID.

## Restricted mutable assignment ledger

| Assignment row | Planned reveal slot | Planned scenario-order ID | Planned latency-order ID | Study ID | Actual reveal-order ID | Actual scenario-order ID | Actual latency-order ID | Deviation ID or `NONE` | Disposition code | Named verifier / date-time PT |
|---|---|---|---|---|---|---|---|---|---|---|
| `ASG-01` | `START` | `SCN-01` | `LAT-01` |  |  |  |  |  |  |  |
| `ASG-02` | `INVERSE` | `SCN-02` | `LAT-02` |  |  |  |  |  |  |  |
| `ASG-03` | `START` | `SCN-03` | `LAT-03` |  |  |  |  |  |  |  |
| `ASG-04` | `INVERSE` | `SCN-04` | `LAT-04` |  |  |  |  |  |  |  |
| `ASG-05` | `START` | `SCN-05` | `LAT-01` |  |  |  |  |  |  |  |
| `ASG-06` | `INVERSE` | `SCN-01` | `LAT-02` |  |  |  |  |  |  |  |
| `ASG-07` | `START` | `SCN-02` | `LAT-03` |  |  |  |  |  |  |  |
| `ASG-08` | `INVERSE` | `SCN-03` | `LAT-04` |  |  |  |  |  |  |  |
| `ASG-09` | `START` | `SCN-04` | `LAT-01` |  |  |  |  |  |  |  |
| `ASG-10` | `INVERSE` | `SCN-05` | `LAT-02` |  |  |  |  |  |  |  |

## Deviation and correction log

~~~text
FORM P04-DEV-01 — MINIMUM RESTRICTED DEVIATION/CORRECTION ENTRY
Deviation or correction ID: [P04-DEV-__ / P04-COR-__]
Assignment row and study ID: [REQUIRED]
Date/time PT and named operator: [REQUIRED]
Category: WRONG-REVEAL-ORDER / WRONG-SCENARIO-ORDER / WRONG-LATENCY-ORDER /
  REPEATED-OR-OMITTED-STIMULUS / MATERIAL-VERSION-MISMATCH / TIMING-TOOL-FAILURE /
  OTHER-APPROVED-NON-SENSITIVE
Planned IDs: [REQUIRED]
Actual IDs: [REQUIRED]
Immediate control action: [PAUSED / STOPPED / CONTINUED ONLY UNDER APPROVED RULE]
Affected evidence IDs: [NONE / REQUIRED]
Incident ID if separately triggered: [NONE / RESTRICTED ID ONLY]
Session disposition and countability: [REQUIRED]
Named A10 review and date/time PT: [REQUIRED]
Append-only correction link if needed: [NONE / P04-COR-__]
~~~

Current result: **NO-GO.** This blank template records no live assignment, completed dry run, participant evidence, approval, or gate closure.
