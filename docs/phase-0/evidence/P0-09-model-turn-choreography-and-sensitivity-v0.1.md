# P0-09 — Model-turn choreography and full-trace sensitivity v0.1

> **STATUS: DESK-AUTHORED REVIEW DRAFT — PROVISIONAL / DEPENDENCY OPEN / NOT ACCEPTED / NOT IMPLEMENTED.** P0-01 is complete and amended P0-03 is accepted. [P0-07 v0.1](P0-07-resolution-lanes-v0.1.md) is a provisional, unaccepted design input; this draft does not satisfy that dependency or complete P0-09. It selects no provider, validates no model, finalizes no cost/latency gate, accepts no ADR, authorizes no production work, and authorizes no participant work. Recruitment and fieldwork remain NO-GO and G0 remains closed.

- Document ID: `P0-09-MODEL-TURN-SENSITIVITY`
- Version: `0.1`
- Prepared: `2026-09-25`
- Accountable roles: `A8 + A2`
- Evidence boundary: `DESK MODEL / NO EXECUTED MODEL TRACES / NO PROVIDER COMMITMENT`
- Controlling inputs: [project charter](../00-project-charter.md), [decision brief D4/D15](../01-decision-brief.md), [agent contracts](../02-agent-roster-and-contracts.md), [amended P0-03](P0-03-vertical-slice-spec.md), and provisional [P0-07](P0-07-resolution-lanes-v0.1.md)
- Related controls: [milestones and gates](../04-milestones-and-gates.md), [risk register](../05-risk-register.md), [research and evidence notes](../07-research-and-evidence.md), and [ADR register](../../adr/README.md)

## 1. Purpose, dependency, and recommendation

This document specifies one provider-neutral candidate for the complete logical model turn and makes its cost, latency, cache, retry, fallback, streaming, data, and telemetry assumptions inspectable. It covers all model calls, engine/tool/random child stages, failed attempts, maintenance calls, and post-result rendering that a one-call estimate would hide.

The recommended **bake-off hypothesis**, not a vendor choice, is:

1. use a certified deterministic parser for exact structured choices where possible;
2. otherwise use an efficient structured-output model class for the pre-roll proposal;
3. use a balanced narrative model class once, after the final authoritative public result;
4. render intermediate checkpoints with deterministic public templates; and
5. fall back to deterministic proposal/result templates whenever authority, privacy, time, or spend cannot support another model call.

The same-model two-pass and all-efficient profiles remain controls. A frontier-priced model is a diagnostic comparison, not the default candidate. Quality, reliability, visibility isolation, and measured full-turn latency can overturn the economic hypothesis.

### 1.1 Dependency state

| Dependency | State used here | Consequence |
|---|---|---|
| P0-01 | Complete | D4 and D15 may shape this draft. |
| Amended P0-03 | Accepted research contract | The slice, authority, safety, and provisional targets are binding inputs. |
| P0-07 | **Provisional / not accepted / incomplete** | Its three-lane and child-stage design is used only as a candidate. This P0-09 version cannot be accepted or treated as satisfying the dependency. |
| P0-06/P0-05 evidence chain | Incomplete; no observed P0-05 evidence | Token shapes, stage mix, and fallback frequency are planning assumptions, not observations. |

Any later P0-07 change to visibility, commitment, child stages, correction, or fallback requires a versioned P0-09 reconciliation before this choreography may be reviewed for acceptance.

## 2. Non-negotiable authority and safety invariants

| ID | Invariant |
|---|---|
| `MT-INV-01` | A model proposes or narrates; it never selects rules authority, commits randomness, writes state, corrects state, or creates an event. |
| `MT-INV-02` | The only bounded ruling the current candidate may reference is `AM01-R1`, exactly as defined by P0-07; routing or model output cannot generalize it. |
| `MT-INV-03` | Pause, Stop, and Report are local/out-of-band controls that preempt prompts, retries, tools, randomness, apply, and narration. They never depend on a model response. |
| `MT-INV-04` | Every model receives a least-privilege, visibility-scoped projection. Private fields are removed before retrieval/request construction, not filtered after the model sees them. |
| `MT-INV-05` | The complete commitment and player-authorized projection exist before related randomness. Every authoritative checkpoint is appended/applied before outcome narration about it. |
| `MT-INV-06` | One logical player resolution retains one correlation identity. Attack, damage, rule-authorized rerolls, child choices, tool calls, and random stages are children, not extra player turns. |
| `MT-INV-07` | At most one semantic proposal repair is allowed against the identical authoritative state version and visibility scope. Provider switching, SDK retries, or rephrasing cannot reset the cap. |
| `MT-INV-08` | A valid unfavorable result is never retried, rerouted, corrected, or renarrated into a different result. |
| `MT-INV-09` | No generated outcome text reaches the player before the corresponding public authoritative result exists. |
| `MT-INV-10` | Every provider attempt, cache transfer, model/tool fee, random/tool stage, fallback, and synchronous or asynchronous maintenance call is attributed to one turn/session ledger. |
| `MT-INV-11` | Operational telemetry contains no raw prompt, player text, backstory, narration, hidden fact, tool argument/result, free-form provider error, or hash of private text. |
| `MT-INV-12` | Quarantined `P0-08-pre` content is excluded from prompts, caches, examples, fixtures, and evaluations until its separate provenance gate closes. |
| `MT-INV-13` | Every submission is authenticated and authorized for the target session, carries a client submission/idempotency key, and is admitted at most once for the same session and state version. Replay returns the existing status/result; bounded per-session concurrency, queue, and rate controls prevent duplicate or parallel spend. |
| `MT-INV-14` | Before any provider call, one atomic admission transaction reserves the configured worst-case token and spend envelope for every possible provider/model/tool leg in that logical resolution. Insufficient or unconfigured capacity fails closed to a local typed fallback; unused capacity is released only through reconciliation. |
| `MT-INV-15` | Autonomous provider-tool loops are disabled for proposal and narration. Any later enabled provider tool is a named, predeclared stage with an accepted call, attempt, token, time, and spend cap; it cannot recurse or reset another cap. |
| `MT-INV-16` | Delete session is a preemptive data-control path: it first advances a deletion epoch/tombstone, cancels queued/in-flight work, rejects late completions, and prevents summaries, caches, telemetry, or gameplay records from rehydrating deleted content. Provider-side retention remains separately disclosed and governed. |

## 3. Correlation and accounting envelope

The correlation tree is:

`session → interaction → logical_resolution → stage → provider_attempt or engine/tool/random operation`

Minimum identities and relationships:

| Field | Purpose | Central form |
|---|---|---|
| `session_ref` | Session grouping | Rotating keyed pseudonym; no raw user/session ID |
| `interaction_id` | One submitted player input | Random opaque ID |
| `logical_resolution_id` | Parent resolution across proposal, children, apply, and narration | Random opaque ID |
| `parent_stage_id` / `stage_id` | Ordered stage graph | Opaque IDs plus enumerated stage type |
| `model_call_id` / `provider_attempt_id` | Logical call versus transport/provider attempts | Opaque IDs |
| `provider_request_id` | Invoice/incident reconciliation | Access-controlled metadata |
| `engine_command_id` / `result_identity` | Idempotency and bound-result lookup | Central status only; canonical values stay local |
| `causation_id` / `correlation_id` | Append-only relationship | Opaque IDs |
| `state_version_in` / `state_version_out` | Detect stale or reordered work | Version numbers/hashes that reveal no content |
| `submission_key_ref` / `admission_id` | Deduplicate a client submission and bind its one admission decision | Rotating keyed reference plus opaque ID; never the raw client key |
| `deletion_epoch` | Reject work created before a delete/tombstone transition | Monotonic non-content version; retained only as required to suppress stragglers |

A new answer to the one permitted player clarification creates a new causally linked interaction against current state. It does not overwrite the first interaction or grant a second clarification. Post-turn maintenance stays charged to the turn that triggered it even when it runs off the critical path.

Admission is a local atomic operation scoped to the authenticated principal, session, authoritative state version, and submission key. Before `M04`, `M05`, `M10`, or any other provider call, it checks the deletion epoch, deduplicates the submission, enforces the configured queue/rate and one-in-flight-or-bounded-concurrency policy, and reserves:

`B_reserve = worst_case(M04 + M05 + M10 + one_mutually_exclusive_successor + N40_count_cap + enabled_provider_tools + B50 + tier/region/long_context uplifts) + safety_margin`

Terms disabled in the certified configuration are zero; an enabled term must have a finite accepted cap. Reservation is against the applicable turn, session, and account/month budgets in the same transaction so parallel requests cannot oversubscribe them. The system records provider-reported actual usage, reconciles the reservation at `S60`, and releases only the unused balance. A missing numeric cap, stale price catalog, unknown fee, failed reservation, duplicate, or concurrency/rate rejection causes no provider call and cannot consume gameplay state.

## 4. Provider-neutral call and stage inventory

| ID | Stage | Model/provider call? | Critical-path rule |
|---|---|---:|---|
| `D00` | Continuous Delete-session intercept and tombstone | No | Preempts new work, advances the deletion epoch before erasure, cancels queued/in-flight work, and blocks every late write or rehydration. |
| `S00` | Continuous out-of-band Pause/Stop/Report intercept | No | Preempts and cancels all cancellable downstream work. |
| `S01` | Authenticate/authorize, deduplicate, rate/queue/concurrency admit, size/type check, and open trace | No | Same-key replay returns the existing status/result. Rejected, malformed, oversized, unauthorized, deleted, or excess-concurrency input causes no provider spend or gameplay mutation. |
| `S01A` | Atomically reserve worst-case token/spend envelope | No | Must cover every permitted provider/model/tool/maintenance leg before the first call; missing/insufficient capacity fails locally without a provider call. |
| `M04` | Optional content classifier/moderation | Optional | Never gates the immediate stop control; if used, its data, tokens, time, and fee are fully counted. |
| `M05` | Optional context compaction/summary needed before proposal | Optional | Certified output only; synchronous use counts in turn latency. Prefer prior-turn asynchronous maintenance. |
| `S02` | Read one authoritative state version and build least-privilege projection | No | No quarantined content and no fields outside the call purpose. |
| `S03` | Assemble stable prefix, schema, dynamic projection, cache controls, and tool allowlist | No | Record every prompt/schema/content version and requested cache policy. Provider tools are disabled by default; every enabled tool maps to a predeclared bounded stage. |
| `M10` | Initial typed pre-roll proposal | Yes, unless certified deterministic parser succeeds | Buffer output; it has no authority and is not shown directly. |
| `V11` | Schema, catalog, authority, state, provenance, and visibility validation | No | A model cannot self-validate. |
| `M12` | One semantic proposal repair | Conditional; may be the sole successor attempt after `M10` | Same state/version/scope; only for a repairable non-authoritative output defect. No third generative attempt follows a failed repair. |
| `F13` | Typed proposal/clarification/unsupported fallback | No | Zero randomness, resource consumption, or state mutation. |
| `E20` | Engine validates, builds commitment/public stakes, and requests confirmation | No | Player may withdraw cost-free before parent freeze/first-roll authorization. |
| `E30` | Bind next preauthored stage/child commitment | No | Bind only an operation or branch already admitted by the parent graph. |
| `R31` | Obtain tool/random result under stable identity | Engine or external tool | Query/redeliver uncertain delivery; never speculative reroll. |
| `E32` | Validate, retain, and project the bound raw result | No | A `PUBLIC_AT_RANDOMNESS` value may be shown as provisional; it cannot authorize mutation or narration. |
| `W33` | Open/close applicable precommitted intervention window | No | Record selection/decline; bind any authorized child before its random operation. No unlisted post-result choice. |
| `E34` | Close applicable windows and append/apply the ordered event group | No | Only the final checkpoint result mutates state; apply is atomic and precedes outcome narration. |
| `E35` | Expose the public applied result and bind any continuing stage | No | Continue the graph from the new authoritative state/version; terminal apply cancels forbidden later stages. |
| `N40.i` | Post-result narration call | Normally one final call; additional calls conditional | Only after its authoritative public checkpoint; receives authorized projection/delta only. |
| `V41` | Narration visibility/content/state-consistency check | No | Invalid prose never changes state. |
| `F42` | Deterministic public result template | No | Mandatory timeout, validation, privacy, and budget fallback. |
| `B50` | Optional post-turn summary/memory/cache maintenance | Optional | Count cost on triggering turn/session; record readiness impact separately. |
| `S60` | Reconcile reservation and close correlated ledger | No | Record complete/fallback/stop/delete status, all missing-usage flags, provider actuals, and released/held reservation without delaying a canonical public result. |

The base economic case includes `M10`, conditional `M12`, one final `N40`, and scheduled `B50`. It assumes local engine/random stages have no per-call vendor fee. Provider-hosted or model-invoked search, file, code, computer, random, or other tools are disabled in this baseline. Any later enabled provider tool must be a named stage with fixed call/attempt/token/time/spend limits and measured fixed and usage charges; it may not be autonomous, recursive, or hidden in “model overhead.”

## 5. End-to-end choreography

### 5.1 Input through valid proposal

