# P0-11 — Dice trust claim and verification protocol v0.1

> **STATUS: DESK-AUTHORED REVIEW DRAFT — PROVISIONAL / DEPENDENCY OPEN / NOT ACCEPTED / NOT IMPLEMENTED.** [P0-10 v0.1](P0-10-data-flow-and-threat-model-v0.1.md) remains provisional, dependency-open, unaccepted, and unimplemented, so this draft cannot satisfy P0-11's dependency or complete P0-11. This is a protocol and ADR proposal only. It supplies no implementation, executed cryptographic evidence, participant evidence, provider/runtime choice, accepted ADR, production authorization, or gate approval. Human research remains NO-GO and G0 remains closed.

- Document ID: `P0-11-DICE-TRUST-VERIFICATION`
- Version: `0.1`
- Prepared: `2026-10-04`
- Accountable roles: `A1 + A3`
- Required independent reviewers: `A6 + A7`
- ADR affected: `ADR-0005` (**PROPOSED / NOT ACCEPTED**)
- Candidate protocol label: `LOCAL-AUDIT-DICE-01`

## 1. Recommendation and exact claim

For the local, solo Phase 2 slice, adopt the smallest protocol that makes an honestly produced roll record independently reproducible: freeze the logical roll commitment before randomness, bind fresh authority-side CSPRNG words to one stable child-stage identity before interpreting them, map every die through specified rejection sampling, retain every raw/rejected word and selection, append a visibility-safe audit projection to a local integrity chain, and provide a separate read-only verifier.

The only proposed user-facing trust claim is:

> **Completed, authorized-visible rolls are locally auditable. Given an intact exported record and its supplied manifest/head, the independent verifier can reproduce the recorded dice and authorized-visible selection/mechanics; when every required input is available, it can also reproduce the modifiers and outcome, and otherwise it reports sealed inputs as unchecked. It can detect internal inconsistencies, required gaps relative to that manifest/head, reordering, duplication, or edits. Because the same local device controls execution and storage, this does not prove neutral dice, detect presentation of an earlier valid prefix or alternate complete history, or prevent the device owner, an administrator, malware, or a modified build from choosing, discarding, or fabricating a history.**

“Auditable” and “reproducible” are permitted only with the intact-record qualification. “Fair,” “verifiably fair,” “neutral,” “tamper-proof,” “unforgeable,” “non-repudiable,” and “cryptographically guaranteed” are prohibited for this Phase 2 topology unless a later accepted architecture supplies the missing external trust and evidence.

The sampling algorithm is designed to avoid range-reduction bias **if** its input words are uniform and the specified algorithm is executed. A matching record cannot prove either premise against the local authority that created it.

## 2. Dependency and authority boundary

| Input | State consumed by this draft | Consequence |
|---|---|---|
| P0-01 / D8a | Complete; local device is Phase 2 authority and eventual multiplayer may move authority to a hosted service | The local device generates and stores the authoritative result. The protocol must not imply independence from that device. |
| P0-01 / D10 | Complete; rule inputs are committed before rolls, hidden mercy is prohibited, and corrections/rewinds remain visible and consent-bounded | Dice evidence cannot authorize fudging, silent modifier changes, preferred rerolls, or correction erasure. |
| P0-01 / D13 | Complete; full local records remain local until authorized export/delete, while project telemetry is metadata-only | Raw random material, hashes, private commitments, and audit files never enter normal project telemetry. |
| Amended P0-03 | Accepted research contract | Actor, action, target, rule basis, difficulty/defense, modifier, advantage state, cost, possible outcomes, and visibility are frozen before randomness; state applies before narration. |
| P0-07 v0.1 | **Provisional / not accepted / not implemented** | Its parent/child commitment, authorized-window, result-identity, visibility, correction, and replay semantics are candidate inputs only. P0-11 cannot accept or extend them. |
| P0-09 v0.1 | **Provisional / dependency open / not implemented** | Its `E20 → E30 → R31 → E32 → W33 → E34 → E35` ordering and same-identity recovery are candidate choreography only. |
| P0-10 v0.1 | **Provisional / dependency open / not accepted / not implemented** | Its local CSPRNG, same-identity lookup, visibility/export, and device-owner adversary boundaries are inherited; P0-11 remains dependency-open. |
| Runtime, persistence, crypto library, and platform | Unselected | P0-12/P0-12A and later accepted ADRs must fix exact encodings, transactions, APIs, supported versions, platform CSPRNG, and reviewed implementation before code. |

The charter's older “server-side CSPRNG” wording means the **authoritative execution boundary**, not mandatory remote hosting. Accepted D8a places that boundary on the local device for Phase 2. A model, model provider, narrator, client rendering layer, user-entered seed, wall clock, or ordinary non-cryptographic PRNG is never the authority for production dice.

## 3. What each evidence tier does and does not establish

