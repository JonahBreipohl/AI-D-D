# Phase 0 evidence and research artifact index

Status: **Navigation and status-control page only; it is not participant evidence, an approval, a gate decision, or production authorization**  
Current through: **2026-09-25**

## Hard boundary

- The completed internal baselines are P0-02 and the owner-accepted P0-03 contract: the base specification accepted 2026-09-18 plus Amendment 01 accepted and in force 2026-09-23.
- Advisory audits check document coherence and deterministic coverage. They are not named-human rules, scene, provenance, privacy, safety, accessibility, legal, operational, or fielding approvals.
- P0-04 has **0 of 5** required interviews. P0-05 has **0 of 3** required qualifying completions. No participant result is claimed anywhere in this index.
- The P0-04 material pack v0.1 and blank restricted assignment-ledger template v0.1 are desk-review artifacts only. They contain no live assignment or participant evidence, close no preflight row, and do not authorize recruitment or fielding.
- P0-06 remains provisional, `SPEC_ONLY / NOT IMPLEMENTED`, and `P0-05 NOT OBSERVED` until real P0-05 evidence and the required A1/A7/A6 reviews exist.
- P0-07 v0.1 is a desk-authored review draft, `SPEC_ONLY / NOT IMPLEMENTED`, and not accepted. It admits no generic runtime ruling: the only bounded ruling is `AM01-R1`.
- P0-09 v0.1 is a desk-authored downstream review draft, `NOT IMPLEMENTED`, with no executed model traces or provider selection. Because P0-07 remains unaccepted, P0-09's dependency and acceptance remain open; its rates, budgets, and candidate classes are sensitivity inputs, not final gates.
- P0-10 v0.1 is a desk-authored downstream review draft, `NOT IMPLEMENTED`, with no executed security test, provider/runtime selection, or legal conclusion. Because P0-07 remains unaccepted, P0-10's dependency and acceptance remain open; its diagram, threats, controls, fixtures, and California-facing questions are planning inputs, not proof.
- `P0-08-pre` scene/provenance packet v0.1 is materialized only as a quarantined desk-review draft; unresolved `UNKNOWN` content blocks every use, `F04` and every required human review remain open, and P0-08 is not complete.
- Recruitment and human research remain **NO-GO**. G0 remains closed. No production implementation is authorized.

The `evidence/` directory contains accepted control baselines as well as provisional specifications. A file location or an advisory review does not turn a draft, dry-run input, or protocol into observed evidence.

## Accepted control baselines and records

| Artifact | Controlled version or date | Current status | Acceptance and review boundary |
|---|---|---|---|
| [P0-02 SRD source pin and content policy](P0-02-srd-source-and-content-policy.md) | SRD 5.2.1 English pin, verified 2026-09-17 | Complete as the Phase 0 source pin and initial internal policy | Records source-integrity and policy evidence. It is not public/commercial legal clearance; qualified review remains open. |
| [P0-03 vertical-slice specification](P0-03-vertical-slice-spec.md) | Base accepted 2026-09-18; amended 2026-09-23 | Accepted, active research contract when read with Amendment 01 | Independent planning-coherence audit passed and human acceptance was recorded 2026-09-18; the amendment contract audit and combat-state walk-through passed and human acceptance was recorded 2026-09-23. This does not authorize fielding or production. |
| [P0-03 Amendment 01](P0-03-amendment-01-proposed.md) | Amendment 01, effective 2026-09-23 | Owner-accepted and in force; controls conflicts with the base P0-03 text | Independent contract audit and combat-state walk-through passed; human-owner acceptance is recorded. It resolves `B-01` through `B-11` but does not complete P0-06 or clear a human-research gate. The legacy filename is retained for link stability. |
| [Owner decision log](../08-owner-decision-log.md) | Living log; decisions recorded through 2026-09-25 | Controlling record of owner choices and acceptances | Records the initial defaults, California jurisdiction, base P0-03 acceptance, Amendment 01 acceptance, and authorization for continued desk-only work while human research is deferred. It is not participant evidence. |

## Provisional specifications and research materials