1. `D00` checks the session's deletion epoch/tombstone before admission and remains able to preempt the turn. `S00` independently checks Pause/Stop/Report before any model work and throughout the turn.
2. `S01` authenticates the caller, authorizes the target session, binds the client submission key to the authoritative state version, and opens the parent trace only after size/type, queue/rate, and one-in-flight-or-bounded-concurrency checks. A duplicate returns the already-bound status/result; it does not open another logical resolution or call a provider.
3. `S01A` atomically reserves the configured worst-case token/spend envelope across turn, session, and account/month scopes before any optional or required provider call. Missing caps, stale/unknown pricing, or insufficient capacity produces a local typed fallback without consuming gameplay state.
4. Optional `M04` or synchronous `M05` runs only if an accepted later contract requires it and its maximum is included in the reservation. A Stop or Delete never waits for either.
5. `S02` reads one authoritative version and produces the minimum public/player-authorized projection.
6. `S03` places stable, versioned instructions/schema before the dynamic suffix and records the requested cache mode and empty provider-tool allowlist. Security does not depend on a cache boundary. If a later certified configuration enables a provider tool, `S03` can expose only its named schema and predeclared finite call/attempt/token/time/spend cap; autonomous or recursive tool choice remains forbidden.
7. A certified deterministic parser may produce the typed proposal for exact structured input. Otherwise `M10` produces one non-authoritative proposal.
8. `V11` validates shape, lane, rule/catalog locator, actor/target, state version, cost, visibility, consequences, and absence of unauthorized fields.
9. If and only if the defect is repairable model output, state/scope are unchanged, and the one global successor slot has not been spent on transport replacement/failover, `M12` receives structured validation errors and gets one repair. Missing authority, provenance, state, or a visibility risk stops rather than prompting the model to invent a fix.
10. A second invalid proposal, timeout, spend breach, or exhausted attempt cap ends at `F13`. Known unsupported intent follows P0-07; unresolved ambiguity gets the one neutral player clarification; a system defect is not mislabeled as unsupported.

### 5.2 Commitment, tools, randomness, and child stages

1. `E20` independently selects the admitted catalog/ruling entry, revalidates current state, constructs the full visibility-scoped commitment, and shows the public actionable stakes.
2. For a voluntary roll-producing choice, the player confirms or withdraws before parent freeze/first-roll authorization. On confirmation, freeze the parent. User think time is measured separately from system-active latency.
3. For each preauthored stage or child, `E30` binds the next commitment to the current applied checkpoint.
4. `R31` requests a tool/random result under one stable identity. Delivery uncertainty triggers a status lookup/redelivery, not a new result.
5. `E32` validates and retains the bound raw result. A stale version after a bound result preserves it under its original stage, applies nothing, and stops; it never rebinds or rerolls. A value classified `PUBLIC_AT_RANDOMNESS` may be shown, but the display must mark it as a bound provisional result that cannot yet authorize state or outcome narration.
6. `W33` opens every applicable cataloged intervention window, exposes only its precommitted options, and records selection or decline. A selected reroll, candidate pool, conditional die, movement option, or nonlethal branch binds its exact child at `E30` before any next random operation. Return to `R31/E32/W33` as required; retain every raw result and choice.
7. Only when all intervention windows for the checkpoint are closed does `E34` validate the final checkpoint result and atomically append/apply its event group.
8. `E35` exposes the public applied result. If the parent graph continues, bind the next stage to the new authoritative state/version and resume at `E30`; a terminal checkpoint cancels forbidden later stages.
9. The loop ends on the parent graph's authored terminal point. No proposal-model recall is needed for deterministic attack→damage, Heroic Inspiration, Tactical Mind, Savage Attacker, Remarkable Athlete, Multiattack, knockout, or `AM01-R1` child mechanics.

### 5.3 Post-result narration

The recommended base topology renders intermediate public checkpoints through deterministic templates and makes one `N40` call after the logical resolution reaches its final applied public state. This keeps dice/results visible, preserves intervention timing, and avoids a model call per child stage.

If later usability evidence requires model prose at an intermediate checkpoint, that call becomes `N40.1`, `N40.2`, and so on. Each call must independently satisfy apply-before-narrate, least privilege, stream validation, cost, and latency rules. The sensitivity table includes 1.25 and 2.0 average narration legs; they are not free.

`V41` validates narration before each player-visible release unit. The fail-closed baseline buffers the complete narration; a later candidate may release sentence/chunk units only after that complete unit passes visibility, content, and state-consistency checks. A validator that cannot prove the next prefix/unit safe forces full-response buffering or `F42`; it never “streams and corrects later.” Raw provider token deltas never go directly to the player and cannot be recalled after a leak. On timeout, provider error, unsafe content, hidden-data risk, or contradiction, discard the unreleased unit and render `F42` from canonical public fields. Do not automatically retry narration in the hot path. The authoritative state/result remains unchanged.

### 5.4 Maintenance and close

`B50` may compact public/session-authorized context after the player-visible result. It is asynchronous only when the next turn does not depend on it. Failure leaves canonical local events authoritative and activates the deterministic/minimal-context path; it cannot block Stop, Delete, or export. `S60` closes the ledger only after every attempt is terminal or explicitly marked orphaned/unknown for reconciliation; it posts provider actuals against the atomic reservation and releases only the unused balance. Unknown charges remain held or fail closed under the accepted budget policy rather than becoming free capacity.

### 5.5 Delete-session race and provider boundary

Delete is a `D00`-class control, not an ordinary queued gameplay command:

1. atomically advance a monotonic deletion epoch/write a non-content tombstone before erasing product-controlled session data;
2. reject new admissions and cancel queued or cancellable in-flight `M04`, `M05`, `M10`, `M12`, `N40`, provider-tool, and `B50` work;
3. require every worker and completion callback to recheck both active-session status and the captured epoch before it can persist, cache, summarize, emit gameplay-derived telemetry, or render;
4. discard late provider content and prevent any cache, summary, retry, status redelivery, or maintenance job from recreating the deleted session; and
5. retain only the minimum non-content tombstone and billing/security evidence required by the accepted deletion, legal, and reconciliation policy, for its separately approved duration.

Best-effort cancellation does not imply that a request already transmitted to a provider was never processed or immediately erased. Product deletion must disclose and enforce the exact endpoint, per-request storage flag, cache mode, abuse-monitoring, retention, region, and deletion behavior accepted for that provider. A local tombstone prevents product-side resurrection; it does not make a false provider-side deletion guarantee.

## 6. Worked stage ledgers

These are accounting fixtures, not executed traces or implementation proof.

| Case | Required stages | Calls billed | Required disposition |
|---|---|---:|---|
| Normal check | `D00/S00→S01→S01A→S03→M10→V11→E20→E30→R31→E32→W33→E34/E35→N40→V41→S60` | Proposal + one narration | Admission/reservation precedes spend; raw result retained; applicable windows closed; state/result applied before prose; one logical resolution. |
| Authored no-roll action | `D00/S00→S01→S01A→M10/V11 or parser→E20→W33 if applicable→E34/E35→N40` | Zero/one proposal + one narration | Predicate/delta committed before mutation; no random call. |
| Attack→damage or multi-child feature | One parent plus repeated `E30→R31→E32→W33`, then `E34/E35` at each cataloged apply checkpoint and final `N40` | Proposal + one final narration | Every raw result/window/child is retained and timed; deterministic checkpoint templates; no provisional narration. |
| `AM01-R1` Opportunity Attack | Parent movement commitment triggers exact `AM01-R1` child before movement | Proposal if intent needed + one final narration | One Slam only; first legal automatic OA; no authority expansion. |
| Material ambiguity | `M10→V11→F13` then one player clarification as new linked interaction | One proposal, then new attempt if player answers | No roll/cost/state; no second clarification. |
| Invalid proposal then repair | `M10→V11→M12→V11` | Two proposal calls | Same state/version/scope; repair cap exhausted. |
| Invalid proposal after repair | Previous row then `F13` | Two proposal calls, no narration | Typed zero-mutation fallback. |
| Narration failure after apply | Valid authoritative path, `N40→V41 fail→F42` | Proposal + failed narration | Canonical result template; no state rollback and no narration retry. |
| Safety control at any stage | `S00` cancels/halts downstream work | Attempts already sent remain counted | No further random/apply/narration/retry until explicit player action under the accepted safety contract. |
| Same-key replay | `S01` returns the bound admission/status/result | No new calls | Same logical resolution; no duplicated proposal, randomness, mutation, or spend. |
| Concurrent/rate/queue rejection | `S01` rejects before `S01A` | No calls | Local busy/rate response; no gameplay consumption or mutation. |
| Reservation failure or missing cap | `S01A→F13` before any provider leg | No calls | Typed local fallback; no unbudgeted provider operation. |
| Delete during queued/in-flight work | `D00` advances epoch, cancels, erases, and rejects late completion | Already-sent attempts remain reconcilable; no new calls | No late render/write/cache/summary rehydration; external retention follows disclosed provider controls. |