| Tier | Evidence available | Supported conclusion | Unsupported conclusion |
|---|---|---|---|
| `T0 — outcome only` | Face/total only | What the UI asserted | Reproduction, correct inputs, or fair generation |
| `T1 — structured audit` | Frozen inputs, raw values, selection, result, ancestry | A reviewer can recompute mechanics from the asserted raw values | Raw values were unpredictable or not selected |
| `T2 — local bound-material protocol` | T1 plus canonical commitments, raw-material binding, exact range mapping, and integrity chain | An independent verifier can reproduce the recorded mapping and detect internal inconsistency in the supplied history | The local authority did not grind raw material, selectively abort, rewrite the whole chain, or withhold another history |
| `T3 — externally witnessed binding` | T2 commitment observed by an independent timestamp/log/party before reveal | The later reveal is bound to what that witness observed, subject to witness availability and key/log trust | Neutral generation unless the entropy and abort rules also remove unilateral control |
| `T4 — independent or joint authority` | Hosted signed/VRF result or sound multiparty/public-entropy construction with fixed inputs, deadlines, and non-reveal handling | Stronger resistance to one local client's after-the-fact alteration or unilateral entropy choice | Freedom from hosted-operator, key-generation, input-choice, withholding, collusion, availability, or implementation risk |

Phase 2 proposes `T2`. A hash chain on the same mutable device is an integrity structure, not an external witness. It is valuable for crash/replay correctness, defect detection, portable verification, and honest dispute review; it is not evidence that a hostile owner preserved the only history.

## 4. Adversary assumptions

| ID | Actor or condition | Capability assumed | Required boundary |
|---|---|---|---|
| `DA-01` | Model/provider/narrator | Can suggest a roll, fabricate prose/results, retry, race, or time out | Has no randomness, commitment, selection, apply, correction, or verifier authority. |
| `DA-02` | Player input or replay | Can submit malformed, duplicate, stale, concurrent, or adversarial requests and can request an unauthorized reroll | Strict schema/auth/version/idempotency checks; one stage identity and at most one authoritative result. |
| `DA-03` | Ordinary crash, torn write, or unknown delivery | Can interrupt any transition or hide an acknowledgement | Durable state machine plus same-stage lookup/resume; never “try another roll.” |
| `DA-04` | Defective implementation/storage | Can introduce modulo bias, wrong selection, reordered events, duplicate results, or ancestry loss | Exact algorithm, strict verifier, golden/negative/property fixtures, and transactional evidence. |
| `DA-05` | Curious recipient of a player-view export | Can inspect and dictionary-guess visible commitments | Private commitments use a secret unpredictable blinding nonce; no hidden payload/nonce before authorized reveal; explicit partial-verification status. |
| `DA-06` | Local device owner, OS administrator, malware, debugger, or modified build | Can read memory/files, replace binaries/keys, call the CSPRNG repeatedly, discard unfavorable raw material, alter clocks, suppress exports, and fabricate a complete new local history | **Outside the protection claim.** Disclose the limitation; do not label local evidence neutral or tamper-resistant. |
| `DA-07` | Independent verifier defect or collusion | Can accept a malformed history or share the producer's bug | Separate implementation/review ownership, fixed public vectors, fail-closed parsing, and cross-implementation tests. This reduces common-mode risk but is not proof of absence. |
| `DA-08` | External hosted/log/beacon operator in a later topology | Can withhold service, rotate or misuse keys, choose inputs, collude, log metadata, or disappear | Later ADR must define keys, inputs, deadlines, non-reveal behavior, privacy, availability, anchoring, and exit; none is adopted here. |

The honest-operation assumptions for the proposed claim are: the accepted build and verifier execute the accepted protocol; the platform cryptographic RBG/CSPRNG is correctly implemented and supplied with adequate entropy; the exported history is the history the local authority retained; and no `DA-06` actor subverted or selectively curated execution. The verifier tests record consistency, not these assumptions.

## 5. Proposed `LOCAL-AUDIT-DICE-01` protocol

This section fixes the semantic protocol proposal. P0-12 must later define the exact byte-level schema and compatibility contract; P0-12A must evaluate implementation technology. No field below authorizes code or selects a crypto library.

### 5.1 Stable identities and immutable inputs

Before any **dice** random material is requested, the authority validates and durably appends one canonical commitment for the parent resolution and, where randomness occurs, one child roll stage. A private-field blinding nonce is separate commitment material, never dice entropy. The child identity is unique and includes at least:

- protocol/schema version, session identity, resolution identity, stage identity, and parent-stage identity; the engine derives the stage identity from canonical ancestry and a fixed ordinal rather than accepting a model/player-chosen grinding input;
- accepted pre-state version and relevant rules/content versions;
- actor, action, target, rule/capability basis, roll expression, die count and sides;
- difficulty/defense, modifiers, advantage/disadvantage or candidate-count rule, deterministic selection rule, cost, and possible outcome class;
- authorization for the roll and any later feature reroll/selection window;
- field-level visibility classes and private-commitment tokens; and
- the prior authoritative audit-chain digest.

The stage/result lookup identity is the tuple `(protocol_version, session_id, resolution_id, stage_id, commitment_digest)`. It is allocated once. Reusing it with different canonical bytes is a typed conflict; retry and status lookup reuse the original identity and never create new randomness. After `MATERIAL_BOUND`, the immutable raw-result evidence identity is a domain-separated SHA-256 digest over one canonical object containing that lookup identity, commitment digest, and raw-material digest; changing any bound word therefore changes the evidence identity rather than silently preserving it.

Exact canonical encoding is a P0-12 acceptance item. The candidate is strict, versioned deterministic CBOR consistent with RFC 8949 §4.2, with duplicate/unknown fields, non-canonical alternatives, unbounded integers/collections, and Unicode ambiguity rejected rather than normalized heuristically.

### 5.2 Private inputs

