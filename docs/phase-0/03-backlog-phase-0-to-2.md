# Phase 0→2 backlog

Status: **Owner-approved sequencing baseline; P0-01 through amended P0-03 complete; recruitment and human research remain NO-GO; implementation tasks remain gated**

## Progress

- **P0-01 — Complete (2026-09-17):** The owner approved every recommended default in D1–D15, approved the Phase 1B mock-only feasibility spike, and accepted the success-gate approach subject to full-turn cost/latency finalization at P1B-05.
- **P0-02 — Complete (2026-09-17):** The official SRD 5.2.1 PDF, SHA-256, source metadata, exact notice, and fail-closed reusable/runtime provenance policy were verified and independently reviewed.
- **P0-03 — Complete; Amendment 01 in force (2026-09-23):** The owner accepted the independently audited *The Signal at Glasswater Weir* baseline on 2026-09-18 and Amendment 01's deterministic refinements in full on 2026-09-23. The base specification plus Amendment 01 is the active research contract, and the amendment controls conflicts.
- **P0-04 — Review materials materialized; evidence pending:** The protocol, material pack v0.1, and blank restricted assignment-ledger template are desk-review controls only and passed advisory fidelity/structure review. The shared preflight remains operationally NO-GO until exact values, named humans, qualified reviews, rehearsals, and the signed P0-04 authorization are complete. At least five real representative-player interviews remain; none are claimed.
- **P0-05 — Fail-closed run pack v0.2 drafted; evidence pending:** Amendment 01 is incorporated into the superseding packet and operator baseline. The `P0-08-pre` scene/provenance packet v0.1 is materialized only as a quarantined `REVIEW DRAFT / NO-GO`; its `UNKNOWN` objects block prompt, fixture, dry-run, and participant use. `F04` requires A5/A7 approval of the same resolved, frozen packet; the separate human rules review, operational preflight, and version-matched dry run also remain open. At least three qualifying real-participant completions remain; none are claimed.
- **P0-06 — Provisional matrix and operator baseline v0.2 drafted; not complete:** Accepted Amendment 01 resolves and incorporates the eleven prior contract blockers. Completion still requires real P0-05 evidence plus A1/A7/A6 traceability, provenance, and test-coverage review.
- **P0-07 — Resolution-lane contract v0.1 drafted; review and acceptance pending:** The [desk-authored review draft](evidence/P0-07-resolution-lanes-v0.1.md) defines deterministic catalog resolution, the sole bounded ruling `AM01-R1`, unsupported/clarify behavior, visibility, commitment, correction, fallback, and downstream handoffs. It is `SPEC_ONLY / NOT IMPLEMENTED`; P0-06 remains provisional and the required A1/A2/A6/A0/human reviews are open, so P0-07 is not complete.
- **P0-08 — Two-stage work; not complete:** The provisional pre-session scene/provenance packet (`P0-08-pre`) now exists as v0.1, but it is a quarantined `REVIEW DRAFT / NO-GO`; `F04` remains open until named A5/A7 reviewers approve the same provenance-resolved, frozen version and hash. Human rules review remains a separate P0-05 readiness requirement. The final adventure graph and provenance ledger (`P0-08-final`) must later incorporate controlled P0-05 findings; only that second stage can complete P0-08.
- **Next desk-only critical path:** Harden and advisory-review P0-07 v0.1 without broadening its authority; final acceptance remains blocked on the P0-06/P0-05 evidence chain and required named-human reviews. P0-09 is the next ordered desk-authorable consumer, but any pre-acceptance draft must stay explicitly provisional and cannot satisfy its dependency. Human research is deferred: recruitment and fieldwork remain NO-GO, G0 remains closed, and no Phase 1 production task is authorized.

Dependencies reference task IDs. Conditional branches use `X OR Y`; unresolved decisions themselves never masquerade as dependencies. “Owner” is accountable for the handoff even when other roles contribute. No task is done merely because a document or first draft exists; its listed evidence must pass review.