| Artifact | Exact version | Current status | Review and evidence boundary |
|---|---|---|---|
| [P0-06 coverage matrix](P0-06-coverage-matrix.md) | Provisional draft prepared 2026-09-18; Amendment 01 incorporated 2026-09-23 | Incomplete; all coverage remains `SPEC_ONLY / NOT IMPLEMENTED` and `P0-05 NOT OBSERVED` | Independent acceptance, amendment-crosswalk, and deterministic combat-state audits passed after repair. Human A1/A7/A6 traceability, provenance, and test-coverage review plus real P0-05 evidence remain open. |
| [P0-06 operator baseline](P0-06-provisional-operator-baseline-v0.2.md) | v0.2, 2026-09-23 | Dry-run input only; not fielding authorization and not P0-06 completion | Independent amendment-crosswalk and deterministic combat-state audits passed after repair. Named-human rules review and a version-matched operational dry run remain open. |
| [P0-07 resolution lanes and authority contract](P0-07-resolution-lanes-v0.1.md) | v0.1, 2026-09-25; document ID `P0-07-RESOLUTION-LANES` | Desk-authored review draft; `SPEC_ONLY / NOT IMPLEMENTED`; not accepted and P0-07 not complete | Defines deterministic resolution, only bounded ruling `AM01-R1`, unsupported/clarify, visibility, pre-roll commitment, correction, fallback, and handoffs. Advisory contract/structural review does not substitute for A1/A2/A6/A0/human review, final P0-06 reconciliation, or acceptance. It authorizes no fielding or production. |
| [P0-09 model-turn choreography and full-trace sensitivity](P0-09-model-turn-choreography-and-sensitivity-v0.1.md) | v0.1, 2026-09-25; document ID `P0-09-MODEL-TURN-SENSITIVITY` | Desk-authored review draft; `NOT IMPLEMENTED`; dependency open; not accepted and P0-09 not complete | Budgets the complete correlated proposal, one repair, child/tool/random, apply, narration, cache/stream, fallback, and telemetry path and provides provider-neutral cost/latency sensitivity. It uses no executed trace, makes no vendor commitment, does not finalize ADR-0007/0015 or provisional gates, and cannot satisfy its unaccepted P0-07 dependency. |
| [P0-10 visibility- and safety-aware data flow and threat model](P0-10-data-flow-and-threat-model-v0.1.md) | v0.1, 2026-09-25; document ID `P0-10-DATA-FLOW-THREAT-MODEL` | Desk-authored review draft; `NOT IMPLEMENTED`; dependency open; not accepted and P0-10 not complete | Defines the provider-neutral trust/data-flow map, classifications, safety/delete/export linearization, authorization/injection/DoW/secret/provider threats, controls, fixtures, incident baseline, and qualified-review queue. It explicitly blocks static client provider secrets, proves no mitigation, reaches no legal conclusion, and cannot satisfy its unaccepted P0-07 dependency. |
| [P0-04/P0-05 human preflight](../research/P0-04-05-human-research-preflight.md) | Current file; no document version declared | Operational draft; NO-GO | Independent planning-coherence audit passed 2026-09-23. Exact values, named humans, qualified reviews, dry runs, and study-specific human GO signatures remain open. It records no recruitment, approval, or participant result. |
| [P0-04 interview protocol](../research/P0-04-player-interview-protocol.md) | Current file; no document version declared | Protocol ready only after preflight; **0 of 5 interviews** | Independent planning-coherence audit passed 2026-09-18. Human preflight and real participant evidence remain required. |
| [P0-04 material pack](../research/P0-04-material-pack-v0.1.md) | v0.1, 2026-09-24; document ID `P0-04-MATERIAL-PACK` | Desk-review draft / NO-GO; **0 of 5 interviews** | Independent fidelity/structure review passed 2026-09-24. It materializes controlled invitation, screening, consent, stimulus, moderator, note, synthesis, manifest, and rehearsal forms, but all exact operational values, named-human and qualified reviews, accessibility/content review, synthetic rehearsal evidence, and signed GO remain open; it is not participant-facing. |
| [P0-04 restricted assignment-ledger template](../research/P0-04-assignment-ledger-template-v0.1.md) | v0.1, 2026-09-24; document ID `P0-04-ASSIGNMENT-LEDGER-TEMPLATE` | Blank restricted template / NO-GO; no live IDs or dispositions | Its separation and trace fields passed advisory review. It keeps mutable study/order/disposition tracking outside the frozen material pack; a live instance may exist only in an approved restricted store after same-version P0-04 authorization, and this blank template is not operational evidence. |
| [P0-05 Wizard-of-Oz protocol](../research/P0-05-wizard-of-Oz-protocol.md) | Current file; no document version declared | Accepted P0-03 dependency satisfied; `P0-08-pre` v0.1 materialized as a review draft with `F04` open; operationally NO-GO; **0 of 3 qualifying completions** | Independent planning-coherence audit passed 2026-09-18. The scene/provenance reviews and freeze, human preflight, other required human reviews, version-matched dry run, and real sessions remain open. |
| [P0-05 run pack](../research/P0-05-run-pack-v0.2.md) | v0.2, 2026-09-23 | Superseding fail-closed packet; NO-GO; no participant evidence | Independent acceptance, amendment-crosswalk, and deterministic combat-state audits passed after repair. Human rules/scene review, operational dry run, and fielding approval remain open. |
| [P0-05 scene/provenance packet](../research/P0-05-scene-provenance-packet-v0.1.md) | v0.1, 2026-09-23; document ID `P0-05-SCENE-PROV-PACKET` | `P0-08-pre` QUARANTINED DESK REVIEW / NO-GO; `F04` OPEN; **0 of 3 qualifying completions** | Independent contract/ledger review passed after repair, but this is not A5/A7 approval. It contains `UNKNOWN` objects, so P0-02 blocks every prompt, fixture, model-context, dry-run, participant, corpus, export, and release use. `F04` requires named A5/A7 approval of the same resolved, frozen packet and hash. Human rules review and version-matched dry-run evidence remain separate open readiness requirements. |
| [P0-05 synthetic dry-run kit](../research/P0-05-dry-run-kit-v0.1.md) | v0.1, 2026-09-23 | Desk-authored template / synthetic rehearsal only; `F12`, `F13`, and `F14` OPEN; **0 of 3 qualifying completions** | Independent contract/structure verification passed after repair. It remains non-operational evidence, not a completed dry run or participant session; human review, actual tools/operations, named staff, a frozen manifest, and a version-matched end-to-end human dry run remain open. |
| [P0-05 run pack, historical](../research/P0-05-run-pack-v0.1.md) | v0.1, 2026-09-18 | Superseded 2026-09-23; never field | Retained only for change history. Its independent structural audit is advisory and records no session or result. |