For each `PRIVATE_COMMITTED` or `AUDIT_RESTRICTED` payload, generate a fresh secret, unpredictable 256-bit **blinding nonce** from the platform cryptographic RBG before the parent commitment and calculate a domain-separated digest over one unambiguous canonical object containing protocol/schema version, stage identity, nonce, visibility class, and the canonical hidden payload. Nonce-generation failure stops before commitment, and a nonce is never reused or consumed as dice entropy. An authorized-visible audit projection may contain the resulting token and minimum type/version metadata only when their existence is itself authorized-visible; otherwise the token remains restricted and the player-facing verifier reports sealed inputs.

- A bare hash, or a hash with a public/predictable salt, does not hide a low-entropy DC, creature identity, branch, or modifier; the secret blinding nonce is mandatory and stays secret until authorized reveal.
- Commitment creation never changes the P0-07 reveal policy. Payload and nonce are disclosed together only at the already-authored reveal trigger or through a later separately accepted, spoiler-safe audit policy.
- P0-11 does not invent a public per-field token. If pre-reveal proof is later required where even field existence/type/count is secret, a constant-shape aggregate commitment must be designed and reconciled under accepted P0-07/P0-10/P0-12 policy.
- A verifier without authorized private material reports `SEALED_INPUTS_NOT_CHECKED`; it may still reproduce the random stream and public mechanics but must not report the entire resolution fully verified.
- Commitment tokens, blinding nonces, hidden values, and raw random material are prohibited from normal project telemetry. Player-view export includes only authorized tokens/material under §9.

### 5.3 State machine and unbiased mapping

Each roll stage advances monotonically:

`COMMITTED → MATERIAL_BOUND → RESULT_BOUND → APPLIED`

It may instead enter a typed terminal or paused state such as `REJECTED_BEFORE_RANDOMNESS`, `RANDOMNESS_UNAVAILABLE`, `MATERIAL_CORRUPT`, `MATERIAL_EXHAUSTED`, or `RESULT_INVALID`. No error transition authorizes a replacement draw.

1. **`COMMITTED`:** append and durably acknowledge the canonical commitment and its SHA-256 digest before asking for randomness.
2. **Obtain raw material:** request the protocol-bounded ordered buffer of fresh words from the authoritative platform cryptographic RBG/CSPRNG. Production mode never accepts a user/model/date/time seed, reusable session seed, provider-generated roll, ordinary non-cryptographic PRNG, or predictable test-seed hook.
3. **`MATERIAL_BOUND`:** atomically persist the full ordered buffer under the committed stage before mapping, display, or apply. Bind it with a domain-separated digest over one canonical envelope containing the protocol version, stage identity, commitment digest, fixed byte order/word width, buffer length, and raw words. Once this state commits, normal recovery cannot replace or extend the buffer. P0-12 must freeze the buffer bound and exhaustion behavior; exhaustion is an explicit failure, never permission to request a favorable replacement or fall back to biased mapping.
4. **Map without modulo bias:** for each die with `s` sides (`1 < s ≤ 2^32`), consume the next big-endian unsigned 32-bit word `x`, define `L = floor(2^32 / s) × s`, reject `x ≥ L`, and otherwise use `(x mod s) + 1`. Continue in order until each declared die has an accepted word. Record every accepted and rejected word and draw index. For example, d6 has `L = 4,294,967,292`; the top four words reject. Bounds make exhaustion a typed failure, not fallback to simple modulo reduction.
5. **Select deterministically:** map every rule-authorized raw die/candidate; apply only the precommitted advantage/disadvantage, feature, or selection rule; retain all candidates and identify the one(s) used. A favorable result is not a validation criterion.
6. **`RESULT_BOUND`:** atomically append the raw-material digest, consumed/rejected words, faces, deterministic selection, modifiers, total, outcome, commitment links, and resulting public-audit-chain digest. At most one authoritative result may bind to the stage. Unconsumed words remain scoped to this completed stage and are never reused for another stage.
7. **`APPLIED`:** validate the result against the still-current pre-state/version and atomically append the authoritative state transition. Narration follows apply and must cite, not reinterpret, the committed result.

The hash and exact mapping support deterministic reconstruction and binding inside the record. They do not certify that the local process requested only one buffer, called the RBG at the asserted time, or refrained from fabricating the record. No filesystem transaction is atomic with an OS randomness call: material lost in the gap before `MATERIAL_BOUND` is not observable in the retained record. This is an ordinary crash-recovery boundary under the honest-device assumption and a selective-abort/grinding avenue under `DA-06`, so the protocol claims at most one **bound** material/result sequence—not one physical RBG call.

### 5.4 Authorized rerolls, child windows, and selection

- An SRD/accepted-feature reroll, replacement, extra candidate, damage die, or other random sub-operation is a separately identified child stage with its own frozen commitment and fresh bound raw material.
- The parent commitment must predeclare whether the window exists, who may invoke it, its limit/cost, and how its child result is selected or combined. P0-11 creates no new rule or player option.
- Every child and raw result remains in ancestry, including unused candidates and abandoned branches. “Reroll because the result was bad,” provider race, validation retry, timeout retry, and facilitator override are prohibited.
- The finite `W33` intervention window may consume only an authority already present in the accepted rules/contract. Closing it binds the declared selection exactly once.

### 5.5 Crash, replay, unknown delivery, and correction