P0-08 has two controlled stages to avoid a false cycle. `P0-08-pre` is the provisional public/private scene, dialogue, reveal, ending, and provenance packet derived only from P0-02 and the accepted P0-03 contract. Its v0.1 review draft is now materialized but quarantined: while any object is `UNKNOWN`, P0-02 blocks prompt, fixture, model-context, dry-run, participant, corpus, export, and release use. Named A5/A7 approval of the same resolved, frozen version and hash closes `F04`; the separate human rules review remains an additional P0-05 readiness requirement. The provisional packet is never P0-08 completion evidence. `P0-08-final` follows P0-05, incorporates controlled study findings without silently changing the accepted contract, and is the stage whose done evidence can complete P0-08.

## Phase 0 — Discovery, evidence, and contract baseline

| ID | Task / concrete output | Owner | Depends on | Done evidence |
|---|---|---|---|---|
| P0-01 | Record owner answers to D1–D15 and classify accepted defaults vs. explicit deferrals | A0 + human | — | Decision log has owner/date/rationale; no ambiguous “TBD” affects Phase 1–2 |
| P0-02 | Pin the chosen SRD PDF, checksum it, and issue the initial rules/content allowlist policy | A7 | P0-01 | Source register, checksum, version-specific notice source, allow/deny policy reviewed |
| P0-03 | Define the exact Phase 2 slice: duration, character level/build, persona, scenes, encounter, endings, supported actions, correction/dispute policy, and safety profile | A0 | P0-01 | One-page slice specification accepted by human |
| P0-04 | Interview at least five representative players about current GM-access, trust, latency, UI, and payment problems | A10 | P0-01 | Participant criteria explicitly test the charter’s target-user hypothesis; coded/pseudonymous notes, ranked evidence, privacy-safe disposition, and disconfirming evidence retained |
| P0-05 | Run at least three facilitated paper/Wizard-of-Oz versions of the proposed slice | A10 + A5 | P0-03, P0-08-pre | Full participant disposition; timing, confusion, fun/trust, content-boundary/pause/stop/report observations, unsupported-action log, and controlled revisions |
| P0-06 | Produce a complete rules/content coverage matrix for the slice | A1 | P0-02, P0-03, P0-05 | Every class feature, action, spell, item, condition, creature ability, and spatial rule is included or explicitly unsupported with SRD locator |
| [P0-07](evidence/P0-07-resolution-lanes-v0.1.md) | Define the three resolution lanes: deterministic mechanic, bounded pre-roll ruling, and unsupported/clarify | A1 + A2 | P0-01, P0-03, P0-06 | Examples, inputs, validators, visibility, pre-roll commitment, correction authority, and fallback for each lane accepted |
| P0-08 | First produce `P0-08-pre`, the provisional pre-session scene/provenance packet required by P0-05; after P0-05, produce `P0-08-final`, the finalized original adventure graph, safety profile, and provenance ledger | A5 | `P0-08-pre`: P0-02, P0-03; `P0-08-final`: P0-05 | Final scenes/objectives/failures/recovery/public-private facts incorporate controlled P0-05 findings, map cleanly to coverage and content boundaries, have A5/A7 review, and contain no unknown provenance; the provisional packet alone is never completion evidence |
| P0-09 | Specify end-to-end model turn choreography and produce model/data/vendor plus full-trace cost/latency sensitivity | A8 + A2 | P0-01, P0-03, P0-07 | Every pre-roll call, tool round trip, post-result narration, retry, cache transfer, stream point, and fallback is budgeted; candidate class—not vendor commitment—reviewed |
| P0-10 | Produce a visibility- and safety-aware data-flow diagram and threat model | A3 | P0-01, P0-03, P0-07 | Trust boundaries, retention/deletion, secrets, authorization, prompt injection, content boundaries, stop path, denial-of-wallet, and mitigations reviewed by A6/A7 |
| P0-11 | Specify dice trust claim and compare audit-log vs. commitment protocols | A1 + A3 | P0-01, P0-10 | ADR proposal, threat assumptions, independent verification method, and UX evidence defined |
| P0-12 | Draft versioned command, event, projection, AI-proposal, adventure, safety-stop, error, and telemetry contracts | A1 (technical coordinator) | P0-06–P0-11 | Producers/consumers named; example fixtures; compatibility rules; consumer contract-test plan |
| P0-12A | Evaluate and recommend the implementation/runtime and persistence technology boundary | A1 + A3 | P0-06, P0-10, P0-12 | ADR compares deterministic-library fit, schema/type safety, transactions, event storage, local development, deployment, migration, operations, and reversal cost; no codebase is started |
| P0-13 | Define test strategy, severity rubric, and gate datasets | A6 | P0-03, P0-06, P0-07, P0-10, P0-12 | Requirements-to-test map, invariant catalog, injection/visibility/content-safety corpora, simulation plan, and release severity policy |
| P0-14 | Define human playtest protocol and precommit success targets before seeing Phase 2 results | A10 + A0 | P0-04, P0-05, P0-10 | Recruitment, consent/privacy, lines/veils, stop/report procedure, scoring rubric, rescue definition, and stopping rules approved; cost/latency values are labeled provisional until P1B-05 or P2F-05 full-trace evidence |
| P0-15 | Complete and accept ADR-0001 through ADR-0016 as applicable | A0 + human | P0-01–P0-14, P0-12A | Each ADR names consequences, reversal cost, contracts/tests affected, and owner acceptance; ADR-0007/0015 explicitly record provisional targets and the mandatory amendment/finalization gate |
| P0-16 | Review and baseline all interface contracts | A0 | P0-12, P0-13, P0-15 | A1–A8 acknowledge version; mock producer/consumer tests specified; change process active |
| P0-17 | Phase 0 gate review | A0 + human | All P0 tasks | A6 evidence-plan sign-off, A7 provenance sign-off, budget/data approval, human phase approval |

