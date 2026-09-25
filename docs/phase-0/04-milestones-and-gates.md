# Milestones and review gates

Status: **Gate plan accepted by the owner on 2026-09-17; P0-03 accepted 2026-09-18 and Amendment 01 accepted/in force 2026-09-23; human research remains NO-GO; G0 remains closed; no calendar commitment**

The order is evidence-driven. A milestone finishes when its exit evidence passes, not when its target date arrives. Human approval is required at each phase boundary.

## Planning assumptions and rough order of magnitude

For a small experienced team with roughly three full-time technical contributors plus part-time product research, content, QA, and licensing support:

| Phase | Rough calendar range | Main uncertainty |
|---|---:|---|
| Phase 0 | 2–3 weeks | Owner decisions, player access, scope of coverage matrix |
| Phase 1A | 6–10 weeks | Rules edge cases, event/replay semantics, dice trust protocol |
| Phase 1B, approved mock-only and parallel | 1–2 weeks | Model access, evaluation corpus, structured-output reliability |
| Phase 2F, inactive contingency if Phase 1B is withdrawn | 1–2 weeks | Full-turn structured output, safety/visibility, latency, and cost feasibility |
| Phase 2 | 5–8 weeks | Model quality, pacing, visibility isolation, playtest iteration |

These are class-5 estimates, not delivery promises. A solo implementer, intermittent staffing, a broader coverage matrix, or delayed decisions can multiply them. Re-estimate after P0-16 and again after P1A-13.

## M0.1 — Decision and evidence lock

**Outcome:** The team knows who it is building for, what exact slice it will prove, which material it may use, and what claims it intends to make.

**Required evidence:**

- D1–D15 owner decisions or explicit deferrals with safe defaults.
- Pinned SRD release/checksum and licensing/provenance posture.
- Target-user/problem evidence from at least five interviews.
- Findings from at least three facilitated no-code/paper prototype sessions.
- Exact Phase 2 slice and precommitted success targets; cost/latency values remain explicitly provisional until full-turn P1B-05 or P2F-05 evidence.
- Explicit correction/dispute authority, Transparent Guide persona, retention/export/delete posture, content boundaries/stop controls, and full-turn choreography hypothesis.

**Reviewers:** A0, A7, A10, human owner.

**Stop/change triggers:** Users do not experience the target problem; trust or pacing requires a fundamentally different interaction; desired content cannot be licensed; the owner will not accept the recommended age/data/cost boundary.

**Current position (2026-09-24):** The original P0-03 slice and Amendment 01 are accepted; together they are the active P0-05/P0-06 research contract, and Amendment 01 controls any conflict. Its eleven resolutions are incorporated into the provisional P0-06 matrix, operator baseline v0.2, and fail-closed P0-05 run pack v0.2. The P0-05 rules/state dry-run kit passed advisory contract review but remains non-operational; `P0-08-pre` v0.1 passed a structural/contract audit but is quarantined because unresolved `UNKNOWN` expression blocks every prompt, fixture, dry-run, participant, corpus, export, and release use. The P0-04 material pack v0.1 and blank restricted assignment-ledger template passed advisory fidelity/structure review but remain desk-review controls. M0.1 remains incomplete: the human preflight is still NO-GO, the interview and prototype counts remain 0 of 5 and 0 of 3, and named-human approvals, qualified reviews, operational rehearsals, and real participant evidence are still required. No recruitment or human research is authorized; G0 remains closed and none of these drafts or advisory audits authorizes production.

## M0.2 — Contract and risk baseline

**Outcome:** Builders can work independently without inventing incompatible authority, visibility, content, or error behavior.

**Required evidence:**

- Complete rules/content coverage matrix with explicit unsupported behavior.
- Three resolution lanes and fairness/persona policy.
- Data-flow diagram and threat model.
- Draft commands, events, projections, AI proposals, adventure, errors, and telemetry contracts with fixtures.
- Test strategy, severity rubric, injection/visibility/content-safety corpus plan, full-turn cost model, dice protocol proposal, and runtime/persistence ADR proposal.
- Risk register has owner, early warning, prevention, contingency, and next review for every critical/high risk.

**Reviewers:** A0–A8; A10 for research-facing interfaces; human owner for policy choices.

**Gate:** **G0 — Phase 0 approval.** A6 confirms the system is testable, A7 confirms provenance controls, A8 confirms measurable economics, A0 confirms contract coherence, and the human explicitly authorizes Phase 1.

## M1.1 — Deterministic mechanics spine

**Outcome:** The entire accepted slice can be resolved headlessly without a model.

**Required evidence:**

- Reproducible selected-SRD records with source traceability.
- Commands validate shape, authority, visibility, phase, resources, and invariants.
- Versioned events replay to identical state; duplicate/out-of-order commands and corrections behave as specified.
- CSPRNG dice and accepted audit/verification protocol work through an independent verifier.
- All in-scope checks, combat, conditions, resources, spatial zones, pregen features, creature abilities, and hazards pass direct and generated tests.

**Reviewers:** A1, A3, A6, A7.

## M1.2 — Headless slice gate

**Outcome:** A fresh checkout can run and inspect the slice mechanics as a durable, documented artifact.

**Required evidence:**