| Observed durable state | Required recovery | Prohibited response |
|---|---|---|
| No `COMMITTED` record | Revalidate the original request; a later admitted resolution receives its own identity | Pretend a roll occurred |
| `COMMITTED`, no `MATERIAL_BOUND` | Resume the same stage and obtain/bind one material buffer. Lost pre-bind bytes are not authoritative and cannot be distinguished from selective abort against `DA-06`. | Allocate another stage merely to obtain a better result |
| `MATERIAL_BOUND`, no `RESULT_BOUND` | Recover the same stored buffer and deterministically complete the same stage | Replace/extend the buffer, call the RBG again, or label a new roll a retry |
| `RESULT_BOUND`, acknowledgement unknown | Query and return the same result identity | Roll again, race replicas, or select among completions |
| `RESULT_BOUND`, pre-state/version no longer valid | Preserve the result under its original identity and enter typed conflict/correction handling | Rebind the result to different inputs/state |
| Bound material or committed bytes unavailable/corrupt | Stop with an explicit indeterminate/failure state and preserve evidence | Generate substitute randomness or silently repair history |

A correction appends a new event/branch with reason, actor, consent/authority, parent ancestry, and supersession relationship. It never edits/deletes the original commitment, raw material, result, state transition, or narration. Fresh randomness is permitted only if replay under the accepted corrected state legitimately reaches a newly authorized roll stage; it cannot be selected because the original result was unfavorable.

### 5.6 Audit-chain rule

Maintain two explicit projections rather than hashing a private record and later trying to redact it:

1. the full restricted authority record, which retains every authorized private field, nonce, raw word, result, apply, and correction under P0-10 storage/visibility controls; and
2. an allowlisted public audit envelope containing public fields plus only those opaque randomized commitment tokens whose existence and minimum metadata are already authorized-visible. Other tokens remain solely in the restricted record and produce an explicit partial-verification status.

Each public envelope contributes canonical bytes to a domain-separated SHA-256 chain entry whose named fields include the previous public-chain digest, event type, protocol/schema version, stable identity, sequence, parent references, and public payload. The hash is not a substitute for ordering or authorization. When a private value becomes revealable, a later public reveal event supplies its payload and blinding nonce and links them to the existing token; the old envelope is not rewritten.

This detects internal edits, required gaps relative to the supplied manifest/head, duplication, and reordering. It does not prove that the head was published at a certain time, expose an omitted valid tail, or show that an earlier valid prefix or alternative complete chain never existed. Local signing with a key controlled by the same device would not change that adversary boundary. External timestamp/log anchoring is a later option, not a Phase 2 baseline.

## 6. Protocol comparison

| Candidate | What it adds | What it can support | Decisive limitation | Phase 2 disposition |
|---|---|---|---|---|
| Plain structured audit log | Frozen inputs, raw values, selection, ancestry | Mechanics review and basic replay | Producer can edit raw values/history; no cryptographic binding of stage, raw material, or projection | Too weak as the accepted target; retain its human-readable fields inside the recommended record. |
| **Local committed stage + bound CSPRNG words + rejection sampling + public integrity chain + independent verifier** | Pre-randomness content binding, pre-interpretation raw-material binding, exact mapping, strict chain/state checks | Strong defect/replay detection and reproducibility of an intact honest-device record | Same local authority can grind, selectively abort, replace software, withhold, truncate, or fabricate a whole history | **Proposed `LOCAL-AUDIT-DICE-01`; smallest proportionate Phase 2 protocol.** |
| Local signature or Merkle log only | Efficient inclusion/consistency proof and/or signed root | Detection after a root reaches an independent observer | A local key/log alone remains under local-owner control; before external publication it does not prevent alternate histories | Not adopted; preserve future-compatible chain/root fields. |
| External timestamp/transparency anchor | Independent evidence that a digest existed before an asserted time; later consistency checks | Stronger post-anchor tamper evidence | Metadata/network/privacy/availability/operations; still does not make locally chosen entropy neutral | Compare later if disputes justify the cost. |
| Hosted signed authority or VRF | Removes ordinary client control; a VRF makes output for a fixed key/input publicly checkable and unique | Stronger client-tamper resistance and portable proof | Trust shifts to host/key generation/input binding; host can withhold service and a broader log/privacy/incident surface appears | Eventual hosted/multiplayer option; not adopted for local Phase 2. |
| Multiparty commit–reveal | Combines independently committed contributions before revelation | Reduces unilateral entropy choice when at least one contribution is honest and inputs are bound | Last revealer can selectively abort unless deadlines/non-reveal consequences and availability are defined; extra UX and recovery complexity | Later multiplayer research only. |
| Precommitted future public beacon pulse | External public entropy not yet known at commitment time | Reduces local prediction/choice if timing/input binding and beacon trust hold | Network dependency, outage/reorganization/trust, metadata, and selective session abandonment remain | Later comparison only; no beacon dependency in Phase 2. |

The eventual hosted decision should prefer the least powerful scheme that closes a demonstrated threat. A VRF, beacon, or commit–reveal protocol is not automatically superior: it adds key lifecycle, service availability, privacy metadata, clock/input binding, recovery, and operational trust. Phase 3 must revise the threat model and ADR rather than relabel this local protocol.

## 7. Proposed ADR-0005 decision

**Status:** `PROPOSED / NOT ACCEPTED`. Formal ADR completion and owner acceptance remain P0-15 work.