## 7. Attempt, retry, and fallback policy

| Condition | Maximum recovery | Cost/latency treatment | Final behavior |
|---|---|---|---|
| Repairable invalid proposal | Use `M12` only when no successor attempt has already been spent | Separate billed/timed call; maximum two proposal generations total | Validated proposal or `FALLBACK_PROPOSAL_INVALID`; a failed/invalid `M12` is terminal. |
| Provider transport failure before known completion | First query idempotent status/redelivery under the same identity; one new generative successor only when provider semantics prove no completed usable response and the successor has not been spent | Count every attempt, query, partial output, and unknown charge | The successor consumes the same global slot otherwise available to `M12`; failure/invalidity then falls back. |
| Provider failover | May be the one generative successor after `M10`; never an additional attempt; only to a pre-certified model/configuration with equivalent-or-stricter visibility, schema, training-use, retention, region, and cache controls | Count both providers and transfer latency | Otherwise use local fallback; no parallel racing and no later semantic repair. |
| Ambiguous player intent | One neutral clarification | Player wait separate; answer starts linked interaction | Admitted lane, known unsupported, or unresolved fallback. |
| Uncertain engine/random delivery | Lookup/redeliver same identity | Tool time counted once per actual operation plus queries | At most one bound result; never reroll. |
| Rule-authorized reroll/second pool | Exact preauthored child stages only | Every random stage timed, not a retry | Preserve all required raw results locally. |
| Missing/conflicting authority or provenance | None | Close trace with stop reason | `STOP_CONTRACT_DEFECT`. |
| Visibility risk | None | Close trace with stop reason | `STOP_VISIBILITY_RISK`. |
| Stale state before a result | One authoritative reread | Count time; no model cap reset | Redisclose changed stakes and require fresh confirmation. |
| State mismatch after a bound result | None | Preserve result identity/time | Apply nothing; stop/correct; never reuse or reroll. |
| Randomness unavailable | Same-identity status query only | Count wait/query | Preserve pending commitment and pause. |
| Narration timeout/error/invalidity | No automatic model retry | Failed call remains billed/timed | Deterministic public result template. |
| Cache miss | No retry | Charge normal fresh/write category | Continue within remaining budget. |
| Spend/latency breaker | No new model work | Close all incurred usage | Pre-apply: zero-mutation typed fallback; post-apply: result template. |
| Duplicate submission/key replay | Return the status/result already bound at `S01`; never readmission | No new reservation, provider call, tool/random operation, or state mutation | Same correlation identity and terminal/pending status. |
| Session concurrency, queue, or rate limit reached | No provider recovery | Reject before reservation/call | Local typed busy/rate response; the player may submit later against current state. |
| Missing or insufficient atomic reservation | No provider recovery | Zero provider spend | `F13`/local deterministic path; absent numeric caps are fail-closed, not unlimited. |
| Provider-tool request | None in the baseline; a certified named tool may run only within its predeclared finite stage cap | Charge every call/fee against the original reservation and trace | Reject undeclared, recursive, or cap-exceeding calls; provider/tool output cannot add authority. |
| Delete observed before or during work | `D00` cancellation plus epoch/tombstone check | Reconcile already-sent calls without retaining response content | Reject all late writes/renders/rehydration; no retry or successor. |

### 7.1 Global proposal-attempt state machine

The maximum is **two billed generative proposal attempts per logical proposal**:

1. `ATTEMPT_1 = M10`.
2. If `M10` returns a complete but repairably invalid proposal, `ATTEMPT_2` may be the one semantic `M12` repair.
3. If `M10` definitively produces no usable completed response because of transport/provider failure, `ATTEMPT_2` may instead be one replacement or failover to a pre-certified equivalent-or-stricter data/schema configuration.
4. Any timeout, delivery uncertainty, invalid output, or transport failure on `ATTEMPT_2` ends in `F13`. There is no repair or delivery retry after it.

An idempotent status lookup or redelivery of the same already-bound response identity is non-generative and does not consume `ATTEMPT_2`, but its latency, fee, and status are recorded. Any operation that can generate a new output consumes the successor slot even if the provider labels it a retry. No blind resend is considered “free.” If a provider cannot distinguish an unprocessed request from an uncertain completed request, the conservative result is fallback, not a duplicate generation.

This proposal-attempt cap sits inside the stricter `S01/S01A` admission and reservation. A client submission replay never reaches this state machine, and a concurrent request cannot open another proposal against the same admitted session/state slot. `M10` and `N40` expose no provider tools in the baseline; a later certified named tool is accounted as its own bounded stage and cannot cause a recursive call loop or reset `ATTEMPT_2`.

## 8. Streaming contract

Safe player-visible stream points are:

1. deterministic progress text that claims no acceptance, rule, result, or hidden fact;
2. the engine-authored public commitment/stakes after `V11/E20`;
3. bound `PUBLIC_AT_RANDOMNESS` dice/tool values after `E32`, clearly marked provisional and never narrated as an outcome;
4. public applied state only after all applicable `W33` windows close and `E34/E35` succeeds; and
5. validated `N40` narration release units after the corresponding authoritative result exists.

The `M10/M12` token stream is buffered internally until the whole typed proposal passes `V11`. A spinner or “working” message does **not** count as first meaningful content. Direct unvalidated provider-to-player output is not this baseline.

For narration, private fields are excluded before request construction. Provider deltas are buffered into the complete response or a separately validated sentence/chunk release unit; an incremental token check is not sufficient and is not a substitute for least-privilege input. If the validator cannot prove a candidate prefix/unit safe, buffer the full response and validate it or use `F42`. Record transport first byte, first valid semantic event, first validated release unit, first player-rendered meaningful content, first player-rendered outcome narration, and completion separately. Current OpenAI documentation confirms that streaming uses typed semantic events, but this design requirement remains provider-neutral and must be verified for each candidate.

## 9. Cache and context contract