## P0-08 two-stage sequencing

The [backlog](../03-backlog-phase-0-to-2.md) separates one task into two controlled stages:

1. `P0-08-pre` depends on P0-02 and the accepted P0-03 contract. [Version 0.1](../research/P0-05-scene-provenance-packet-v0.1.md) is now materialized as a quarantined desk-review draft. It must resolve every blocked object and receive named A5/A7 approval on the same frozen version and hash to close `F04`; the separate human rules review and all other P0-05 gates must also pass before fielding.
2. P0-05 uses that frozen packet and produces controlled participant observations only after every human fielding gate closes.
3. `P0-08-final` depends on P0-05 and incorporates controlled findings into the final original adventure graph, safety profile, and provenance ledger.

`P0-08-pre` is currently **MATERIALIZED / QUARANTINED DESK REVIEW / `F04` OPEN**. It is not an admitted research input while any object remains unresolved, not participant evidence, and not proof that P0-08 is complete. P0-08 remains incomplete until `P0-08-final` passes its done-evidence standard.

## Observed evidence counts

| Workstream | Required denominator | Observed qualifying evidence | Current disposition |
|---|---:|---:|---|
| P0-04 representative-player interviews | 5 | 0 | Not started; recruitment and interviews remain NO-GO |
| P0-05 facilitated prototype completions | 3 | 0 | Not started; recruitment and sessions remain NO-GO |
| P0-06 incorporation of P0-05 findings | Completed P0-05 evidence set | 0 | `P0-05 NOT OBSERVED`; matrix and operator baseline remain provisional |

No protocol, template, synthetic walkthrough, advisory audit, or dry run counts toward either human-participant denominator.

## Human and operational blockers

Before any recruitment or participant contact, the applicable frozen materials must have all of the following:

- named human role owners, backups, reviewers, and authorization signers;
- the versioned `P0-08-pre` scene/provenance packet with A5/A7 review;
- field-by-field human rules review of the exact operator baseline and scene/run-pack crosswalk;
- exact consent, privacy, incentive, recording, retention, deletion, incident, report, safety, boundary, and accessibility values and materials, including appropriate qualified California-facing review;
- version-matched dry runs of rules/state, pause/stop/report, deletion, incident handoff, accessibility, and the complete end-to-end packet;
- a frozen manifest and separate, fully signed P0-04 or P0-05 human GO block, as applicable.

An advisory audit, owner acceptance of the scenario contract, or participant willingness cannot substitute for these closures.

## Pinned rules source

| Field | Pinned value |
|---|---|
| Document | [SRD 5.2.1 English PDF](../../../third_party/srd/SRD_CC_v5.2.1.pdf) |
| Document ID | `wotc-srd-5.2.1-en-cc-by-4.0` |
| File size | 6,031,375 bytes |
| SHA-256 | `8974902d109d6e63672d7c490bde9ccf052410503d9cfa768237154fbc5e3d87` |
| Metadata | [SOURCE.json](../../../third_party/srd/SOURCE.json) |
| Checksum sidecar | [SRD_CC_v5.2.1.pdf.sha256](../../../third_party/srd/SRD_CC_v5.2.1.pdf.sha256) |
| Notice | [NOTICE.md](../../../third_party/srd/NOTICE.md) |

Recompute and compare the checksum before any ingestion run. A mismatch is a hard stop, not permission to upgrade or substitute a source.