**Proposed decision:** For the local Phase 2 slice, standardize `LOCAL-AUDIT-DICE-01` as a `T2` reproducible-audit protocol and use only the exact qualified trust claim in §1. Bind accepted roll inputs to a stable stage before randomness; bind a bounded buffer of fresh authoritative platform-CSPRNG words before interpretation; apply fixed 32-bit rejection sampling; preserve public audit projection and append-only ancestry; and supply a separate offline verifier. Do not add a local session seed, remote authority, external anchoring, beacon, VRF, or multiparty commit–reveal to Phase 2. Preserve versioned identities and public-chain heads so a later hosted ADR can migrate without reinterpreting old evidence.

**Why:** It materially improves correctness, crash/replay behavior, user inspection, and independent defect detection over a plain audit log while matching the accepted local-first, single-player topology. Anything that resists the local owner requires an external trust boundary and operations that the Phase 2 product neither needs nor has accepted.

**Consequences:**

- “Auditable/reproducible from an intact record” replaces any unqualified fairness claim.
- Exact encoding, platform RBG boundary, 32-bit word extraction, material-buffer limit, transaction semantics, export schemas, compatibility, and test vectors become blocking P0-12/P0-13 contract work.
- P1A-05 must implement the accepted version behind the authoritative boundary and pass the independent verifier; test determinism may use explicit test fixtures only, never predictable production seeding.
- Private fields can leave public verification partial until their accepted reveal trigger; trust UX must say so plainly.
- The local-owner threat remains accepted residual risk for the private solo slice, not a silently “mitigated” item.
- Hosted/multiplayer work must reopen ADR-0005 alongside ADR-0008 and P0-10 rather than treating local hashes as a hosted fairness proof.

**Reversal/migration:** Protocol versions never reinterpret old bytes. A later authority writes a new protocol version and trust tier, preserves old roots/records with their original claims, supplies a version-aware verifier and migration/export plan, and explicitly handles key rotation, external anchors, non-reveal, and legacy sessions.

## 8. Independent verification method

The verifier is a separate, read-only, offline-capable executable or package with independent ownership/review from the dice producer. It consumes an authorized export plus a declared protocol/schema version and returns machine-readable findings and a concise human report. It never repairs the record, generates replacement randomness, writes authoritative state, requests hidden data, or calls a network service.

For every completed stage it must, in order:

1. strictly decode canonical records and reject unsupported versions, duplicates, unknown critical fields, ambiguous encodings, broken limits, and malformed identities;
2. verify sequence/parent ancestry, prior public-chain links, stage/private/raw-material commitment digests, and monotonic stage transitions;
3. confirm the full parent/child roll commitment precedes `MATERIAL_BOUND` in the supplied history and is unchanged thereafter;
4. consume the bound words in order and reproduce every rejection-sampling attempt, face, advantage/disadvantage or authorized child selection, and each authorized-visible modifier/total/outcome; sealed mechanics remain unchecked and force the partial result;
5. enforce at most one bound material buffer/result per identity and identify gaps relative to the supplied manifest/head, duplicates, substitutions, reordering, orphans, or post-result mutation;
6. verify apply/correction ancestry against exported authoritative events without deleting an unfavorable or superseded branch; and
7. check visibility manifests before rendering findings, reporting `SEALED_INPUTS_NOT_CHECKED` rather than inferring or exposing a hidden payload.

Every report returns two orthogonal fields: one record result and one anchor status. The separation prevents an internally consistent local bundle from being presented as externally witnessed.

| Record result | Meaning |
|---|---|
| `REPRODUCED` | Every required authorized input was present and every exported deterministic step matched. This is record consistency, not neutral-execution proof. |
| `REPRODUCED_WITH_SEALED_INPUTS` | Randomness/public mechanics matched, but one or more private committed inputs were not authorized for reveal and were not checked. |
| `INCOMPLETE` | Required records/material are missing or a stage is legitimately pending/failed; no fairness inference. |
| `UNSUPPORTED_VERSION` | The verifier cannot safely interpret the declared protocol/schema. |
| `FAILED` | At least one strict integrity, identity, derivation, selection, mechanics, ancestry, or visibility check failed. |

| Anchor status | Meaning |
|---|---|
| `LOCAL_UNANCHORED` | No independently retained checkpoint was supplied. This is the normal and only supported Phase 2 status. A valid prefix or alternate full history cannot be excluded. |
| `EXTERNAL_CHECKPOINT_VERIFIED` | A future supported verifier matched an independently obtained checkpoint. This status is reserved and unsupported by the Phase 2 protocol. |
| `EXTERNAL_CHECKPOINT_NOT_PROVIDED` | The bundle declares an external-checkpoint protocol, but no checkpoint was supplied. |
| `EXTERNAL_CHECKPOINT_FAILED` | A supplied future checkpoint did not validate. |

Downstream P0-12/P0-13 contract evidence and P1A-05 implementation acceptance evidence must eventually include the following. These executed artifacts are **not** prerequisites for accepting this P0-11 planning proposal; P0-11's backlog done evidence is the ADR proposal, threat assumptions, independent verification method, and UX evidence plan, subject to its P0-10 dependency and required review.