| Rule | Requirement |
|---|---|
| Stable prefix | Put approved system/persona policy, public rules subset, and tool/output schema before changing turn data; version every element. |
| Scope | Partition cache accounting by organization/tenant, session where needed, visibility class, region, model/snapshot, persona, adventure, rules catalog, and schema version. |
| Privacy | A cache hit is an optimization, not authorization. Never reuse a player-private or GM-private prefix for a public call or another tenant/session. |
| Dynamic content | Put only player text, current state, payloads already authorized/revealed for that call, and changing event deltas after the stable boundary. Unrevealed/unauthorized private payloads are excluded before request construction. Do not deliberately prewarm private gameplay content; authorized dynamic content may still enter provider-managed cache behavior and therefore requires scoped retention review. |
| Provider behavior | Record requested versus resolved cache mode, fresh/read/write tokens, TTL/retention, and hit/miss. Do not assume a hit or a discount. |
| Application cache | Keep gameplay-derived caches local for the Phase 2 direction; Delete session must remove product-controlled summaries, indexes, caches, and queued diagnostics as well as events/narration. |
| Compaction | Treat prefix changes and compaction as possible cache invalidation. Compare total tokens/cost, not hit rate alone. |

For the current OpenAI example, official documentation says cache reuse depends on matching a rendered prefix; cache writes, reads, and uncached input are mutually exclusive billing categories; cache entries can contain processed context state; and retention/eligibility vary by model and organization. Those are vendor facts, not portable guarantees. The provider-neutral adapter must normalize actual usage fields without pretending different cache semantics are equivalent.

## 10. Provider-neutral model, data, and vendor review contract

No candidate advances when a required fact is unknown. `UNKNOWN` is a blocker or explicitly priced risk, not an optimistic assumption.

| Dimension | Required review evidence |
|---|---|
| Model identity | Requested and resolved model, immutable snapshot/version support, alias drift behavior, deprecation notice, rollback path. |
| Proposal capability | Structured output/function-call conformance on the fixed corpus; first-pass and after-repair validity; hidden-field and authority violations. |
| Narration capability | Continuity, voice, state fidelity, safety, visibility isolation, output length, and deterministic-template comparison. |
| Transport | Streaming event semantics, idempotency/status lookup, timeout/cancel behavior, rate limits, availability/SLA, error taxonomy. |
| Usage and price | Fresh/read/write input, visible and reasoning/thinking output, cache storage/TTL, fixed tool fees, service tier, region uplift, long-context threshold, taxes/credits. |
| Data use | Training default/opt-in/out, abuse-monitoring content and duration, application-state storage, human access, deletion, legal exceptions. |
| Strong controls | ZDR/modified monitoring eligibility, endpoint/model exclusions, data residency/processing region, cache implications, organization/project configuration. |
| Commercial/legal | DPA/terms, subprocessors, incident notification, export/deletion commitments, California-facing qualified review. |
| Operations | Capacity limits, spend limits, invoices/usage export, provider request IDs, support/escalation, status history. |
| Exit | Portable prompts/schemas/evals, provider-independent canonical state, alternate certified candidate, deterministic fallback. |

The bake-off must run the same versioned evaluation set against at least an efficient proposer class and a balanced class. The recommended tiered route must also be compared with one balanced model for both passes, an all-efficient control, and deterministic templates. Provider/model selection remains deferred to measured P1B evidence and later owner review.

## 11. Full-trace cost model

For model call or provider attempt `c`, with disjoint token categories in millions:

`C_c = K_tier,region × (I_fresh × R_fresh + I_read × R_read + I_write × R_write + O_billable × R_output) + C_tools + C_cache_storage + C_other`

`O_billable` includes reasoning/thinking tokens when the provider bills them as output, whether or not they are visible. If the provider reports different categories, retain its raw usage fields and map them explicitly; do not infer zero. A cache-write rate is not added on top of the same uncached input unless the provider's official billing contract says so.

For logical resolution `r`:

`C_r = Σ all initial, failed, transport, repair, narration, moderation, summary, and maintenance attempts + Σ tool/random vendor fees`

For inference and inference-adjacent provider charges in session `s`:

`C_inference,s = Σ C_r + unattributed session model/auxiliary calls + session-level provider cache charges not already attributed in C_c`

For product data-plane operations where applicable:

`C_product-data,s = GB-hours × storage rate + reads × read rate + writes × write rate + GB egress × egress rate + fixed data-vendor operations`

The buckets must be disjoint: a cache-storage, network, or vendor-operation charge attributed in `C_c`/`C_inference,s` cannot appear again in `C_product-data,s`. Report inference-only and total application cost (`C_inference,s + C_product-data,s + other disjoint hosting/support`) separately. Also report cost per successful resolution, fallback, player-hour, 60–90-minute slice, and normalized three-hour session. A simple time normalization may be shown only alongside the assumed turn density.

### 11.1 Current official rate-card example

Verified on `2026-09-25`; USD per one million text tokens, Standard tier, short-context requests. These rates are a reproducible worked example, not a recommendation or vendor commitment.