## Phase 1A — Deterministic mechanics spine, no production AI

Scope is exactly the accepted slice coverage matrix, not all SRD content.

| ID | Task / concrete output | Owner | Depends on | Done evidence |
|---|---|---|---|---|
| P1A-01 | Build a reproducible selected-SRD ingestion/provenance pipeline for in-scope records | A1 | P0-02, P0-06, P0-16 | Every derived field links to source version/location and transformation; unknown/extra content fails validation |
| P1A-02 | Implement canonical IDs, value objects, entities, and state invariants for the slice | A1 | P0-06, P0-16 | Schema validation and invariant/property tests pass; no narrative fields act as authority |
| P1A-03 | Implement command validation including actor, visibility, phase, targets, resources, expected version, and idempotency | A1 + A3 | P1A-02; P1B-05 when the Phase 1B branch is authorized | Unauthorized and semantically illegal but schema-valid fixtures are rejected with stable reason codes |
| P1A-04 | Implement versioned events, deterministic reducers, snapshots, replay, correction/fork semantics, and upcast fixtures | A1 + A3 | P1A-02, P0-16 | Exact state-hash replay, ordering, idempotency, and migration tests pass |
| P1A-05 | Implement server-side CSPRNG dice notation and the accepted verification/audit protocol | A1 | P0-11, P1A-04 | Independent verifier reproduces every completed test roll; production randomness is never seeded for predictability |
| P1A-06 | Implement core checks, saves, attacks, advantage/disadvantage, criticals, damage, healing, resistance/immunity/vulnerability, initiative, and action economy required by the slice | A1 | P1A-02–P1A-05 | Coverage-matrix golden cases and property invariants pass |
| P1A-07 | Implement slice conditions, concentration, death/dying, rests, resources, inventory, spell slots, and recharge behavior | A1 | P1A-06 | Transition/state-machine tests cover apply, stack/replace, expire, interrupt, restore, and invalid paths |
| P1A-08 | Implement zone/range-band movement, reach, opportunity, cover, and area targeting required by the slice | A1 | P0-16, P1A-06 | Spatial examples and ambiguity/fallback cases pass; no grid-only claim is made |
| P1A-09 | Implement only the declared pregen features, spells, items, monster actions, hazards, and encounter rules | A1 | P1A-06–P1A-08 | 100% traceability to P0-06; unsupported content is rejected explicitly |
| P1A-10 | Build generated-state, simulation, replay, and conformance harnesses | A6 | P1A-03–P1A-09 | At least 10,000 transitions with zero invariant/replay mismatch; every declared mechanic has a direct test |
| P1A-11 | Build the headless runnable encounter/slice-mechanics demonstration | A1 | P1A-09, P1A-10 | Fresh-environment run demonstrates success, failure, correction, save/resume, and audit; documentation matches behavior |
| P1A-12 | Rules/provenance/security review | A6 + A7 | P1A-11 | No critical/high correctness or provenance defect; threat mitigations for headless scope verified |
| P1A-13 | Phase 1 gate review | A0 + human | P1A-12 | Coverage, test, replay, audit, docs, and demo accepted; no AI integration is present |

