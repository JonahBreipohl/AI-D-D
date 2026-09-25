# Project charter

Status: **Accepted as the Phase 0 baseline on 2026-09-17; G0 implementation approval still required**  
Planning date: 2026-09-17

## Problem

Small groups often cannot play a tabletop fantasy role-playing session because no human is available or willing to prepare and run it. Existing chatbots can improvise prose, but they lose state, invent rules, leak hidden information, and create dice outcomes players cannot trust. Full virtual tabletops solve maps and connectivity but do not supply a reliable game master.

## Product thesis

A rules-bounded AI game master can run an enjoyable fifth-edition-compatible adventure if creative narration is separated from authoritative mechanics. The model proposes narration, intent interpretations, and bounded rulings; deterministic services validate and apply state changes; players can inspect the rule decision, roll inputs, result, and event history.

The first proof is not “all of fifth edition.” It is one original, 60–90 minute adventure slice with an explicit supported-rules matrix, one player character, one Transparent Guide persona, a social beat, exploration, and one combat encounter. Unsupported actions are identified honestly rather than resolved by invented mechanics.

## Target user

Primary initial user: an adult player already familiar with fifth-edition play who wants a short, text-first session when a human game master is unavailable. The initial operating environment is a private, invite-only alpha. The eventual target is a host plus 2–4 remote adult players, subject to later multiplayer and safety gates.

Not the initial target: minors, public anonymous users, groups seeking a tactical-grid VTT, users expecting licensed campaign settings, or tables that need every optional and edge-case rule.

## Value proposition

- Start quickly with a pre-generated character and no game-master preparation.
- Receive coherent, responsive narration without granting the model authority over rules or state.
- Trust outcomes because rulings are committed before rolls, dice are generated server-side, and state transitions are auditable.
- Recover or replay a session from structured, versioned events without treating prose as the source of truth.

## Phase 0→2 success criteria

Product and play:

- At least 80% of a minimum 10 representative players complete the 60–90 minute slice without developer rescue or a softlock.
- At least 70% say they would voluntarily play again; median fun and fairness/trust ratings are at least 4/5.
- No required story node is unreachable; the slice has a successful ending, a failure ending, and at least one recovery path.

Rules and integrity:

- 100% of declared mechanics map to a pinned SRD section/version and an automated test; unsupported mechanics fail explicitly.
- No model or narrative path can mutate authoritative state except through validated commands and append-only events.
- Replaying a completed turn reconstructs the identical canonical state; no invariant failures occur across at least 10,000 generated state transitions.
- Every random result records its notation, modifiers, advantage state, request context, commitment/audit evidence, raw result, and derived outcome.
- A schema-valid but unauthorized, invisible, wrong-phase, or resource-invalid action is rejected. Retry is capped and ends in a deterministic safe fallback.

AI, safety, cost, and performance:

- At least 95% of model tool calls are valid on the first attempt, at least 99.5% after one retry, and fallback is below 1% on the fixed evaluation set.
- Zero illegal mutations in the versioned adversarial suite. This is a release gate, not a claim of complete security.
- Zero visibility-boundary disclosures, disallowed-content successes, or safety-stop bypasses in the fixed release corpus; every visibility disclosure is automatically critical.
- Streaming time to first meaningful content is p50 ≤2 seconds and p95 ≤5 seconds; complete resolution is p95 ≤10 seconds, unless the owner approves a different budget.
- Every model call records provider, model/version, token counts, latency, cache use, retry/fallback, and turn correlation without placing raw sensitive role-play text in operational telemetry.
- Recommended economic gate for a text-only three-hour session on the selected balanced tier: p50 under $1 and p95 under $2. It is accepted only after the complete multi-call turn—including proposal, tool round trips, post-result narration, retries, and cache traffic—is measured.

## Explicit non-goals through Phase 2

- AI-controlled party members.
- Tactical grid, map editor, line-of-sight engine, or general-purpose VTT features.
- Voice input/output.
- Public anonymous access or support for minors.
- Explicit sexual content, sexual violence, hate-based targeting, encouragement of self-harm, graphic torture/gore, or higher-intensity content profiles.
- Importing, reproducing, summarizing, or adapting published adventures.
- Multiple personas, full character creation, campaign-length memory, or broad homebrew.
- Exhaustive implementation of every SRD class, spell, monster, item, and ambiguous ruling.
- Model-generated dice, direct model state writes, or transcript-as-database behavior.

## Invariants

1. No unlicensed Wizards-derived material ships. Every rules record, text passage, image, map, font, audio asset, and adventure element has recorded provenance and compatible terms. Original project content is allowed; “SRD-only” is not a substitute for an asset provenance system.
2. One exact SRD release is pinned by version and checksum. Content from another edition or from memory is excluded unless separately reviewed and recorded.
3. Randomness comes from a server-side CSPRNG. “Verifiable” will mean a documented commitment protocol and independent verifier; otherwise the narrower term “auditable” will be used.
4. The model proposes; deterministic policy and rules code validate and apply. Subjective rulings are bounded, committed before a roll, and visible in the dispute log.
5. Authoritative state is structured and event-backed. Corrections are compensating or fork events, never silent history edits.
6. Memory and retrieval enforce public, per-player, and DM-private visibility at storage and query time.
7. Player text is hostile input. It receives no authority merely because it is inside a character name, backstory, chat message, or imported field.
8. Personas cannot change post-commit roll outcomes, rules semantics, hidden information boundaries, correction consent, or player agency.
9. Any player-facing safety stop is out of band: it bypasses the model and immediately pauses generation and state progression.
10. No outcome narration is exposed before the authoritative result exists. Cost and latency are measured over the entire logical turn, not a convenient subset of calls.

## Approval boundary

The owner approved D1–D15 and the proposed success-gate approach on 2026-09-17. This charter is now the active discovery baseline. It does not authorize production implementation by itself; G0 still requires the remaining Phase 0 evidence, contracts, independent reviews, and explicit human approval.
