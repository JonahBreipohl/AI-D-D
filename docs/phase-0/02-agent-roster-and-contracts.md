# Agent roster and handoff contracts

Status: **Role structure confirmed; build activation is gated**

No build agent may begin implementation before the owner approves Phase 0 and the relevant ADRs/contracts. “Agent” describes a workstream owner; one person may hold multiple compatible roles, but approval duties must not be self-certified where an independent gate is named.

## A0 — Program lead and chief architect

**Mandate:** Own product coherence, decision records, sequencing, cross-team contracts, phase gates, and escalation to the human owner.

**Owned artifacts:** Charter, decision log, ADR register, roadmap, dependency map, scope/coverage baseline, consolidated risk register, gate decisions.

**Does not own:** Legal acceptance, automated QA sign-off, content authorship, or unilateral changes to owner-approved product policy.

**Handoff contract:** Publishes accepted decisions and versioned contract baselines. Every affected owner must acknowledge a contract change before dependent work merges. Batches true product ambiguities for the human owner rather than allowing local guesses.

## A1 — Game systems architect

**Mandate:** Own the deterministic mechanics spine and the distinction between supported, bounded-ruling, and unsupported actions.

**Owned artifacts:** Canonical game-state model; rules IDs and source traceability matrix; commands, events, reducers, invariants, and reason codes; dice service/verification protocol; character/creature/action/resource/condition/spell data needed by the declared slice; SRD ingestion and provenance validators; headless engine API.

**Does not own:** Narrative generation, persona behavior, adventure prose/plot, networking, client authority, or subjective product policy.

**Handoff contract:** Delivers to A2/A3/A4/A5/A6 a versioned schema bundle containing command and event definitions, state projections, validation errors, compatibility policy, deterministic fixtures, supported-rules matrix, and mock server. Breaking changes require A0 approval and consumer contract-test updates.

## A2 — AI game-master engineer

**Mandate:** Own the bounded model loop that translates visible context and player intent into narration plus structured proposals.

**Owned artifacts:** Provider-neutral model interface; full pre-roll proposal/tool/post-result narration choreography; prompting and instruction hierarchy; one persona and content-safety specification; visibility-aware context assembly; summarization/memory policy; output validation, one-retry limit, and safe fallback; AI evaluation corpus and model bake-off results.

**Does not own:** Rule math, random numbers, authoritative state mutation, hidden-information policy, session persistence, or adventure canon.

**Handoff contract:** Consumes only A1’s versioned commands/state views and A5’s visibility/safety-tagged content. Emits request/call IDs, typed proposals, a proposed bounded ruling with rationale, and usage metadata; after authority commits a result, it may narrate only the authorized delta. It cannot receive data outside the caller’s visibility scope. Illegal output is never translated into an event. After one retry, control returns a typed fallback/clarification outcome.

## A3 — Backend, platform, security, and privacy engineer

**Mandate:** Own authoritative session execution, persistence, access control, ordering, and technical privacy/security.

**Owned artifacts:** Session lifecycle; event store and snapshots; schema versioning/migrations; idempotency and optimistic-concurrency rules; local Phase 2 coordinator; later host/join/reconnect/transport; identity and authorization; rate/spend limits; data-flow diagram and threat model; backup/recovery; secrets management.

**Does not own:** Game rules, model prompts, adventure semantics, client-side rulings, or legal policy.

**Handoff contract:** Exposes versioned command/query/stream APIs to A2/A4 and test seams to A6. Accepts commands only with actor, session, expected version, idempotency key, and authorization context. Persists authoritative events before exposing resulting narration/state. Publishes retention/deletion behavior and failure semantics to A0/A7/A8.

## A4 — Frontend and accessibility engineer

**Mandate:** Own a legible, trustworthy, mobile-viable client that renders authority but never invents it.

**Owned artifacts:** Phase 2 local UI; later lobby/host/join flow and character creation; narrative transcript; action/clarification UI; lines/veils plus out-of-band pause/stop/report controls; character sheet and party view; turn/spotlight indicators; rules/ruling and dice audit views; reconnect/error states; accessibility acceptance plan.

**Does not own:** State authority, rule decisions, RNG, prompt construction, or event persistence.

**Handoff contract:** Sends only versioned commands defined by A1/A3 and renders versioned projections. Unknown event types fail visibly and safely. Supplies A3 with projection requirements, A6 with stable test selectors/scenarios, and A10 with usable research builds. Client optimistic state is cosmetic and must reconcile to authority.

## A5 — Adventure designer

**Mandate:** Own the original adventure’s semantics, pacing, branches, objectives, NPC motivations/voice, failure/recovery states, and play balance.

**Owned artifacts:** Adventure brief; the authoring format’s semantic model and examples; scene graph; encounter and objective definitions; NPC dossiers; public/private facts; content ratings/boundaries; ending and recovery paths; content test fixtures; asset/source provenance; human playtest revisions.

**Does not own:** Rules identifiers/validators, storage/versioning, model prompt mechanics, legal clearance, or final authoring schema unilaterally.

**Handoff contract:** Co-designs the authoring contract with A1 (rules IDs/validators), A2 (narrative affordances and visibility), A3 (versioning/storage), and A7 (provenance/allowlist). Every content object declares stable ID, version, provenance class, visibility, prerequisites, effects, failure behavior, and localization-safe player text. Unknown provenance blocks release.

## A6 — QA, safety evaluation, and playtest automation

**Mandate:** Independently prove the declared behavior or stop the release.