- published canonical byte and end-to-end golden vectors covering d2, d4, d6, d8, d10, d12, d20, d100, pools, advantage/disadvantage, multi-die damage, rejected candidates, child rerolls, and visibility tokens;
- a second implementation or independently authored oracle agreeing on every vector;
- mutation tests for each committed field and byte; truncation relative to a supplied manifest/head, reordering, duplicate, fork, swapped raw material, wrong version/endianness/domain, modulo shortcut, word reuse, child-selection, stale-state, crash-boundary, same-ID replay, and correction-ancestry fixtures;
- property tests showing outputs always lie in range and deterministic re-verification is exact; distribution tests may detect gross defects but never certify fairness from a sample;
- platform CSPRNG failure/injection tests, including fail-closed bounds and separation of production from explicit deterministic test mode; and
- reproducible build/provenance, dependency review, parser fuzzing, and independent A6/A7 evidence review before P1A-05 implementation acceptance.

## 9. Visibility-safe inspection and export

The default roll surface shows human-readable notation, raw public dice, advantage/disadvantage or child selection, modifier, total/outcome, and a short audit status. An expandable “How this roll was determined” view shows the stable roll reference, committed public inputs, authorized correction ancestry, and verifier/export action without requiring cryptographic vocabulary.

`PLAYER_VIEW_EXPORT` may contain:

- public commitment fields and private commitment tokens already visible to the player;
- the full bound word buffer—including rejected and unused stage-scoped words—plus deterministic selection, result, protocol/schema versions, and public-chain material only for completed stages whose roll evidence is authorized-visible;
- already-revealed private payload/blinding-nonce pairs only after their authored reveal trigger; and
- an explicit manifest of omitted/sealed classes and the resulting verification level.

It must exclude unrevealed private payloads/blinding nonces, `AUDIT_RESTRICTED` material, hidden-roll material, future or pending raw material, signing/authority secrets, report/safety secrets, and any cross-session linkage. The exporter applies authorization before retrieval, creates one version-consistent snapshot, and obeys P0-10's Delete/export linearization. Deleting a session necessarily deletes its local audit evidence; no later audit claim survives unless the player already made an authorized export outside product control. A `FULL_AUDIT_EXPORT` remains unsupported until P0-07/P0-10 and qualified privacy/security review accept its audience, spoiler timing, retention, deletion, and handling.

Hash-like tokens can themselves be identifiers or dictionary targets; they receive the same visibility, minimization, retention, and export analysis as the fields they bind. They are never sent to central telemetry merely because they are not plaintext.

## 10. UX evidence plan

This is a plan, not observed evidence. Synthetic desk checks may proceed; participant recruitment, contact, and research remain NO-GO until the existing human preflight and GO controls close.

### 10.1 Questions to answer

1. Can a player state, without prompting, what the audit status proves and what it does not prove about the local owner?
2. Before randomness, can the player identify the action, die expression, modifier/advantage state, difficulty/defense disclosure state, and consequence class that are already fixed?
3. After a roll, can the player find raw dice, selection, modifier, outcome, child/reroll ancestry, and any correction without reading hashes?
4. Does unknown delivery read as “checking the same roll,” never an invitation to roll again?
5. Does `REPRODUCED_WITH_SEALED_INPUTS` communicate useful partial verification without leaking or falsely validating hidden content?
6. Are audit, correction, and export controls keyboard reachable, screen-reader coherent, mobile readable, and clearly separate from Pause/Stop/Report?

### 10.2 Controlled evidence sequence

| Stage | Material | Evidence sought | Gate boundary |
|---|---|---|---|
| Desk content review | Exact §1 claim, status labels, tooltips, sealed-input and failure copy | A4/A6/A7 find no neutrality overclaim, hidden-data cue, or safety-control confusion | Advisory only |
| Synthetic state walkthrough | Normal roll, advantage, authorized child reroll, rejected proposal, CSPRNG unavailable, crash at every state, unknown delivery, stale apply, visible correction, sealed input, export/delete race | Every state has one non-misleading action and no “roll again” recovery | Not implementation evidence |
| Accessibility inspection | Static/mobile prototypes and semantic control map | Reading/focus order, names/status announcements, contrast/non-color cues, target sizes, reduced-motion behavior | Named accessibility review still required |
| Later moderated comprehension study | Same frozen wording/prototype and neutral tasks | Precommitted comprehension/error thresholds, qualitative confusion taxonomy, and accessibility findings | Only after separate human GO; no recruitment now |
| Implemented usability/evidence run | Version-matched build, verifier, corrupted fixtures, assistive technology/platform matrix | Task completion, correct claim comprehension, defect recognition, no hidden disclosure, no duplicate roll | Requires implementation authorization and accepted protocol |

Before any human study, P0-14 must precommit participant profile, task script, success thresholds, stopping/safety rules, data collection/retention, accessibility accommodations, and analysis method. A favorable demo or self-review cannot substitute for those results.

## 11. Threat/control and fixture handoff