| Candidate-class proxy | Fresh input | Cache read | Cache write | Output | Current official source |
|---|---:|---:|---:|---:|---|
| Efficient — OpenAI GPT-6 Luna | $0.10 | $0.01 | $0.125 | $0.50 | [Official model page](https://developers.openai.com/api/docs/models/gpt-6-luna) |
| Balanced — OpenAI GPT-6 Sol | $2.00 | $0.20 | $2.50 | $10.00 | [Official model page](https://developers.openai.com/api/docs/models/gpt-6-sol) |
| Frontier sensitivity — OpenAI GPT-6 Astra | $10.00 | $1.00 | $12.50 | $50.00 | [Official model page](https://developers.openai.com/api/docs/models/gpt-6-astra) |

The same official pages state that Luna/Sol short-context rates change above 272K input tokens, regional processing adds 10% where available, Batch/Flex are 50% of Standard, and Fast mode is 2× applicable rates. This draft assumes Standard, no region uplift, and every individual request below 272K. It does not assume Batch/Flex can serve an interactive turn.

### 11.2 Explicit planning assumptions

No row below is observed behavior or a percentile claim. Input totals include proposal, conditional semantic repair, one final narration per turn, and listed maintenance calls; there is no opaque “15% overhead” multiplier. Each successor/repair uses the same proposal input/output shape as `M10`; the session cache read/write/fresh mix applies uniformly to all modeled input; and each 1.25/2.0 narration-leg sensitivity duplicates the scenario's base narration input/output shape and cache mix.

This table does not silently revise the earlier 2026-09-17 research snapshot. It is a new decomposed two-pass sensitivity whose narration/repair/maintenance legs are explicit. The earlier 15% allowance expressly excluded a systematic second pass, so it must not be added to or substituted for these totals without rebuilding the call ledger.

| Scenario | Turns / 3h | Proposal per turn input/output | Narration per turn input/output | Repair rate | Maintenance calls input/output | Session input/output | Cache read/write/fresh |
|---|---:|---:|---:|---:|---:|---:|---:|
| Lean | 30 | 3.5k / 160 | 2.5k / 220 | 2% | 3 × 4k / 200 | 0.1941M / 0.012096M | 50% / 10% / 40% |
| Base | 45 | 7k / 250 | 5k / 350 | 5% | 5 × 6k / 300 | 0.58575M / 0.0290625M | 60% / 10% / 30% |
| Stress | 60 | 12k / 350 | 8k / 500 | 10% | 10 × 10k / 500 | 1.372M / 0.0581M | 70% / 10% / 20% |

Assumptions exclude taxes, application hosting, support, voice/images/search, paid external random/tool calls, and cache-storage fees. Reasoning tokens are included only if present in reported billable output; the bake-off must expose them separately. All maintenance uses the efficient class in the tiered row.

### 11.3 Calculated three-hour inference sensitivity

| Model topology | Lean | Base | Stress | Interpretation |
|---|---:|---:|---:|---|
| Efficient class for proposal, narration, maintenance | $0.02 | $0.04 | $0.08 | Cheapest control; quality/reliability unknown. |
| **Tiered hypothesis: efficient proposal/maintenance + balanced narration** | **$0.16** | **$0.40** | **$0.73** | Recommended evaluation hypothesis; not selected. |
| Balanced class for all calls | $0.34 | $0.86 | $1.66 | Continuity/control comparison. |
| Frontier-price sensitivity for all calls | $1.72 | $4.29 | $8.32 | Exceeds provisional session targets in these assumptions. |

These are scenario points, not p50/p95. Under the same assumptions, a fully cold/fresh tiered session is about `$0.23 / $0.65 / $1.36` for Lean/Base/Stress. A 10% regional uplift would multiply applicable totals by `1.10`.

Narration frequency matters because the balanced narration leg dominates the tiered example:

| Average model narration legs per turn | Lean | Base | Stress |
|---:|---:|---:|---:|
| 1.00 — recommended final-only baseline | $0.16 | $0.40 | $0.73 |
| 1.25 | $0.20 | $0.49 | $0.90 |
| 2.00 | $0.31 | $0.78 | $1.41 |

### 11.4 Conditional-branch sensitivity and zero baselines

The numeric tables set optional synchronous `M04/M05`, external paid tools, cache-storage fees, and product data-plane cost to zero. They still belong in every real trace. The one modeled `N40` leg is charged even when it fails; `F42` adds no inference call. The proposal successor rate is the semantic-repair baseline, but a transport replacement or certified failover consumes the same mutually exclusive slot and call shape.

| Conditional branch | Base-tiered worked increment | Latency increment |
|---|---:|---|
| One additional allowed proposal successor on an affected turn | `$0.0004645` for the Base 7k/250 efficient-class shape; session delta is `turns × (q_successor − 5%) × $0.0004645`, bounded to one successor per turn | Actual successor critical-path duration; represented by the repair add-on in §12.2 |
| Optional `M04`, illustrative 1k fresh input / 20 output on efficient class | `$0.00011` per call (`$0.00495` if used on all 45 Base turns) | `+T_M04` when synchronous |
| One extra synchronous `M05`, illustrative 6k fresh input / 300 output on efficient class | `$0.00075` per call | `+T_M05`; asynchronous work still affects next-turn readiness |
| External paid tool/random operation | `+ quantity × official per-operation/usage rate` | Add only operations on the actual critical path; retain every child span |
| Provider cache storage | `+ cached million-token-hours × storage rate` | Usually off-path; record cache preparation/lookup time when on-path |
| Narration fails after the already-counted `N40` | Actual billed partial/full `N40` usage replaces, not supplements, its assumed usage; `F42 = $0` inference | `T_N40-to-failure + T_F42`; use `0.1s` as the local template what-if |

If a future configuration makes one of these nonzero by default, move it into §11.2 rather than leaving it as an add-on. Actual partial attempts use provider-reported usage, not the full-shape proxy.

The base tiered estimate normalizes to about `$0.13` per player-hour and `$0.13–$0.20` for a 60–90-minute slice only if turn density stays proportional. Real trace distributions, not this arithmetic, must decide whether the provisional p50 `<$1` and p95 `<$2` three-hour targets are viable.

## 12. Correlated latency model

Record both wall time and system-active time:

- `T_wall = final_player_rendered_at − input_accepted_at`, including explicit player confirmation/choice time;
- `T_user_wait = Σ explicit player-think/confirmation windows`;
- `T_active = T_wall − T_user_wait`, with asynchronous post-turn work reported separately; and
- `T_complete_resolution` runs through final validated narration or deterministic result template, not merely proposal completion.

For each actual trace, the no-repair critical path is approximately:

`T_active = T_context + T_M10 + T_validate/commit + Σ T_child_tool/random/apply + T_N40_complete + T_render/close`

Add actual transport attempts, `M12`, moderation/summary, and every extra narration leg. Compute p50/p95 over these complete same-trace totals. **Never add independent component p95s and label the result a turn p95.**

### 12.1 First-content definitions

| Metric | Starts | Ends | Does not qualify |
|---|---|---|---|
| First meaningful content | Input accepted | First validated public stakes, material clarification, unsupported/fallback explanation, or authoritative no-roll result | Spinner, typing dots, generic acknowledgement, unvalidated model text |
| First outcome content | Input accepted | First public applied result/template or validated narration release unit | Proposal prose, predicted outcome, or provisional `PUBLIC_AT_RANDOMNESS` value |
| Complete resolution | Input accepted | Final public authoritative result plus validated narration/template and closed hot-path trace | Background maintenance that does not gate the next turn |

### 12.2 Illustrative latency sensitivity

These are arithmetic what-if inputs, not vendor claims or measured percentiles. Player confirmation time is excluded but retained in the trace.

| Planning band | Context | Proposal complete | Validate/disclose | Child tools/random/apply | Narrator first delta after request | Narrator complete | Render/close | First meaningful | First public applied result | Complete, no repair | Repair add-on |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Fast-path assumption | 0.1s | 0.8s | 0.1s | 0.2s | 0.4s | 0.9s | 0.1s | 1.0s | 1.2s | 2.2s | 0.9s |
| Planning assumption | 0.2s | 1.8s | 0.2s | 0.5s | 1.0s | 2.5s | 0.2s | 2.2s | 2.7s | 5.4s | 2.0s |
| Tail stress assumption | 0.4s | 4.0s | 0.3s | 1.0s | 2.5s | 5.0s | 0.4s | 4.7s | 5.7s | 11.1s | 4.3s |

The tail row breaches the provisional 10-second complete-resolution target even without repair. That is the useful conclusion: streaming alone cannot rescue full-turn tail latency, and the system needs a cumulative breaker plus deterministic templates.

The “Narrator first delta” column assumes a certified validator can release a complete safe sentence/chunk. Under the fail-closed full-buffer baseline, first narration release equals narrator completion; the earlier public applied-result metric is unchanged.

### 12.3 Provisional cumulative budget

Allocate one **10-second system-active envelope** as a review hypothesis, not an accepted SLO:

| Pool | Candidate maximum | Degradation rule |
|---|---:|---|
| Trace/context/cache assembly | 0.5s | Use last certified local projection/minimal context or stop on version risk. |
| Proposal plus one mutually exclusive successor (semantic repair, transport replacement, or certified failover) | 4.0s aggregate | Render typed zero-mutation fallback by the 5-second first-meaningful boundary. Do not start a successor that consumes the reserved resolution/narration pool. |
| Validation, commitment, local child tools/random/apply | 1.0s system time | Preserve pending identity and pause if authoritative result is unavailable; never substitute a roll. |
| Post-result narration | 4.0s aggregate | Stream only after apply; switch to deterministic result template before the cumulative deadline. |
| Render and hot-path trace close | 0.5s | Mark reconciliation gaps without delaying public canonical result. |

Unused time may flow forward; later pools may not borrow time that makes an earlier player-facing guarantee false. Explicit player choice time pauses the active envelope. P1B-04 must test whether this allocation is achievable and whether the target's human-wait semantics need a versioned owner clarification.

## 13. Privacy-safe telemetry and provider data boundary

### 13.1 Central metadata allowlist

One record per provider attempt plus correlated stage summaries may contain:

- keyed/rotating pseudonymous session and turn/resolution IDs;
- call purpose and enumerated stage/parent/attempt/status;
- provider; requested/resolved model and snapshot; tier and processing region;
- prompt, persona, rules, adventure, projection, and tool/output-schema version IDs;
- rotating submission-key reference, admission outcome, non-content deletion epoch, queue/concurrency class, and reservation/release status and amount—never authentication credentials or the raw client key;
- request start, transport first byte, first valid event, first meaningful render, tool-result, apply, narration-first, completion, and cancellation timestamps;
- fresh, cache-read, cache-write, visible-output, and reasoning/thinking token counts as actually reported;
- enumerated tool call count/type, schema failure, authority/engine rejection, transport recovery, semantic repair, fallback, provider error class, cancellation, and finish reason;
- price-catalog version/date, rate categories, estimated call cost, currency, and provider request ID; and
- ledger reconciliation status and attribution gaps.

Operational telemetry must not contain raw or excerpted prompt/input, role-play, backstory, narration, hidden facts, commitment/tool arguments, dice/tool results, provider error text, model rationale, authentication secret, raw submission key, or a digest/hash of private text. Error and result values use approved enums/counts only. Canonical events and exact narration stay in the local game record until export or deletion under D13; central non-content metadata retention is 30 days unless the accepted deletion/legal policy requires earlier erasure. A tombstone is not a content recovery key and remains only for the approved straggler-suppression period.

Provider processing is a separate D4/P0-10 boundary. Calling project telemetry “metadata-only” does not imply that provider requests contain no scoped gameplay content. Before any provider commitment, review its training, abuse-log, application-state, cache, human-access, region, and deletion behavior against the exact endpoint/model/configuration.

### 13.2 Current verified provider facts used only as an example

Checked `2026-09-25` against official OpenAI documentation:

- API data is not used to train or improve OpenAI models unless the customer explicitly opts in.
- Default abuse-monitoring logs may contain prompts/responses and are retained up to 30 days, subject to documented exceptions.
- Modified Abuse Monitoring and Zero Data Retention require eligibility/approval and have endpoint/feature limitations; they must not be assumed.
- For `/v1/responses`, the documentation describes application-state response retention of at least 30 days by default or with `store=true`, with feature-specific behavior and exceptions. Endpoint, feature, organization controls, and the per-request `store` setting therefore require explicit verification; this draft's candidate baseline requires `store=false` where supported unless an accepted policy deliberately authorizes storage.
- `store=false` is not a deletion guarantee for other provider systems: it does not by itself erase abuse-monitoring logs or provider prompt-cache state. Those controls and their eligibility/retention must be reviewed separately.
- Streaming can deliver typed semantic events.
- Prompt caching reuses matching rendered prefixes; a session does not guarantee a hit; cache retention and behavior vary by model/organization; and the documented cache cannot be manually cleared, so expiry and disclosure must be handled in P0-10/provider review.

Sources: [OpenAI data controls](https://developers.openai.com/api/docs/guides/your-data), [streaming responses](https://developers.openai.com/api/docs/guides/streaming-responses), and [prompt caching](https://developers.openai.com/api/docs/guides/prompt-caching). These facts do not approve OpenAI or establish equivalence with another provider.

## 14. Provisional targets, breakers, and decision rules

All targets remain **PROVISIONAL** until full-turn P1B-04 evidence and P1B-05 owner acceptance or replacement; P2F-04/05 is only the documented contingency if Phase 1B is withdrawn.

| Dimension | Provisional target/control | Required denominator |
|---|---|---|
| Model tool-call validity | ≥95% valid first attempt; ≥99.5% after at most one retry; deterministic fallback <1% | Every model tool call in the fixed evaluation set; do not substitute proposals, turns, sessions, or logical resolutions as the denominator |
| First meaningful content | p50 ≤2s; p95 ≤5s | Complete correlated turns; definition in §12.1 |
| Complete resolution | p95 ≤10s; p95 >20s requires explicit owner acceptance rather than becoming normal | Every terminal logical turn, including fallback; system-active and wall time both reported |
| Three-hour inference spend | p50 <$1; p95 <$2 | Session-level sums of every call/tool/cache/failed attempt |
| Cache | Warm cache-read share ≥50% | Eligible input tokens, with misses/writes reported |
| Token bounds | Input p95 ≤20k and output p95 ≤800 billable tokens per logical turn | All provider attempts summed by turn, not per convenient call |
| Retry | Schema/engine semantic repair rate <5% | Eligible turns; transport recovery separate |
| Reconciliation | Internal request ledger within 2% of provider daily usage/cost | Daily provider account/export |
| Drift | Alert at >25% tokens/turn above accepted persona/adventure baseline | Same evaluation/session mix and configuration |

Candidate circuit breakers:

- authenticate/authorize every session submission, deduplicate its submission key, permit only the configured one-in-flight or bounded concurrency, and apply queue/rate admission before spend;
- atomically reserve the configured worst-case full-trace token/spend amount before any provider leg and reconcile actuals at `S60`; parallel requests cannot oversubscribe turn, session, or account/month limits;
- certify no provider-enabled candidate until every per-call, per-turn, per-session, and account/month cap is finite and non-null; an unset cap is `STOP_BUDGET_POLICY`, not unlimited service;
- stop new model calls when the per-turn remaining envelope cannot fund the required deterministic/tool/narration reserve;
- cap initial proposal, transport recovery, and semantic repair separately and globally;
- cap output tokens and context before sending;
- stop or downgrade at session/monthly spend limits without interrupting Delete/Stop/export;
- cap proposal generation at `M10` plus exactly one mutually exclusive successor—semantic repair, transport replacement, or failover—and prohibit automatic narration retry and parallel provider racing;
- disable provider tools for `M10/N40` by default; reject undeclared, recursive, autonomous, or cap-exceeding provider-tool calls;
- make Delete advance a tombstone/epoch before cancellation and erasure, and require every queued/in-flight completion to reject a stale/deleted epoch before any write, render, cache, summary, or retry;
- reject unpinned/drifted resolved model IDs from certified operation; and
- fall back deterministically on provider outage, price-catalog uncertainty, privacy-control mismatch, or missing usage fields.

Required adversarial fixtures for P0-13/P1B include sequential and simultaneous replay of one submission key; distinct parallel keys against one state version; a reservation race one unit below the account/session ceiling; missing/stale price or unset-cap admission; a provider requesting an undeclared or recursive tool; and Delete immediately before dispatch, mid-stream, between apply and narration, and during `B50`, followed by delayed provider/tool completions. Passing means at most one admitted spend path per configured slot, no cap oversubscription, no undeclared tool execution, and no post-delete gameplay-derived write, render, cache, summary, retry, or rehydration.

## 15. Producer/consumer handoffs

| Consumer | This draft supplies | Still required |
|---|---|---|
| P0-10 threat/data-flow model | Call/stage trust boundaries, provider/cache/telemetry data categories, cancellation and deletion obligations | Threat analysis, mitigations, provider/legal review; this draft does not solve P0-10. |
| P0-11 dice trust | Correlated random-stage identities and uncertain-delivery behavior | Cryptographic/audit claim and verifier; no proof is claimed here. |
| P0-12 contracts | Stage IDs, attempt taxonomy, usage/timing fields, fallback reason families | Versioned schemas, compatibility rules, fixtures, and consumer tests. |
| P0-13 test strategy | Choreography fixtures, invariants, full-trace denominators, cost/latency scenarios | Corpus, severity rubric, property/adversarial tests, and independent review. |
| ADR-0007/0015 | Candidate provider boundary, data questions, choreography, economics, and reversibility | Formal ADR amendment/finalization and owner acceptance; this draft accepts neither ADR. |
| P1B-02–05 | Candidate classes, exact tracing requirements, assumptions, targets, and decision rules | Executed ≥200-turn evaluation, full-trace distributions, quality/safety evidence, and go/change/stop decision. |
| P2-02/04/05/08/12 | Adapter, context, choreography, instrumentation, and bake-off obligations | Gated production implementation and later real-session evidence. |

## 16. Skeptical review checklist

- [ ] P0-07 is named provisional and its dependency is not claimed satisfied.
- [ ] No stage gives a model, narrator, provider tool, cache, or facilitator state/rules/correction authority.
- [ ] `AM01-R1` is the only bounded ruling referenced and is never generalized.
- [ ] Every initial, failed, repaired, moderation, narration, summary, maintenance, tool, and cache operation is attributable.
- [ ] Children remain one logical resolution and all tool/random latency remains in its trace.
- [ ] Proposal text is buffered; outcome text cannot stream before authoritative apply.
- [ ] Semantic repair, transport recovery, player clarification, result lookup, and rule-authorized reroll are distinct.
- [ ] Provider failover cannot reset caps or create parallel selectable outcomes.
- [ ] Authentication/authorization, submission deduplication, bounded concurrency, queue/rate admission, and atomic worst-case reservation occur before every provider call.
- [ ] Autonomous provider-tool loops are disabled; every enabled tool is a named finite stage charged to the same reservation and trace.
- [ ] Delete advances a tombstone/epoch before erasure; late provider or maintenance completions cannot write, render, cache, summarize, retry, or rehydrate content.
- [ ] Correlated full-turn percentiles are required; independent stage percentiles are not summed.
- [ ] Costs distinguish verified rates from scenario assumptions and include cold-cache/multi-narration sensitivity.
- [ ] Central telemetry has an explicit allowlist and no raw/private-text backdoor.
- [ ] Provider processing/retention is not confused with project-operated metadata telemetry.
- [ ] Quarantined P0-08 content is excluded.
- [ ] Deterministic fallback preserves state/result and never becomes an invented mechanic.
- [ ] No model, vendor, feasibility result, gate, ADR, production, or participant authorization is claimed.

## 17. Open blockers, review, and change control

P0-09 remains open after this draft. At minimum, acceptance requires:

1. accepted P0-07 and reconciliation of this choreography to its final exact authority/visibility/child-stage contract;
2. A2 review of proposal/narration schemas, prompt projections, retry/fallback, and candidate classes;
3. A8 review of formulas, price catalog, instrumentation completeness, circuit breakers, and reconciliation;
4. direct A3/A7/A6 handoff review of this draft's privacy/data-flow/provenance/test implications, without requiring downstream P0-10/P0-12/P0-13 completion;
5. current official-source verification for every external rate/product/data fact used in the accepted sensitivity, with unknowns labeled; and
6. a versioned P1B measurement plan capable of calculating same-trace distributions and testing quality, privacy, safety, full-turn latency, and session cost.

Phase 0 acceptance of P0-09 would freeze a reviewable choreography, accounting model, evaluation plan, and explicitly provisional targets. It does **not** require or claim executed P1B traces. Executed P1B-02–04 evidence and P1B-05 (or the inactive P2F-05 contingency) ADR amendments plus owner acceptance/replacement remain mandatory later, before the affected contracts harden or production AI integration is authorized.

P0-10/P0-12/P0-13 completion and actual-provider terms, retention, region, cache, usage-field, DPA/subprocessor, and qualified commercial/legal diligence are downstream requirements before vendor selection or integration; they are not circular prerequisites for accepting this Phase 0 planning artifact.

Open measurement decisions also remain: define how the existing 30/45/60 “turn” assumptions map to submitted interactions and logical resolutions; empirically reconcile the three-hour economic normalization with the accepted 60–90-minute slice; set per-turn, per-session, and monthly spend breakers; set an availability/error-budget target; and determine whether any provider-specific cache storage or synchronous moderation leg belongs in the certified baseline. None is silently filled in by this v0.1 arithmetic.

### Review record

| Review | Reviewer/date | Result | Boundary |
|---|---|---|---|
| Dependency/contract audit | Independent desk audit, 2026-09-25 | PASS for draft scope and required boundaries | Advisory only; no P0-07/P0-09 acceptance |
| Cost arithmetic/source check | Independent desk verification, 2026-09-25 | PASS — arithmetic and current official OpenAI sources verified | Advisory only; no executed trace/provider acceptance |
| Choreography red-team | Independent adversarial desk review, 2026-09-25 | PASS after denial-of-wallet and deletion-race repair | Advisory only; no named-human acceptance or implementation proof |
| Structural/link validation | Repository-wide local check, 2026-09-25 | PASS — 29 Markdown files; zero broken links, malformed tables, or fence errors | Syntax/discoverability only; no semantic acceptance |
| Required named-human/role review | `[OPEN]` | — | Required before P0-09 completion |

Any change to call count, narration frequency, tool hosting, cache retention, data region, candidate class, output/reasoning policy, fallback, or P0-07 authority must update the formulas and rerun the full-trace evaluation. A lower rate card never substitutes for quality, safety, visibility, or authority conformance.