## Phase 1B — Approved isolated model feasibility spike

The owner approved this track on 2026-09-17 because waiting until Phase 2 to learn that structured output, secret separation, latency, or cost is infeasible creates avoidable rework. It is **non-production, uses contract mocks, cannot access the rules engine or authoritative state, and must be discarded or rebuilt for Phase 2**. P1B-05 must finish before P1A-03 hardens the affected contracts.

| ID | Task / concrete output | Owner | Depends on | Done evidence |
|---|---|---|---|---|
| P1B-01 | Create mock state views and engine responses from the frozen contracts | A2 + A6 | P0-16 | Fixtures cover success, rejection, hidden facts, ambiguity, retry, and outage without production integration |
| P1B-02 | Test structured proposal validity and capped retry/fallback across candidate models | A2 | P1B-01 | Versioned results for ≥200 representative turns; failure taxonomy retained |
| P1B-03 | Test visibility isolation, content boundaries/stop, and adversarial player text against mock private facts | A6 | P1B-01 | Zero visibility leaks, disallowed-content successes, and stop bypasses on fixed corpora or spike fails; limitations documented |
| P1B-04 | Measure token, cache, latency, and estimated session cost for the complete multi-call logical turn | A8 | P1B-02 | Reproducible full-trace distributions and three-hour projection, not vendor marketing claims |
| P1B-05 | Recommend whether Phase 2 AI integration is viable and what contract changes are needed | A2 + A8 + A6 | P1B-02–P1B-04 | Written go/change/stop recommendation, any contract revision, ADR-0007/0015 amendments, and final owner acceptance or replacement of cost/latency gates before P1A-03 |

## Phase 2F — Inactive contingency if Phase 1B is later withdrawn

The approved route is P1B. This branch remains documented only as a contingency if the owner later withdraws Phase 1B authorization before it completes. Exactly one of P1B or P2F must complete before production AI integration.

| ID | Task / concrete output | Owner | Depends on | Done evidence |
|---|---|---|---|---|
| P2F-01 | Create mock state views and engine responses from the frozen contracts | A2 + A6 | P1A-13 | Success, rejection, hidden facts, ambiguity, correction, retry, stop, and outage fixtures |
| P2F-02 | Test structured proposal and post-result narration validity with capped retry/fallback | A2 | P2F-01 | Versioned results for ≥200 representative logical turns and retained failure taxonomy |
| P2F-03 | Test visibility isolation, content boundaries, and adversarial player text | A6 | P2F-01 | Zero visibility leaks, disallowed-content successes, and stop bypasses on fixed corpora, or feasibility fails |
| P2F-04 | Measure full-turn tokens, cache, latency, retries, and session cost | A8 | P2F-02 | All inference legs and tool round trips included; reproducible distributions |
| P2F-05 | Issue go/change/stop decision for integration | A2 + A8 + A6 + A0 + human | P2F-02–P2F-04 | Viability, required contract revisions, ADR-0007/0015 amendments, and final owner acceptance or replacement of cost/latency gates before P2-02/P2-04/P2-05 |

## Phase 2 — Local end-to-end vertical slice