| Risk | Candidate control/evidence | Residual boundary |
|---|---|---|
| Biased range mapping | Rejection sampling, frozen byte order/width, boundary vectors and property tests | Cannot prove source-word uniformity or honest execution against `DA-06`. |
| Raw-material grinding | Stage commitment before RBG request; at most one durably bound buffer/result; crash fixtures | Local owner can exploit the pre-bind gap, bypass/modify the producer, or fabricate history. |
| Selective abort/withholding | Durable `MATERIAL_BOUND`, explicit indeterminate state, no substitute result after binding, preserve pending stage | Local owner can abandon the app/session, discard unbound bytes, or withhold the record; only an external observer can strengthen this. |
| Duplicate/timeout reroll | Stable raw-result identity and same-ID lookup | Storage/transaction bugs remain until implemented and fault-tested. |
| Hidden-input dictionary attack | Fresh secret high-entropy blinding nonce and delayed reveal | Payload size/timing/token existence may still leak; field-by-field review required. |
| Preferred child selection | Precommitted finite window/selection; retain every child | Accepted rule semantics and P0-07 remain open. |
| Whole-history rewrite | Chain plus independent verifier | No protection without an external trusted copy/anchor. |
| Correction laundering | Append-only reason/actor/consent/ancestry and preserved original result | Human misuse remains possible and must remain visible. |
| Verifier common-mode bug | Independent implementation/oracle, public vectors, fuzz/mutation tests | Independence and review must be demonstrated, not inferred from a separate folder. |
| Audit leaks private content | Authorization-before-retrieval, sealed status, spoiler-safe export manifest | Exact policy depends on P0-07/P0-10 and qualified review. |

P0-13 must assign durable fixture IDs for at least: commitment mutation; same-ID/different-body replay; duplicate result; crash before/after each transition; raw-material swap/reuse/corruption; forced rejection word; modulo-bias implementation; bad endianness/domain/version; unauthorized child reroll; preferred-result selection; stale apply; correction branch; low-entropy private-field guessing; premature nonce/private/hidden-roll material export; public-chain truncation/reorder/fork; alternate-head presentation; restore/fork identity reuse; Delete/export race; production test-seed hook; and verifier fail-open behavior.

## 12. Limitations and open decisions

P0-11 remains open after this draft. Before acceptance:

1. P0-10 must be accepted or this artifact reconciled to its accepted authority, visibility, export/delete, threat, and telemetry contract.
2. P0-07 must be accepted and its exact private reveal, child window, correction, full-audit, and result-identity semantics reconciled, even though it is not a formal backlog dependency of P0-11.
3. A1/A3 must own the exact protocol and recovery semantics; A6 must independently review testability and cryptographic claims; A7 must review visibility, privacy, provenance, and export implications; A0 must review contract coherence.
4. This proposal must hand off explicit blocking obligations to P0-12/P0-13 to later freeze and review canonical bytes, hash/domain fields, 32-bit word extraction/order, raw-buffer/exhaustion limits, transaction boundaries, schemas, compatibility, verifier interface, vectors, and fixtures. Those downstream tasks are not prerequisites for accepting this planning artifact, but their accepted outputs and executed evidence are prerequisites to implementation acceptance.
5. Exact supported platform CSPRNGs, runtime/library provenance, secret-memory/crash behavior, packaging, and update/rollback path remain P0-12A/implementation decisions.
6. ADR-0005 remains proposed until formal P0-15 acceptance. No user-facing trust claim ships before the accepted protocol and independent evidence exist.

Known irreducible Phase 2 limitation: a hostile local authority can inspect or resample raw material before binding, generate alternatives, fabricate commitments and timestamps, alter both producer and verifier, delete an unfavorable session, present an earlier valid prefix, or present a different complete history. No arrangement of hashes stored only under that authority converts it into a neutral dealer. The mitigation is honest scope language and later external authority if the product threat model comes to require it.

## 13. Producer and consumer handoffs

| Consumer | This draft supplies | Still required |
|---|---|---|
| P0-12 contracts | Candidate identities, commitment/raw-material/result fields, state machine, visibility/export and compatibility obligations | Exact versioned encodings/schemas, limits, errors, transactions, producer/consumer ownership, and fixtures |
| P0-12A runtime/persistence ADR | CSPRNG, durable atomic transition, strict canonicalization, verifier isolation, and recovery requirements | Technology/library comparison, platform proof, dependency/provenance, rollback, and migration |
| P0-13 test strategy | Threat assumptions, verifier method, negative/property/fault fixture classes, critical claim boundaries | Requirements-to-test map, harnesses, severity rubric, owners, and executed evidence |
| P0-14 human protocol | Exact trust claim, inspection/export interactions, comprehension questions, and evidence sequence | Approved precommit targets, materials, privacy/accessibility/safety controls, human GO, and real evidence |
| P0-15 / ADR-0005 | Proposed local protocol, alternatives, consequences, residual risk, and migration trigger | Formal ADR text, cross-ADR reconciliation, named review, and owner acceptance |
| P1A-05 | Accepted-protocol target and independent-verifier acceptance shape | Prior gates, implementation, test vectors, platform evidence, and independent pass |
| Eventual hosted/multiplayer design | Trust-tier ladder and candidate external options | New threat model/ADR, authority/key/input/abort/privacy/availability design, and executed evidence |

This document does not start or complete any consumer task.

## 14. Primary references and interpretation boundary