- 100% of declared mechanics linked to source and test; unsupported mechanics reject explicitly.
- At least 10,000 generated state transitions with zero invariant or replay mismatch.
- No critical/high correctness, authority, replay, or provenance issue.
- Runnable demonstration covers success, failure, correction/fork, save/resume, and dice audit.
- Documentation and fixtures match actual contract versions.

**Required Phase 1B evidence:** The approved mock-only AI feasibility report must show structured proposal, visibility isolation, content-safety/stop behavior, and full-turn latency/cost viability before affected contracts harden. Phase 2F remains only a documented contingency if the owner withdraws Phase 1B before it completes.

**Gate:** **G1 — Phase 1 approval.** A6 and A7 sign their evidence and A0 confirms contract conformance. If Phase 1B passed, the human may authorize AI integration using the amended ADR-0007/0015 and finalized gates. If the owner instead withdraws Phase 1B before completion, G1 can authorize only the Phase 2F contingency; integration remains blocked until P2F-05 and human acceptance. Failure returns to coverage/contract design rather than adding prompt exceptions.

## M2.1 — Integrated local alpha

**Outcome:** One player can complete the original slice locally with one persona, durable state, visible rulings/dice, and safe failure behavior.

**Required evidence:**

- The model proposes only through typed tools; deterministic validation is the sole path to state.
- Subjective rulings and consequences are recorded before a roll.
- Exact narration is persisted as non-authoritative output; state can be replayed independently.
- Public, player-private, and GM-private information remain separated in storage, retrieval, prompts, UI, and telemetry.
- Phase 2 game records remain local with export/delete controls; centralized telemetry is metadata-only under the accepted retention policy.
- Lines/veils are applied as policy inputs, and pause/stop bypasses the model and halts state progression.
- Spend and latency circuit breakers, provider outage behavior, retry cap, and deterministic fallback work.
- Minimum accessible UI exposes status, turn/spotlight, rules trace, and dice audit.

**Reviewers:** A1–A8.

## M2.2 — Technical release candidate

**Outcome:** The slice is safe enough for preregistered external playtesting.

**Required evidence:**

- First-pass tool validity ≥95%; ≥99.5% after one retry; fallback <1% on the fixed suite.
- Zero illegal state mutation, zero visibility-boundary disclosure, zero disallowed-content success, and zero safety-stop bypass on the fixed suites; every visibility disclosure is classified critical.
- 100% engine-covered resolutions correct against accepted fixtures.
- Time to first meaningful content p50 ≤2 s and p95 ≤5 s; full resolution p95 ≤10 s, or owner-approved replacements.
- Every call records purpose, requested/resolved model snapshot, tier/region, prompt/persona/adventure/tool-schema versions, provider request ID, input/cache-write/cache-read/output/reasoning tokens, price-catalog version, timing, engine rejection, retry, fallback, and finish status without raw private text in operational telemetry.
- The request ledger reconciles within 2% of the provider’s daily usage/cost, and tokens per turn alert at more than 25% above the approved baseline.
- Full logical-turn, text-only three-hour projected inference spend is p50 under $1 and p95 under $2 on the selected balanced tier, or meets an explicitly owner-approved replacement.
- A7’s attribution/provenance checklist passes.

**Reviewers:** A6, A7, A8; A0 adjudicates only scope/contract questions, not their independent evidence.

## M2.3 — Validated vertical slice

**Outcome:** Representative players can finish, understand, trust, and enjoy the slice at acceptable cost and latency.

**Required evidence:**

- At least 80% of a minimum 10 representative participants finish without developer rescue or softlock.
- At least 70% would voluntarily play again.
- Median fun and fairness/trust are each at least 4/5.
- No required scene is unreachable; success, failure, and recovery are observed or directly tested.
- Real-trace model bake-off supports the provisional model/routing decision.
- Known failures and unsupported actions are understandable to players and recover safely.
- Participants can set content boundaries and use pause/stop without model resistance or an unintended state transition.

**Gate:** **G2 — Phase 2 go/change/stop.** A6, A7, A8, and A10 submit independent reports. The human decides whether to proceed to multiplayer, repeat discovery, narrow/alter the product, or stop. Passing technical gates does not overrule poor human-play evidence.

## Common definition of done

Every completed build task is:

- **Tested:** requirement and failure paths are covered at the appropriate level.
- **Documented:** public contract, assumptions, supported/unsupported behavior, and operational failure mode are current.
- **Contract-conformant:** producer and consumer checks pass against the approved version.
- **Observable:** latency, error, cost, and correlation data exist without unnecessary sensitive content.
- **Provenance-safe:** code/content/source/license records are complete for its outputs.
- **Demonstrated:** a reviewer can reproduce the result in a fresh environment.
- **Reviewed:** no task owner self-approves a required independent gate.

## Gate discipline

- Product, safety, correctness, and human-play thresholds are set before tests and are not weakened after results merely to advance a phase. Phase 0 cost/latency targets are explicitly provisional because no full-turn trace exists; P1B-05 or P2F-05 must finalize or replace them, with rationale and owner approval, before integration—not after Phase 2 results are known.
- A critical rules, authorization, privacy, secret-leak, provenance, or data-loss defect is ship-blocking.
- Event-history “undo” is a compensating/fork event; no gate accepts silent mutation of prior authoritative events.
- Model/provider updates rerun the pinned AI evaluation suite before adoption.
- Contract changes identify every affected consumer, migration, fixture, and rollback plan.