| ID | Task / concrete output | Owner | Depends on | Done evidence |
|---|---|---|---|---|
| P2-01 | Finalize one original 60–90 minute machine-readable adventure slice | A5 | P0-08, P1A-09 | Schema-valid content, A7 provenance/safety review clean, success/failure/recovery paths, no unreachable required node |
| P2-02 | Implement provider-neutral model adapter and pin evaluated model configurations | A2 | P0-09, P0-16, P1B-05 OR P2F-05 | Same evaluation harness runs against at least two candidates; timeouts/version/fallback semantics pass |
| P2-03 | Implement the Transparent Guide persona with measurable policy and safety fields | A2 | P0-01, P0-07, P2-02 | Persona changes allowed dimensions only; mechanics/fairness/content-boundary invariance tests pass |
| P2-04 | Implement visibility-scoped context assembly, rolling summary, retrieval, corrections, and hard token budget | A2 + A3 | P0-01, P0-10, P2-01, P1B-05 OR P2F-05 | Public/player-private/GM-private tests; provenance/correction behavior; deterministic overflow fallback |
| P2-05 | Implement the pre-roll propose/commit → validate/roll/apply → post-result narrate choreography | A2 + A1 | P1A-13, P2-02–P2-04, P1B-05 OR P2F-05 | No model path writes state; no outcome streams before authority; rejected proposals cannot leak into state; full-turn fallback and narration reference the committed result |
| P2-06 | Implement local session coordination, durable event/narration persistence, resume, and export | A3 | P1A-04, P2-05 | Crash/restart reconstructs exact state and preserves original narration; privacy classifications honored |
| P2-07 | Build minimal accessible client for pregen, narrative, choices/free text, state, rules trace, dice audit, lines/veils, and out-of-band pause/stop/report | A4 | P0-16, P2-05, P2-06 | Keyboard/screen-reader/mobile checks; safety stop bypasses model and state progression; unknown/error/offline states visible; client cannot authorize itself |
| P2-08 | Add full-turn cost/latency/retry/fallback instrumentation and spend circuit breaker | A8 + A3 | P2-02, P2-05, P2-06 | Each call records purpose, requested/resolved model, tier/region, schema/content versions, provider request ID, all token/cache/reasoning categories, price-catalog version, engine rejection and finish status; no raw private text; ledger reconciles within 2% daily; >25%-above-baseline token drift alerts; budget breach stops safely |
| P2-09 | Run complete rules, replay, injection, authorization, visibility, content-boundary/stop, denial-of-wallet, and provider-failure suites | A6 | P2-05–P2-08 | Charter thresholds pass; zero visibility-boundary disclosure or stop bypass; no critical/high open defect; exact model/config recorded |
| P2-10 | Conduct internal dogfood and repair material softlocks, pacing, and usability failures | A10 + A5 + builders | P2-09 | No developer-known blocker; changes rerun relevant regression suites |
| P2-11 | Conduct preregistered representative-player test with at least 10 participants | A10 | P0-14, P2-10 | Completion, rescue, fun, trust, replay, latency perception, and qualitative failure evidence captured |
| P2-12 | Re-run cost/model bake-off on real complete logical-turn traces and choose provisional model policy | A8 + A2 | P2-11 | Every inference leg/tool round trip is included; typical/p95 cost and latency meet owner ceiling; quality tradeoff documented; fallback tested |
| P2-13 | Complete technical, provenance, safety, economics, and human-evidence gate reports | A6 + A7 + A8 + A10 | P2-09, P2-11, P2-12 | Independent reports link evidence and unresolved risks; no threshold is retroactively weakened |
| P2-14 | Phase 2 demonstration and owner go/change/stop decision | A0 + human | P2-13 | Fresh-run demo; accepted decision names Phase 3 scope or returns to discovery |

## Post-Phase 2 epics only

Detailed task planning this far out would encode guesses as commitments.

- **Phase 3 — Multiplayer:** hosted authority, identity/session ownership, host/join, out-of-combat spotlight/intent queue, combat turns, reconnect, spectators, conflict/timeouts, multi-seat visibility, initial capacity and abuse controls.
- **Phase 4 — Content and depth:** complete original adventure, broader coverage matrix, persona library, long-session memory, character creation, save/resume UX, balance and authoring tools.
- **Phase 5 — AI party members:** only if D5 is reopened; human-equivalent visibility and rules authority, tactics, personality, agency safeguards.
- **Phase 6 — Hardening and launch:** commercial/privacy/legal review, public moderation and takedowns, disaster recovery, support/onboarding, SLOs, cost optimization, scale testing, launch decision.
