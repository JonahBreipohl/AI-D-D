# AI Game Master — Phase 0 planning pack

Status: **P0-02 and the amended P0-03 research contract are complete; Amendment 01 is accepted and in force; recruitment and human research remain NO-GO; G0 is closed and production implementation is not authorized.**

This repository currently contains planning artifacts only. The proposed product is a transparent, rules-bounded, text-first AI game master for an original fifth-edition-compatible adventure. The initial proof is deliberately narrower than a general-purpose virtual tabletop or a complete digital implementation of every fifth-edition rule.

## Approved direction at a glance

- Build against the pinned **SRD 5.2.1 under CC BY 4.0** baseline.
- Ship an **original, provenance-tracked adventure**. Do not ship or ingest published adventures in v1.
- Validate a **60–90 minute local vertical slice** before multiplayer or broad rules coverage.
- Use a **commercial model API behind a provider-neutral boundary** for the slice, with spend caps and a measured model bake-off. Defer self-hosting and consumer BYOK.
- Use **theater of the mind with explicit zones/range bands**, not a tactical grid.
- Keep v1 **text-only, AI-DM-only, private, invite-only, and adults-only**.
- Use a **Teen/PG-13 content ceiling**, pre-session boundaries, and an out-of-band stop control even though the alpha is adults-only.
- Make every state change deterministic and event-backed. The model may propose typed actions and reference an explicitly accepted bounded ruling, but it may never invent authority or write authoritative state.
- Personas may change presentation and precommitted challenge selection; they may not secretly fudge rolls or change rules semantics.
- Cost and latency must include the complete proposal → tool/roll → outcome-narration turn, not only one convenient inference call.

These are the owner-approved Phase 0 product directions. They authorize the remaining discovery, evidence, contract, and mock-only feasibility work, but not production implementation; that remains gated on G0.

## Planning pack

1. [Project charter](docs/phase-0/00-project-charter.md)
2. [Decision brief](docs/phase-0/01-decision-brief.md)
3. [Agent roster and handoff contracts](docs/phase-0/02-agent-roster-and-contracts.md)
4. [Phase 0→2 backlog](docs/phase-0/03-backlog-phase-0-to-2.md)
5. [Milestones and review gates](docs/phase-0/04-milestones-and-gates.md)
6. [Risk register](docs/phase-0/05-risk-register.md)
7. [Questions for the owner](docs/phase-0/06-owner-questions.md)
8. [Research and evidence notes](docs/phase-0/07-research-and-evidence.md)
9. [Owner decision log](docs/phase-0/08-owner-decision-log.md)
10. [Phase 0 evidence and research artifact index](docs/phase-0/evidence/README.md)
11. [ADR register](docs/adr/README.md)

## Active execution artifacts