- [NIST SP 800-90A Rev. 1](https://csrc.nist.gov/pubs/sp/800/90/a/r1/final) specifies deterministic random bit generator mechanisms, [SP 800-90B](https://csrc.nist.gov/pubs/sp/800/90/b/final) addresses entropy sources, and [SP 800-90C](https://csrc.nist.gov/pubs/sp/800/90/c/final) describes random bit generator constructions combining those components. They frame later platform evidence; this proposal does not claim that an unselected OS API conforms.
- NIST's [2022 decision to revise SP 800-22](https://csrc.nist.gov/news/2022/decision-to-revise-nist-sp-800-22-rev-1a) explicitly rejects using that statistical suite to assess cryptographic RNGs. Distribution tests here are defect screens, never proof of source quality or fair execution.
- [RFC 4086](https://www.rfc-editor.org/rfc/rfc4086.html) documents security requirements and failure modes for randomness. It supports the prohibition on predictable production seeds; it does not certify a selected platform source.
- [RFC 9415](https://www.rfc-editor.org/rfc/rfc9415.html) explicitly describes distribution distortion from simple modulo mapping and rejection sampling as the uniform range-reduction method. This artifact applies that general technique to dice; it does not claim RFC 9415 is a dice protocol.
- [FIPS 180-4](https://csrc.nist.gov/pubs/fips/180-4/upd1/final) defines SHA-256. Its use supplies a standardized hash, not proof that the surrounding local protocol defeats its owner.
- [RFC 8949 §4.2](https://www.rfc-editor.org/rfc/rfc8949.html#section-4.2) defines deterministic CBOR encoding requirements relevant to later canonical schemas.
- [RFC 9162](https://www.rfc-editor.org/rfc/rfc9162.html) provides an append-only Merkle-log model with inclusion and consistency proofs. It is a later transparency pattern; this proposal does not claim Certificate Transparency properties for a local linear chain.
- [RFC 3161](https://www.rfc-editor.org/rfc/rfc3161.html) defines a trusted timestamp protocol that can evidence that a datum existed before a time. It is cited only as an external-anchoring comparison.
- [RFC 9381](https://www.rfc-editor.org/rfc/rfc9381.html) defines verifiable random functions and their uniqueness/verifiability properties for fixed inputs/keys. It is an eventual hosted option, not a claim that VRFs alone solve input choice, key trust, withholding, or availability.
- [Blum, “Coin Flipping by Telephone”](https://www.cs.cmu.edu/~mblum/research/pdf/coin/) is the foundational commit–reveal comparison. The [Bicorn paper](https://eprint.iacr.org/2023/221) directly discusses the last-revealer refusal/selective-abort problem and recovery approaches; this draft adopts none of those constructions.

These references are design sources, not certification, conformance, implementation evidence, or a substitute for specialist cryptographic review.

## 15. Skeptical review checklist

- [ ] The exact §1 claim is used without dropping the intact-record and hostile-local-owner qualifications.
- [ ] “Unbiased” describes the mapping conditional on correct uniform source words/execution, not verified real-world fairness.
- [ ] All consequential inputs and private tokens bind before the RBG request; result favorability never controls validation, retry, or correction.
- [ ] One stable stage receives at most one durably bound material buffer and result; unknown delivery uses lookup/recovery, not new randomness after binding.
- [ ] Every reroll/candidate is an authorized child with fresh bound raw material, a finite selection rule, and preserved raw ancestry.
- [ ] A crash after `MATERIAL_BOUND` resumes the same buffer or fails explicitly; corruption never authorizes a substitute.
- [ ] Correction preserves original commitment/result/state/narration and cannot launder a preferred reroll.
- [ ] Private commitments use secret blinding nonces, remain visibility-scoped, and produce an explicit partial-verification result while sealed.
- [ ] Public/player export excludes hidden payloads/nonces, hidden/pending raw material, authority secrets, reports, and cross-session data.
- [ ] Hash chain/local signatures are never described as an external timestamp, independent witness, neutrality proof, or protection from `DA-06`.
- [ ] Seed grinding, selective abort, whole-history fabrication, alternate-root, verifier compromise, and session withholding remain explicit limitations.
- [ ] Hosted signatures/VRFs, external anchors/beacons, and multiparty commit–reveal are compared without adoption or automatic superiority claims.
- [ ] No model/provider, runtime/library, schema, gate, ADR, production, participant, recruitment, or human-research authorization is implied.

## 16. Review, acceptance, and change control

| Review | Reviewer/date | Result | Boundary |
|---|---|---|---|
| Dependency/contract audit | Independent desk audit, 2026-10-04 | PASS after dependency-cycle and sealed-token visibility repairs; cross-link/status coherence confirmed | Advisory only; no P0-07/P0-10/P0-11 acceptance |
| Cryptographic/source review | Independent primary-source desk review, 2026-10-04 | PASS after raw-material/crash-gap, truncation, anchor-status, private-blinding, and export repairs | Design/source accuracy only; no cryptographic implementation certification |
| Trust-claim/adversarial red-team | Independent desk red-team, 2026-10-04 | PASS after protocol simplification; no remaining material trust-claim defect found | Advisory only; no hostile-device resistance or executed evidence |
| Structural/link validation | Repository-wide local check plus primary-source fetch, 2026-10-04 | PASS — 31 Markdown files; zero broken local links, malformed tables, fence errors, or diff whitespace errors; all 13 cited external sources resolved | Syntax/discoverability/current-source reachability only; no semantic or implementation proof |
| Required named-human/role review | `[OPEN]` | Not performed | Required before P0-11 completion |

Any change to authority location, multiplayer scope, commitment/reveal timing, entropy source, derivation/range algorithm, stage identity, child/reroll rule, correction, visibility, export/delete, verifier, signing/anchoring, protocol version, runtime, or persistence requires a versioned reconciliation of this proposal, P0-07/P0-09/P0-10, ADR-0005/0006/0008, affected contracts, fixtures, migration, and trust copy before adoption.