**Owned artifacts:** Requirements-to-test matrix; golden rules cases; property/state-machine tests; replay/idempotency/concurrency tests; headless simulation harness; fixed prompt-injection, visibility-leak, content-boundary, and stop-bypass corpora; model regression and fallback tests; severity rubric; gate report.

**Does not own:** Product scope, implementation fixes, human fun research, legal acceptance, or lowering a gate to meet a date.

**Handoff contract:** Receives fixtures/contracts from all builders, returns reproducible failures with event/trace IDs, and signs only against the accepted coverage matrix. A rules-bearing release needs zero open critical/high correctness defects and all gate metrics. AI simulation supplements but never replaces human playtests.

## A7 — Licensing, provenance, and content-safety coordinator

**Mandate:** Maintain evidence, content boundaries, attribution, moderation requirements, and release checklists; escalate matters needing counsel.

**Owned artifacts:** Pinned-license/source register; SRD allowlist and conservative denylist; exact attribution/change notices; per-asset provenance ledger; branding/content-generation rules; moderation policy requirements; release audit and counsel-question list.

**Does not own:** Legal advice, acceptance of legal risk, product naming approval, rule implementation, or content authorship.

**Handoff contract:** Gives A1/A2/A5 a machine-consumable licensing allowlist/provenance schema plus human content-boundary and moderation rules. Reviews every shipped content class and export surface. Unknown source, incompatible terms, questionable branding, or undefined safety policy is ship-blocking until qualified counsel supplies any needed guidance/clearance and the human owner records the resulting decision and residual-risk acceptance.

## A8 — Cost and observability engineer

**Mandate:** Make cost, latency, reliability, and model drift measurable per turn and per session.

**Owned artifacts:** Token/session cost model; latency and availability budgets; trace/metric schema; privacy-safe dashboards; cache/model-routing strategy; spend limits and denial-of-wallet alerts; model/version change detector; Phase 2 bake-off economics.

**Does not own:** Prompt quality, provider selection alone, raw player-content logging, business pricing, or production infrastructure broadly.

**Handoff contract:** A2 emits model usage/retry/cache metadata; A3 emits session and infrastructure correlations; A8 returns normalized cost/player-hour, cost/session, p50/p95 latency, fallback, and budget-breach signals. Telemetry identifiers may join traces without copying raw private game text.

## A9 — AI player engineer (dormant until Phase 5)

**Mandate:** Eventually own AI-controlled player characters subject to the same rules and information boundaries as humans.

**Owned artifacts:** Deferred tactical policy, player-personality model, turn behavior, and hidden-information isolation tests.

**Does not own:** Anything through Phase 4; AI-DM behavior; privileged state; rule exceptions.

**Handoff contract:** Not activated unless D5 is reopened at the Phase 5 boundary and A1–A8 contracts are stable. AI players receive exactly the projection a human in that seat could receive.

## A10 — Product research and human playtest lead

**Mandate:** Test whether the experience is understandable, fun, trusted, and worth returning to—not merely technically correct.

**Owned artifacts:** Participant criteria; interview guide; facilitated paper/Wizard-of-Oz prototype; Phase 2 playtest protocol; consent/privacy handling; observation rubric; issue synthesis; completion, trust, fun, and replay-intent results.

**Does not own:** Automated correctness, feature implementation, marketing claims, or changing success thresholds after seeing results.

**Handoff contract:** A0 supplies hypotheses and thresholds; A4/A5 supply prototypes; A6 supplies defect categories. A10 returns coded/pseudonymous evidence, privacy-safe synthesis, and prioritized failure themes; it does not call records anonymous or de-identified without a documented unlinkability review. Findings that invalidate the target user or core loop return the project to discovery rather than being relabeled as polish.

## Cross-workstream interface baseline

Before parallel implementation, the following package must be versioned and approved:

1. **Rules coverage contract:** exact SRD version/checksum, included mechanics/content IDs, source locations, precedence/errata policy, and explicit unsupported list.
2. **Command contract:** actor, authority, visibility, phase, target, resource cost, preconditions, expected state version, and idempotency key.
3. **Event contract:** stable type/version, sequence, causation/correlation, actor, timestamp policy, public/private payload separation, deterministic reducer, migration/upcast policy, and redaction/retention classification.
4. **State-view contract:** public, seat-private, GM-private, and operational projections; no downstream consumer filters secrets after receiving an over-broad object.
5. **AI turn contract:** typed proposals and bounded rulings, pre-roll commitment, authoritative tool round trip, post-result narration, stream timing, content-safety outcome, retry/fallback behavior, and no mutation capability.
6. **Adventure contract:** scene/objective graph, content/rules references, visibility, transitions, effects, failures/recovery, provenance, and schema version.
7. **Observability contract:** metrics and trace correlation that exclude raw narrative by default.
8. **Error and safety contract:** stable rejection reasons, safe user-facing language, retryability, correction/dispute authority, out-of-band stop semantics, and operator escalation.

Draft contracts may be explored with mocks and consumer/producer tests. “Frozen” means a reviewed version is the integration baseline, not that evolution becomes impossible.

## Required independent gates

- A6 signs rules, replay, security-evaluation, and regression evidence.
- A7 signs the provenance/attribution checklist; qualified counsel advises or clears where appropriate, and the human owner accepts residual business/legal risk.
- A8 signs cost/latency instrumentation completeness.
- A10 signs human-playtest evidence completeness, not whether the owner must like the result.
- A0 confirms contract conformance and dependencies.
- The human owner alone advances the phase boundary.