- [Evidence and research artifact index](docs/phase-0/evidence/README.md) — controlled map of accepted baselines, provisional materials, evidence counts, source pin, and open human blockers.
- [P0-02 — SRD source pin and content policy](docs/phase-0/evidence/P0-02-srd-source-and-content-policy.md) — complete internal Phase 1–2 baseline; public/commercial qualified review remains later.
- [P0-03 — concrete vertical-slice specification](docs/phase-0/evidence/P0-03-vertical-slice-spec.md) — accepted on 2026-09-18 and governed with Amendment 01 as the active research contract.
- [P0-04 — representative-player interview protocol](docs/phase-0/research/P0-04-player-interview-protocol.md) — ready after the human research/privacy preflight; 0 of 5 interviews completed.
- [P0-04 — interview material pack v0.1](docs/phase-0/research/P0-04-material-pack-v0.1.md) — desk-review draft with consent, screener, stimuli, moderator, note, synthesis, manifest, and dry-run controls; participant use remains NO-GO and 0 of 5 interviews are complete.
- [P0-04 — restricted assignment-ledger template v0.1](docs/phase-0/research/P0-04-assignment-ledger-template-v0.1.md) — blank operational template that keeps live study/order/disposition data outside the frozen material pack; it contains no participant record and authorizes no fieldwork.
- [P0-04/P0-05 — human research preflight](docs/phase-0/research/P0-04-05-human-research-preflight.md) — independently audited operational draft; still NO-GO until named humans, exact values, qualified reviews, and dry runs are complete.
- [P0-05 — Wizard-of-Oz protocol](docs/phase-0/research/P0-05-wizard-of-Oz-protocol.md) — P0-03 is satisfied; `P0-08-pre` v0.1 is quarantined for desk review because unresolved provenance blocks use, and `F04` plus the human fielding gates remain open; 0 of 3 qualifying completions.
- [P0-05 — run pack v0.2](docs/phase-0/research/P0-05-run-pack-v0.2.md) — superseding fail-closed packet with Amendment 01 incorporated; human fielding remains NO-GO. [v0.1](docs/phase-0/research/P0-05-run-pack-v0.1.md) is retained only as history.
- [P0-05 — scene/provenance packet v0.1](docs/phase-0/research/P0-05-scene-provenance-packet-v0.1.md) — quarantined `P0-08-pre` desk-review draft; `UNKNOWN` content blocks prompt, fixture, dry-run, and participant use until resolved, while `F04` A5/A7 review and the separate human rules/fielding gates remain open.
- [P0-05 — synthetic dry-run kit v0.1](docs/phase-0/research/P0-05-dry-run-kit-v0.1.md) — desk-authored template only; not operational or participant evidence and closes no dry-run blocker.
- [P0-06 — provisional operator baseline v0.2](docs/phase-0/evidence/P0-06-provisional-operator-baseline-v0.2.md) — exact dry-run input; human rules review and a version-matched dry run remain open.
- [P0-06 — provisional coverage matrix](docs/phase-0/evidence/P0-06-coverage-matrix.md) — Amendment 01 resolves `B-01` through `B-11`; P0-05 evidence and required reviews are still needed before completion.
- [P0-07 — resolution lanes and authority contract v0.1](docs/phase-0/evidence/P0-07-resolution-lanes-v0.1.md) — desk-authored review draft: deterministic catalog entries, only bounded ruling `AM01-R1`, and unsupported/clarify; acceptance and implementation remain open.
- [P0-09 — model-turn choreography and full-trace sensitivity v0.1](docs/phase-0/evidence/P0-09-model-turn-choreography-and-sensitivity-v0.1.md) — provisional downstream review draft covering every proposal, repair, child/tool/random stage, post-result narration, cache/stream point, fallback, and privacy-safe ledger; P0-07 remains unaccepted, so the dependency and P0-09 acceptance remain open.
- [P0-10 — visibility- and safety-aware data flow and threat model v0.1](docs/phase-0/evidence/P0-10-data-flow-and-threat-model-v0.1.md) — provisional desk-review artifact covering trust boundaries, authorization, injection, visibility, stop/delete/export races, denial-of-wallet, secrets, provider/relay processing, telemetry, retention, fixtures, and qualified-review questions; P0-07 remains unaccepted and no mitigation is implemented or proven.
- [P0-03 Amendment 01 — deterministic baseline](docs/phase-0/evidence/P0-03-amendment-01-proposed.md) — accepted and in force 2026-09-23; it controls any conflict with the base P0-03 text.
- [Pinned SRD metadata, notice, checksum, and PDF](third_party/srd/) — integrity-verified source package.

## Gate status

| Gate | Status | Why |
|---|---|---|
| Phase 0 owner decisions | Complete | On 2026-09-17 the owner approved all recommended defaults in D1–D15 plus the Phase 1B spike and proposed success-gate approach; California, United States is the initial jurisdiction. |
| Phase 0 evidence and contracts | In progress | P0-02 and the amended P0-03 research contract are complete. Amendment 01 is incorporated into the provisional matrix, operator baseline v0.2, and run pack v0.2. P0-07 resolution-lane contract v0.1 is a desk-authored review draft, not an accepted or implemented contract. P0-09 model-turn choreography/sensitivity and P0-10 data-flow/threat-model v0.1 are provisional desk drafts; both explicitly retain their open P0-07 dependency, select no provider/runtime, and prove no implementation. P0-10 also blocks distributed provider use until a reviewed short-lived credential or minimal-relay path replaces any static client secret. The P0-04 material pack v0.1 and its blank restricted assignment-ledger template are desk-review controls only; `P0-08-pre` v0.1 and the P0-05 dry-run kit v0.1 are review/synthetic drafts only. P0-04/P0-05 remain NO-GO pending human preflight, required reviews, operational dry runs, and real participants; P0-06 remains provisional pending evidence and review. Contracts, technical ADRs, and independent gate evidence follow. |
| Contract freeze | Not started | It depends on the decisions above and on a rules/content coverage matrix. |
| Phase 1 implementation | Not authorized | No accepted ADRs or reviewed interface contracts exist. |
| Phase 2 integration | Not authorized | It depends on a verified mechanics spine and model feasibility evidence. |

## Immediate owner response

The owner decisions, including the 2026-09-25 authorization for continued desk-only work, deferral of human research, and direction to prepare provisional P0-10, are preserved in the [decision log](docs/phase-0/08-owner-decision-log.md). [P0-07 v0.1](docs/phase-0/evidence/P0-07-resolution-lanes-v0.1.md) remains provisional, so the downstream [P0-09](docs/phase-0/evidence/P0-09-model-turn-choreography-and-sensitivity-v0.1.md) and [P0-10](docs/phase-0/evidence/P0-10-data-flow-and-threat-model-v0.1.md) drafts cannot satisfy their dependencies or complete those tasks. Phase 0 acceptance remains blocked on the P0-06/P0-05 evidence chain and required named-human/role reviews; provider/legal/security diligence and executed P1B evidence remain later integration gates. Human rules/scene/provenance review, operational dry runs, and fieldwork remain deferred requirements. No recruitment, invitation, screening, interview, prototype session, or participant contact is authorized. G0 remains the authorization boundary for Phase 1 production implementation.
