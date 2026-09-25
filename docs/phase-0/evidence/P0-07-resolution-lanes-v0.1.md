# P0-07 — Resolution lanes and authority contract v0.1

> **STATUS: DESK-AUTHORED REVIEW DRAFT — PROVISIONAL / NOT ACCEPTED / NOT IMPLEMENTED.** This artifact defines a candidate contract for review; it does not complete P0-07, complete P0-06, authorize participant work, open G0, or authorize production implementation. P0-04 and P0-05 fieldwork remain NO-GO.

- Document ID: `P0-07-RESOLUTION-LANES`
- Version: `0.1`
- Prepared: `2026-09-25`
- Accountable roles: `A1 + A2`
- Controlling inputs: [P0-03 vertical-slice specification](P0-03-vertical-slice-spec.md), [P0-03 Amendment 01](P0-03-amendment-01-proposed.md), [P0-06 provisional coverage matrix](P0-06-coverage-matrix.md), and [P0-06 provisional operator baseline v0.2](P0-06-provisional-operator-baseline-v0.2.md)
- Evidence boundary: `SPEC_ONLY / NOT IMPLEMENTED / P0-05 NOT OBSERVED`

## 1. Purpose and non-authority

This document fixes a reviewable candidate for the three resolution lanes required by P0-07:

1. `DETERMINISTIC_MECHANIC`;
2. `BOUNDED_RULING_AM01_R1`; and
3. `UNSUPPORTED_CLARIFY`.

It covers lane admission, inputs, validators, visibility, commitment timing, correction authority, failure behavior, examples, and producer/consumer implications. It is a contract specification, not production code or an operational fielding sheet.

The three lanes are exhaustive only after the system has passed safety, contract-integrity, and state-integrity checks. A safety halt, missing authoritative field, source conflict, stale or unrepresented state, visibility risk, or impossible invariant is a **contract-defect stop**, not a fourth lane and not a player-caused unsupported result.

This draft deliberately narrows the bounded-ruling lane. The only executable bounded ruling in the accepted slice is `AM01-R1`. P0-03's permission to define a closed ruling schema does not authorize a model, facilitator, operator, or future implementer to invent another ruling, DC, effect, condition, item capability, creature ability, tactic, route, or branch at runtime.

## 2. Authority and precedence

Resolve conflicts in this order:

1. out-of-band `Pause`, `Stop`, and active-play `Report` controls;
2. owner decisions D10/D15 and the desk-only boundary in `OD-2026-09-25-01`;
3. accepted P0-03 plus accepted Amendment 01, with Amendment 01 controlling conflicts;
4. a reviewed, version-matched P0-06 catalog entry, while recognizing that the current matrix and operator baseline are provisional;
5. this P0-07 version after acceptance;
6. typed proposals, player text, facilitator notes, and narration, none of which is authority.

If an apparent resolution cannot be derived without skipping a level, filling a blank, reconciling a contradiction by judgment, or broadening an entry, stop with `STOP_CONTRACT_DEFECT`. Do not improvise and do not route the defect through `UNSUPPORTED_CLARIFY`.

### 2.1 Current-slice policy decisions proposed by v0.1

| Topic | v0.1 policy | Boundary |
|---|---|---|
| Exact DC/defense | Show the exact DC, AC, or other defense before the player finally confirms a voluntary roll-producing choice and always before randomness | Conservative continuation of the accepted P0-05 full-disclosure convention; requires P0-07 acceptance before becoming the Phase 2 policy |
| Other authoritative fields | Show the actor, action, target, basis, modifier, Advantage/Disadvantage, cost, and player-actionable consequences before randomness | Hidden narrative payloads remain separately visibility-scoped |
| Hidden facts | Commit the exact hidden payload and reveal trigger before related randomness; reveal the payload only through its authored trigger or an authorized audit path | Concealment changes disclosure timing, never authority or post-roll selection |
| Bounded rulings | Only `AM01-R1` is admitted | No generic live ruling, contextual bonus, improvised DC, or new ruling ID |
| Proposal retry | One structured-proposal repair against the same authoritative state/version | Player clarification is separate; neither permits repeated paraphrase loops |
| State mutation | Only the authoritative state/event boundary applies a validated committed delta | The model, narrator, UI, and content text never write authoritative state |

If review rejects the visibility recommendation, replace it through a versioned P0-07 revision. Do not silently use a different reveal policy.

## 3. Terms and universal invariants

### 3.1 Terms

- **Proposal:** non-authoritative structured interpretation of an intent. It may be rejected or repaired without changing game state.
- **Commitment:** the immutable, version-bound authoritative resolution record fixed before randomness, or before mutation for a no-roll action.
- **Resolution graph:** the finite, preauthored parent sequence of possible random stages, automatic branches, conditional costs, and explicitly admitted post-result option windows.
- **Child commitment:** an append-only record linked to the parent that selects one preauthored triggered branch and fixes every field required before that branch's next random operation or mutation.
- **Intervention window:** a cataloged timing window—such as Heroic Inspiration after a Rin-owned roll—in which the accepted rule permits a named later choice. It is not a general post-roll edit.
- **Pending-command lock:** a non-gameplay, non-consuming idempotency/concurrency record created after a committed selection. It prevents duplicate resolution but does not decrement a resource, consume an action/Reaction/use, change canonical gameplay state, or authorize narration.
- **Public projection:** only the commitment fields the player is authorized to see at that moment.
- **Private commitment:** authoritative hidden content fixed before resolution but excluded from public/model/UI projections until an authored trigger or authorized audit.
- **Resolution event group:** the append-only authoritative record that applies one committed result/checkpoint and its state transition as an ordered unit. A parent may require several groups, with each applied before the next stage binds.
- **Clarification:** one neutral question used only when actor, target, rule, cost, visibility, or consequence would materially differ.
- **Typed fallback:** a non-authoritative, reason-coded response used after a proposal cannot be validated; it cannot roll or mutate state.
- **Contract-defect stop:** a fail-closed halt caused by missing, conflicting, stale, leaking, or unrepresented authority/state. It is not a resolution lane.

### 3.2 Invariants

| ID | Invariant |
|---|---|
| `RL-INV-01` | Every admitted resolution has exactly one lane label and one reason code. |
| `RL-INV-02` | A proposal, rationale, facilitator statement, or narration cannot create authority or mutate canonical state. |
| `RL-INV-03` | Before the first random operation, the parent fixes actor, action, target, authority, DC/defense, modifier, Advantage/Disadvantage, base/conditional costs, complete finite resolution graph, possible mechanical outcomes, visibility, and pre-state version. |
| `RL-INV-04` | For no-roll authoritative actions, the same fields are fixed before mutation. |
| `RL-INV-05` | A committed field is never edited in place. A triggered child may select only a branch already present in the parent and must bind its stage fields before that stage's next randomness/mutation. Any other change requires a visibly voided commitment and a new parent commitment. |
| `RL-INV-06` | State/result events are applied before outcome narration. Narration may describe only the visibility-scoped committed result. |
| `RL-INV-07` | Visibility affects disclosure only; it cannot permit a later rule, DC, target, consequence, or hidden-payload choice. A later player choice is legal only in a named cataloged intervention window whose options and consequences were fixed in the parent graph. |
| `RL-INV-08` | `AM01-R1` is the entire bounded-ruling registry for this slice. No pattern-matching or analogy may generalize it. |
| `RL-INV-09` | An unsupported or clarified intent consumes no action, turn, resource, item, Reaction, or authoritative state and causes no roll. |
| `RL-INV-10` | A model proposal receives at most one repair against the same state/version; exhaustion returns a typed fallback or hard stop, never an improvised event. |
| `RL-INV-11` | Transport retry or replay uses the same stage/correlation/idempotency identity and can never create a fresh selectable roll. Separately admitted feature rolls are new child stages, not retries. |
| `RL-INV-12` | Corrections are append-only and visible within the viewer's scope. Valid unfavorable results are not errors. |
| `RL-INV-13` | A discretionary rewind identifies a checkpoint, requires Rin's player's explicit consent, preserves the abandoned branch, and never selects a preferred reroll. |
| `RL-INV-14` | Safety pause/stop/report preempts lane selection, randomness, mutation, narration, correction, and retry. |
| `RL-INV-15` | Downstream consumers receive least-privilege projections; they never receive an over-broad state object and filter secrets locally. |
| `RL-INV-16` | Every random operation has a unique stage identity and at most one authoritative result. Multiple rolls or result selection exist only where an accepted feature explicitly requires them; all raw results, the rule-authorized selection, and the final used result are retained. |
| `RL-INV-17` | Selecting an action or intervention may create only a pending-command lock before its apply checkpoint. Actual action/resource/Reaction/use costs and results enter gameplay state together in the ordered authoritative event group. |

## 4. Common resolution envelope

### 4.1 Commitment fields

The eventual P0-12 command/event schemas may rename fields, but they must preserve these semantics.

| Field group | Required content | Rule |
|---|---|---|
| Identity | Parent resolution ID, stage/child ID, causation/correlation IDs, idempotency key, schema version | Stable across delivery retries; never reused for a different operation or resolution |
| Intent | Stable reference to the player's input, normalized goal, and any single clarification answer | Raw private text is not copied into broader projections merely for convenience |
| Lane | Exact lane enum and reason code | Exactly one of the three lane values; stops are recorded separately |
| Actor and target | Actor, target, and authority/seat | Both must exist in the committed pre-state and be legal for the entry |
| Authority | P0-06 entry ID, rules/content IDs, source/provenance class, locator, and contract version | `AM01-R1` must remain labeled `PROJECT_ORIGINAL`, not SRD text |
| State binding | Expected state/event version and, when specified later, state hash or equivalent replay identity | A stale binding cannot be silently refreshed after the roll |
| Timing | Phase, turn, trigger, interrupt point, terminal state, and pending transaction | The exact temporal window must be legal before commitment |
| Spatial and visibility context | Zones, engagement, accepted distance, line of sight, and viewer-scoped field map | Uses the accepted 5/10/20/40-ft. mappings; no inferred grid or hidden-state leak |
| Costs and prerequisites | Action/Bonus Action/Reaction, movement, resource/item/hand state, use counters, conditions, prerequisites, and every conditional cost rule | Availability and conditional cost timing are fixed in the parent; selection may create only a non-consuming pending-command lock; the actual cost delta is applied with the accepted checkpoint result |
| Test/stage graph | Roll/no-roll stages, dice owner, die expression, DC/AC/defense, modifier components, Advantage/Disadvantage sources/cancellation, triggers, and stage ordering | Every possible stage is closed before the first roll; a triggered child fixes its exact operation before obtaining that operation's randomness |
| Outcomes | Exhaustive result predicates, cataloged intervention windows, and exact allowed state deltas, including failure-forward and terminal behavior | No narration-only or unenumerated post-result choice may add a fact or mechanical effect |
| Visibility | Per-field disclosure class and authored reveal trigger for each private payload | Projection occurs before retrieval by a model or UI consumer |
| Choice | Initial player confirmation or accepted automatic trigger/algorithm basis, plus each cataloged intervention option | Initial choice may be withdrawn without cost before first-roll authorization; a later choice is allowed only in its committed intervention window |
| Correction ancestry | Superseded/voided commitment, compensation, fork, or dispute reference | History is appended and preserved, never overwritten |

`UNSUPPORTED_CLARIFY` records only the minimum intent reference, classification/reason, clarification count, alternatives offered, visibility scope, and audit ordering. It has no DC, roll, cost, or authoritative delta.

### 4.2 Resolution order

1. Honor an out-of-band safety control immediately; do not classify a gameplay lane.
2. Read a least-privilege public/private projection appropriate to the caller.
3. Normalize the intent without adding actor, target, effect, or advantage.
4. If a material field remains ambiguous, record `UNSUPPORTED_CLARIFY / CLARIFY_MATERIAL_AMBIGUITY` with zero authoritative delta, ask the one neutral question, and end this classification attempt. Treat the answer as causally linked new input against the then-current authoritative state; no second clarification is permitted for that intent.
5. Otherwise, select exactly one lane from explicit catalog authority.
6. Run all applicable validators against one authoritative state version.
7. Assemble the full visibility-scoped parent commitment, including the finite stage graph, every admitted intervention window, and its public projection.
8. Show the player-actionable stakes. For a voluntary choice, allow confirmation or cost-free withdrawal before roll authorization.
9. Freeze the parent commitment. Any unenumerated later field change voids it visibly and returns to step 6 with a new parent ID.
10. Process the next stage from the committed graph. If an accepted result opens a cataloged intervention window, show only its precommitted options; record the player's selection or decline and freeze a linked child commitment before the next random operation or mutation.
11. Obtain each stage's randomness under its unique child/stage identity. Obtain at most one authoritative result per operation; an accepted feature that calls for a reroll or two candidate rolls creates the exact additional operations fixed by that feature. The raw results may be shown as `PUBLIC_AT_RANDOMNESS`, but they cannot independently authorize narration or state mutation.
12. Retain every raw result and rule-authorized selection. At each catalog-defined apply checkpoint, close its applicable intervention windows, validate the checkpoint result, and atomically append/apply its resolution event group.
13. Produce projections and narrate only the applied public checkpoint. If the committed parent graph continues, bind the next child to the new authoritative state/version and return to step 10; a terminal checkpoint cancels forbidden later stages.

For a no-roll deterministic action, the parent still freezes before mutation and only an admitted no-roll child choice may select a preauthored branch. For an automatic opponent behavior, the player does not approve the opponent's legal action, but any player-actionable risk must have been disclosed before the player's triggering choice.

### 4.3 Exact check/DC authoring admission

A check can enter the deterministic catalog only through a versioned authoring record that contains all of the following:

- stable check/action ID and version;
- SRD versus `PROJECT_ORIGINAL` authority class with exact locator(s);
- allowed intent/approach set and exact applicability predicate;
- actor, target, phase, timing, attempts/no-retry rule, and prerequisites;
- exact ability, skill, tool, attack, save, or other admitted test type;
- exact DC/defense or a deterministic formula whose complete inputs are already authoritative;
- every modifier and Advantage/Disadvantage source/cancellation rule;
- action/resource/item/movement costs and all conditional spend/refund rules;
- finite parent/child stage graph and any accepted intervention windows;
- exhaustive success, equality, failure, failure-forward, recovery, and terminal deltas;
- field-by-field visibility/reveal triggers, reason codes, unsupported behavior, and fixtures.

A difficulty label, range, “appropriate DC,” analogy, facilitator judgment, or model-selected number is not an authoring record. The current slice retains its accepted exact DCs; any new or changed check/DC requires a versioned accepted contract change and downstream fixture impact review.

## 5. Visibility and reveal timing

### 5.1 Disclosure classes

| Class | Meaning | Examples in this slice |
|---|---|---|
| `PUBLIC_BEFORE_CHOICE` | Available early enough to inform a voluntary choice | Supported action, known resource cost, reachable zone, `AM01-R1` OA risk before provoking movement |
| `PUBLIC_BEFORE_RANDOMNESS` | Visible after the choice is formed but before final confirmation/roll | Exact DC/AC, modifier, Advantage/Disadvantage, rule/ruling basis, roll formula, public possible consequences |
| `PRIVATE_COMMITTED` | Fixed before randomness in the authoritative private projection; absent from public/model retrieval until an authored trigger | Exact NPC concern before successful `CHK-02`; unrevealed content payload or branch label |
| `PUBLIC_AT_RANDOMNESS` | The bound random result is visible when authoritatively obtained; it carries no independent mutation authority | Visible attack/check/damage dice and their commitment identity |
| `PUBLIC_AFTER_APPLY` | Revealed only after the authoritative result/state event exists | Success/failure, damage application, public state delta, triggered fact |
| `AUDIT_RESTRICTED` | Retained for authorized correction/provenance/security review and never automatically disclosed during play | Private commitment payload whose trigger never occurs; operational defect detail that would leak hidden state |

The commitment mechanism in this document is a logical immutability requirement, not a cryptographic claim. P0-11 owns the dice/commitment protocol recommendation; P0-10 and P0-12 own trust boundaries, storage, projections, and concrete schemas.

### 5.2 Exact policy for v0.1

- Every current-slice DC, AC, defense, modifier, Advantage/Disadvantage state, resource cost, and public mechanical consequence is `PUBLIC_BEFORE_RANDOMNESS`.
- A system-presented option must disclose, before selection, its support status; action/Bonus Action/Reaction, resource, item, movement, and other costs; target/range legality; and every player-actionable, irreversible, terminal, or triggered risk. Free text creates only a tentative proposal: the system must then show the complete public commitment—including the exact DC/defense under v0.1—and obtain explicit cost-free final confirmation before authorizing the first roll. A field that cannot be classified this way is `STOP_CONTRACT_DEFECT`, not an operator judgment about whether disclosure is “enough.”
- The standing nonlethal order is disclosed and recorded after initial positions and before Initiative, exactly as Amendment 01 requires. `AM01-R1` is explained before combat and its risk is shown again before Rin confirms voluntary movement that would provoke it.
- A private narrative fact is committed in full before any related roll. The public projection may describe the type of result—such as “success reveals the NPC's concern”—without exposing the payload.
- A private payload becomes public only through its authored reveal event. If its trigger never occurs, it stays private during play; any later audit access must be explicit, least-privilege, and spoiler-aware.
- A commitment token may be projected publicly only when the token's existence does not itself reveal a secret. P0-11 must not be preempted by claiming that this draft already provides cryptographic verification.
- The narrator receives the projected result, not the over-broad commitment. It cannot infer, retrieve, or disclose a `PRIVATE_COMMITTED` or `AUDIT_RESTRICTED` field.

## 6. Validator set and dispositions

Validators run before commitment and again where the returned result crosses the authoritative boundary.

| ID | Validator | Required rejection/stop behavior |
|---|---|---|
| `RL-V01` | Safety/control preemption | Halt immediately; no gameplay retry or mutation |
| `RL-V02` | Schema/version/required fields | One proposal repair if the defect is solely in a non-authoritative model proposal; otherwise stop |
| `RL-V03` | Lane exclusivity and reason code | Reject mixed, blank, generic-ruling, or unknown lane |
| `RL-V04` | Authority/source/provenance | Stop on missing/conflicting locator, non-admitted entry, unknown provenance, or SRD/project mislabeling |
| `RL-V05` | Expected state/version/idempotency | Before any bound result, reject stale state and re-read once before a new player-confirmed parent. After a stage result exists, preserve that result/audit but apply nothing; stop/correct and never rebind, reuse, or reroll it under a new commitment. |
| `RL-V06` | Actor/target/phase/turn/trigger | Reject illegal actor, target, time, interrupt, or terminal state |
| `RL-V07` | Position/range/engagement/visibility | Reject unrepresented spatial state or visibility leak; never infer an exact grid |
| `RL-V08` | Action economy/resources/items/hands/conditions | Reject unavailable cost, illegal hand state, depleted use, invalid condition interaction, or conditional spend/refund not present in the parent graph |
| `RL-V09` | Resolution specification/stage | DC/defense, modifier, Advantage/Disadvantage, dice expression/owner, allowed stages, roll count, and selection rule must derive from the admitted catalog, parent graph, and committed state; reject any other specification |
| `RL-V10` | Outcome/intervention/state-delta allowlist | Reject an incomplete outcome set, new effect, new branch, narrative mutation, or post-result choice outside a named accepted intervention window |
| `RL-V11` | Invariants/terminal ordering | Stop or reject any result that would violate HP, resources, terminal state, nonlethal order, or event ordering |
| `RL-V12` | Visibility projection | Stop before retrieval or display if a consumer would receive an unauthorized field |
| `RL-V13` | Correction authority | Reject silent edit, unconsented discretionary rewind, branch deletion, or preferred reroll |
| `RL-V14` | Returned randomness/result | Accept only a raw result bound to its stage identity, valid for the committed expression/range, and verifiable under the later accepted P0-11 protocol; uncertain delivery is queried by identity, never rerolled speculatively; feature-authorized rerolls/candidate rolls use distinct committed child stages |

### 6.1 Reason/disposition classes

| Code | Meaning | State effect |
|---|---|---|
| `RESOLVE_DETERMINISTIC` | Admitted deterministic entry validated | Apply only the committed delta |
| `RESOLVE_AM01_R1` | Exact bounded ruling validated | Apply only the one-Slam OA event group |
| `CLARIFY_MATERIAL_AMBIGUITY` | One allowed neutral clarification is required | None |
| `FALLBACK_CLARIFICATION_UNRESOLVED` | The single clarification was used but the intent is still materially ambiguous | None; state that no authoritative resolution was identified and offer only validated alternatives |
| `REJECT_UNSUPPORTED` | Intent is known to be outside the accepted envelope | None |
| `FALLBACK_PROPOSAL_INVALID` | One structured-proposal repair failed | None; present a typed clarification/fallback |
| `STOP_CONTRACT_DEFECT` | Authority, provenance, or frozen data is missing/conflicting | Pause dependent resolution; none |
| `STOP_STATE_MISMATCH` | State is stale, unrepresented, or violates an invariant | Pause dependent resolution; none |
| `STOP_VISIBILITY_RISK` | Required projection cannot be made without disclosure | Halt retrieval/display; none |
| `STOP_RANDOMNESS_UNAVAILABLE` | No authoritative result exists and randomness cannot be obtained safely | Preserve the pending parent/child commitment and pause; none |
| `STOP_SAFETY_CONTROL` | Pause, Stop, or active Report preempts play | Halt as defined by the safety contract |
| `CORRECT_COMPENSATION` | A predefined deterministic compensating event repairs an invalid system event | Append visible compensation; preserve original event |
| `CORRECT_FORK_PROPOSED` | No safe predefined compensation exists | Pause and propose a preserved fork; consent rules apply |

## 7. Lane D — deterministic mechanic

### 7.1 Admission

An intent enters `DETERMINISTIC_MECHANIC` only when all of the following are true:

- its mechanic, character/monster field, item use, state transition, or authored branch predicate is explicitly admitted by the accepted P0-03/Amendment 01 contract and represented by a version-matched `IN` or `IN-ORIGINAL` P0-06 entry;
- every authoritative input can be derived from the committed state and authored catalog without live judgment;
- the exact possible state deltas are closed and validated; and
- any narrative wording is downstream of the authoritative event.

An authored feasibility or approach predicate is deterministic only when the accepted content/rules records already enumerate the predicate, allowed approach, DC/defense, and outcomes. “Reasonable in the fiction” is not authority.

### 7.2 Lane-specific inputs and validators

Use the common envelope plus the exact P0-06 entry, content predicate/version, source locator, action/resource state, and closed outcome mapping. Apply all common validators. `RL-V04`, `RL-V09`, and `RL-V10` must prove that neither a model nor an operator supplied a discretionary number or effect.

### 7.3 Visibility and commitment

All non-hidden resolution fields are public before randomness. Hidden authored payloads are committed privately and revealed only by their trigger. The deterministic lane commits before mutation even when no die is rolled.

### 7.4 Admitted multi-stage and post-result mechanics

The parent commitment must enumerate every possible stage below before the first roll. When a listed trigger occurs, a linked child commitment binds the exact next operation or no-roll option before it executes. These accepted windows do not authorize any analogous feature or general post-roll discretion.

| Accepted mechanic | Triggered option/stage | Required record and boundary |
|---|---|---|
| Attack → damage | A committed attack result is a hit or critical hit | Retain the attack dice/result; derive the already-enumerated normal/critical damage formula; freeze a child damage commitment before rolling damage; no damage stage on a miss except an already-committed Graze branch |
| Heroic Inspiration | Immediately after the participant rolls a Rin-owned die | Parent enumerates eligibility and one-Heroic-Inspiration cost; if selected, bind the exact original die and create a non-consuming pending lock, roll one replacement, retain both, then atomically consume the resource and use the replacement result even if worse; never reroll a Watcher-owned die |
| Tactical Mind | A committed ability check is provisionally failed | Parent enumerates the feature and `1d10`; if selected, create a pending conditional-use lock and freeze the child before rolling; the final event spends one Second Wind use only if the addition changes failure to success, otherwise its gameplay resource delta is exactly zero while the attempt remains audited—do not emit a spend-plus-refund gameplay pair |
| Savage Attacker | Rin has a qualifying weapon hit and the once-per-turn feature is available | If selected, create a non-consuming pending once-per-turn lock, roll the committed weapon-damage pool twice, retain both candidates, record the player's rule-authorized selection, then apply the chosen damage and once-per-turn used state together; on a critical each candidate uses the admitted critical weapon-dice pool |
| Remarkable Athlete | Rin scores a qualifying critical hit | Offer only the admitted immediate 0/5/10/15-ft. no-OA movement states; validate the selected state before applying it; it cannot cross a 20-ft. edge or bank movement |
| Rin's nonlethal final blow | A qualifying melee attack would reduce the Watcher to 0 HP | The parent already enumerates lethal 0 HP versus the admitted knockout option; if the player selects knockout, set Watcher to 1 HP, apply Unconscious, begin but do not complete a Short Rest, and end combat as victory; a thrown Javelin cannot open this window |

The engine may record provisional raw results while a checkpoint's windows are open, but it cannot narrate that checkpoint's outcome or apply its authoritative delta until those windows close. A feature decline is recorded and does not permit the same window to reopen for that trigger. Where the accepted rule requires intermediate state—such as each Slam in Multiattack—the checkpoint applies before the next child stage binds.

### 7.5 Example `P007-D-01` — authored traversal

| Field | Committed value |
|---|---|
| Intent | Rin uses Dexterity (Acrobatics) to traverse the Broken Sluice |
| Authority | P0-06 `CHK-06`; accepted P0-03 fixed check sheet |
| Lane/reason | `DETERMINISTIC_MECHANIC` / `RESOLVE_DETERMINISTIC` |
| Test | Dexterity (Acrobatics) `+2` vs. DC `13`; no Advantage/Disadvantage unless another admitted, applicable entry validates before commitment |
| Public before roll | Actor, approach, DC 13, +2 modifier, dice owner/formula, no-damage rule, no-retry rule, and both timing outcomes |
| Success | Reach the tower and preserve current `arrival` timing |
| Failure | Open the safe route, reach the tower, set `arrival=late`; deal no damage; no retry |
| Forbidden mutation | Changing the DC, adding damage, blocking the tower, inventing a bonus, or choosing the branch after the roll |

### 7.6 Failure and fallback

- If the player intent is materially ambiguous, emit the zero-mutation `UNSUPPORTED_CLARIFY / CLARIFY_MATERIAL_AMBIGUITY` record and ask one neutral question. Classify the causally linked answer afresh; do not continue the original commitment.
- If the intent is known to be outside the envelope, route to `UNSUPPORTED_CLARIFY` without a roll or state change.
- If a required deterministic field is absent, conflicting, stale after one re-read, or not represented, use a contract/state stop. Do not call the player's intent unsupported.
- A non-authoritative model proposal may be repaired once against the same state/version. A second invalid proposal returns `FALLBACK_PROPOSAL_INVALID`.
- If randomness delivery is uncertain, query by the same stage identity. Never issue a speculative second roll. If no result exists and the source is unavailable, preserve the pending parent/child commitment and pause at `STOP_RANDOMNESS_UNAVAILABLE`.
- If result application succeeds but narration fails, keep the authoritative result and use a deterministic public result template. Do not roll or apply again.

## 8. Lane R — bounded ruling `AM01-R1`

### 8.1 Registry

| Ruling ID | Narrow project-authored decision | Separately traced mechanics and explicit exclusions |
|---|---|---|
| `AM01-R1` | The Watcher Harness's Slam counts as its melee attack for an Opportunity Attack; the OA is exactly one Slam, never Multiattack, consumes its Reaction, uses `+4` to hit, and resolves before the provoking movement | Slam attack/damage uses `CMB-09`; public order uses `CMB-12`; mandatory knockout/Unconscious/terminal behavior uses `REC-01`, `STA-04`, `CMB-11`, and `STA-08`. No Rin/general-creature authority, other attack, non-OA use, new reaction, tactic, DC, effect, route, or analogy is granted. |

Only the Slam-as-Watcher-OA eligibility and one-Slam constraint are the `PROJECT_ORIGINAL` bounded ruling. Opportunity Attack timing, Reaction, attack resolution, visible `1d6+2`/critical `2d6+2` Slam damage, the knock-out mechanic, the Unconscious state, and Short Rest initiation retain their separate SRD/project trace. None may be attributed to `AM01-R1` alone or presented as quoted or implied SRD text.

### 8.2 Preconditions and validators

All must be true before the OA roll:

1. actor is the Watcher Harness and target is Rin;
2. both are nonterminal and engaged at 5 ft.;
3. Rin has confirmed voluntary movement that would leave engagement;
4. the movement is not Disengage, forced movement, or another explicitly admitted OA-free movement;
5. the Watcher's Reaction is available;
6. timing is immediately before Rin spends the provoking first 5 ft.;
7. range, visibility, AC 17, `+4` attack, damage dice, critical rule, and mandatory nonlethal order match the accepted state and catalog; and
8. no prior event has already consumed the Reaction or terminated combat.

If all preconditions are true, the deterministic Watcher policy takes this first legal OA automatically; no model, operator, or facilitator may decline it. If any suppression condition is true, no OA occurs. If a required fact is missing or contradictory, stop; do not substitute Multiattack, another attack, or operator judgment.

### 8.3 Visibility and commitment

The Watcher's standing nonlethal order must already have been disclosed after initial positions and before Initiative, with `operating_order_visible=yes` recorded. The OA risk, exact one-Slam limit, attack modifier, Rin's AC, damage formula, Reaction cost, timing, and possible terminal nonlethal consequence are public before Rin confirms provoking movement. Once Rin confirms:

- bind the OA to the current pre-movement state and pending movement transaction;
- commit one Slam, never Multiattack;
- keep the movement unapplied until the OA resolves;
- obtain and apply the bound attack/damage result; and
- only if the result is nonterminal, continue the already-confirmed movement.

### 8.4 Example `P007-R-01` — legal Watcher OA

| Field | Committed value |
|---|---|
| Pre-state | Rin and Watcher engaged; Watcher Reaction available; combat nonterminal |
| Player choice | Rin confirms voluntary movement out of engagement without Disengage |
| Lane/reason | `BOUNDED_RULING_AM01_R1` / `RESOLVE_AM01_R1` |
| Authority | Narrow ruling: Amendment 01 `B-07`, `AM01-R1`, P0-06 `CMB-07`; first-legal policy: `MON-19`; attack/damage/order/knockout/state/ending: `CMB-09`, `CMB-12`, `REC-01`, `STA-04`, `CMB-11`, and `STA-08` |
| Resolution | Before movement: spend/resolve one Watcher Slam at `+4` vs. Rin AC 17; on hit roll `1d6+2`, or `2d6+2` on a critical |
| Miss/nonterminal hit | Mark Reaction spent, then complete the already-confirmed legal movement |
| Terminal hit | Consume the Reaction; leave Rin at 1 HP; apply the full Unconscious state; begin but do not complete a Short Rest; produce the accepted failure ending; cancel pending movement/further attacks |

### 8.5 Negative and suppression cases

- Rin Disengages: suppress the OA; do not spend the Reaction.
- Rin is moved forcibly: suppress the OA.
- Watcher Reaction is spent: suppress the OA.
- Rin does not leave engagement: no trigger.
- All preconditions are valid but the model/operator proposes declining the OA: reject the proposal and execute the first legal `AM01-R1` OA; there is no discretion to waive it.
- A proposal requests Watcher Multiattack as the OA: reject it; do not “repair” it into two attacks.
- A proposal uses `AM01-R1` for Rin or another creature/attack/context: `REJECT_UNSUPPORTED` if it is a player request; `STOP_CONTRACT_DEFECT` if authored system content claimed that authority.

### 8.6 Failure and fallback

- A pre-roll validation failure causes no OA roll, Reaction spend, movement, or damage.
- An uncertain randomness delivery is recovered only by the same commitment identity; never generate another selectable attack result.
- If randomness is unavailable before a result exists, preserve the pending parent/child commitment and unapplied movement transaction, pause without mutation, and report `STOP_RANDOMNESS_UNAVAILABLE`.
- If an invalid OA event was applied, use the correction policy in §10. Never hide the event or select a more favorable reroll.
- The typed fallback must describe the halt without inventing a ruling. It may offer Disengage or another already-supported action only if the current public state still validates it.

## 9. Lane U — unsupported/clarify

### 9.1 Admission

Use `UNSUPPORTED_CLARIFY` in either of two zero-mutation cases:

1. `CLARIFY_MATERIAL_AMBIGUITY` — one neutral question is needed because actor, target, rule, cost, visibility, or consequence would materially differ; or
2. `REJECT_UNSUPPORTED` — the intended mechanic or authoritative effect is known to be outside the accepted envelope.

Unsupported examples include mechanical Stealth/Hide, a Torch attack or fire effect, improvised damage/effects, an unlisted item benefit, added creature, alternate route/ending, unlisted Watcher tactic, spellcasting, or any unlisted SRD mechanic.

Do not use this lane to conceal a malformed proposal, missing catalog entry that should exist, version conflict, unrepresented state, provenance problem, or visibility risk. Those are system/contract stops.

### 9.2 Clarification contract

For `CLARIFY_MATERIAL_AMBIGUITY`, append the lane/reason record before asking exactly one neutral question. The question must not coach a preferred tactic, reveal hidden information, or silently narrow the intent to something supported. The answer is a causally linked new classification against current state, not an in-place edit of the original record.

If the answer remains materially ambiguous, record `FALLBACK_CLARIFICATION_UNRESOLVED`, state that no authoritative resolution was identified, confirm that nothing was rolled/spent/changed, and offer only validated public alternatives. Do not falsely label the unknown mechanic unsupported.

If the answer is known to be outside the envelope—or immediately when the initial intent is already clearly unsupported—record `REJECT_UNSUPPORTED` and:

1. acknowledge the player's goal;
2. identify the specific unsupported mechanic;
3. state that nothing was rolled, spent, or changed; and
4. offer one to three nearby supported options only when they genuinely preserve the goal and validate against current public state.

If no nearby supported option exists, say so plainly. Never invent one to keep the story moving.

### 9.3 Example `P007-U-01` — Stealth/Hide request

Player input: “I hide in the fog and sneak past.”

- If it is unclear whether the player wants effect-free flavor or a mechanical advantage, ask once: “Do you mean Rin moves quietly as description only, or are you trying to gain a mechanical Stealth/Hide benefit?”
- Effect-free quiet narration is allowed only if it creates no fact, advantage, hidden state, avoidance, or branch.
- A mechanical Stealth/Hide request is `UNSUPPORTED_CLARIFY` / `REJECT_UNSUPPORTED` under Amendment 01 `B-01` and P0-06 `CHK-08`.
- Roll no Stealth check, consume no action/resource, and change no position, engagement, visibility, or encounter state.
- Offer only currently legal supported alternatives, such as an admitted traversal approach outside combat or Disengage/Dodge in combat; validate before displaying them.

### 9.4 Failure and fallback

- One clarification is the maximum. Rephrasing loops do not create authority.
- If a structured proposal remains invalid after one repair, return a typed fallback; do not transform the model defect into a gameplay penalty.
- Alternative generation is non-authoritative. Each alternative must pass the same visibility and catalog checks before display.
- The lane may append a non-state audit record for measurement, but that record cannot consume a turn or alter game state.

## 10. Disputes, correction, rewind, and recovery

| Situation | Authorized response | Forbidden response |
|---|---|---|
| Dispute before result | Pause dependent resolution and expose the committed record within the player's visibility scope | Continue rolling/applying while the dispute is unresolved |
| Invalid proposal before commitment | Reject or repair once; no cost/state | Silent reinterpretation or repeated model loop |
| Invalid commitment discovered before randomness | Visibly void it and create a new commitment after revalidation and player reconfirmation | Edit the commitment in place |
| Uncertain result delivery | Query using the same identity; apply at most one bound result | Generate another roll and choose one |
| Invalid event with a predefined exact inverse | Append a visible deterministic compensation; preserve the invalid event and linkage | Rewrite/delete history |
| Invalid event without a safe predefined inverse | Pause and propose a preserved fork from a named checkpoint | Guess a compensating value or silently rewind |
| Discretionary solo rewind | Require Rin's player's explicit consent, preserve the abandoned branch, and use fresh randomness only when the replay legitimately reaches a new roll | Infer consent, delete the old branch, or pick a preferred reroll |
| Valid unfavorable result | Explain the rule/commitment on request; keep the result | Treat disappointment as an error or grant hidden mercy |
| Narration contradicts valid state | Correct narration from the authoritative event without changing state | Change mechanics to fit prose |
| Safety Pause/Stop/Report | Follow the out-of-band safety contract; resume only by explicit player action | Treat safety control as rewind or demand a reason |

### 10.1 Correction-authority matrix

| Actor/boundary | May | Must not |
|---|---|---|
| Rin's player | Raise a dispute; request a correction or rewind; inspect the visibility-scoped commitment/history; explicitly consent to or decline a discretionary solo fork | Edit state/events directly, select a preferred correction reroll, or reveal unauthorized private fields |
| A2 model/narrator or facilitator | Flag a suspected mismatch, pause dependent narration/resolution, cite the visible record, and offer the accepted dispute control | Classify itself as state authority, append/apply compensation, alter a commitment/result, infer consent, or directly rewind/fork state |
| Authoritative validator/state boundary | Detect an accepted reason code; halt application; append/apply only a previously accepted deterministic compensation; create a proposed preserved fork record for player decision | Invent an inverse, checkpoint, result, or correction policy; erase/overwrite the invalid event; approve its own discretionary rewind |
| A1/A3 contract owners | Version the rule/state/error contract and propose exact compensation/fork semantics with replay consequences | Introduce a live inverse or checkpoint outside reviewed contract/change control |
| A0/human owner and required reviewers | Accept or reject a new correction policy/version at the applicable gate | Retroactively relabel an unfavorable valid outcome as a defect |

Automatic compensation is allowed only when a later accepted contract defines the exact inverse and proves it cannot select among outcomes. Otherwise preserve, pause, and escalate. P0-12 must encode the concrete event/error shapes; P0-13 must test every path.

The ban on a preferred **correction** reroll does not suppress an accepted feature window. Heroic Inspiration's mandatory replacement and Savage Attacker's rule-authorized candidate selection occur inside the original parent graph, retain every raw result, and are not defect correction or host mercy.

## 11. Failure taxonomy and capped recovery

| Failure source | Maximum automatic recovery | Final disposition |
|---|---|---|
| Ambiguous player intent | One neutral player clarification | Admitted lane, known `REJECT_UNSUPPORTED`, or `FALLBACK_CLARIFICATION_UNRESOLVED` without claiming unsupported authority |
| Invalid model proposal with complete authority/state | One proposal repair against the same version and visibility scope | `FALLBACK_PROPOSAL_INVALID` |
| Stale state before any bound result | One authoritative re-read; show any changed stakes and require a new parent confirmation | New validated commitment or `STOP_STATE_MISMATCH` |
| State/version mismatch after a bound result | None; preserve the result under its original stage identity and apply nothing | `STOP_STATE_MISMATCH` plus accepted correction/escalation; never rebind, reuse, or reroll |
| Missing/conflicting authority or provenance | None | `STOP_CONTRACT_DEFECT` |
| Visibility projection risk | None | `STOP_VISIBILITY_RISK` |
| Uncertain command/event delivery | Idempotent lookup/redelivery under the same identity | One event or a stop; never duplicate |
| Randomness unavailable before a result exists | No substitute roll/provider chosen by the narrator | Preserve the pending parent/child and pause at `STOP_RANDOMNESS_UNAVAILABLE` |
| Narration generation failure after valid apply | One deterministic public result template; later narration retry cannot alter state | Keep authoritative result |
| Safety control | None | `STOP_SAFETY_CONTROL` |

The “one retry” limit applies to the A2 structured proposal, not to player consent, a player choosing a different action, or an idempotent query that checks whether an already-requested authoritative result exists.

## 12. Producer and consumer implications

| Role/artifact | Produces | May consume | Must never do |
|---|---|---|---|
| A1 / P0-06 rules catalog | Versioned admitted entries, source locators, validators, exact deltas, reason codes | Accepted rules/content contract | Accept a blank/generalized entry or let narration supply rule math |
| A2 / P0-09 AI turn choreography | Typed, visibility-scoped proposal; optional rationale; one repair; typed fallback; post-result narration | Public/authorized projections and committed results | Mutate state, see over-broad private data, invent a ruling, DC, consequence, or retry loop |
| A3 / P0-10/P0-12 authority boundary | State/version binding, append-only event/correction persistence, least-privilege projections, idempotency | Validated commands/commitments | Give consumers over-broad objects, silently overwrite history, or accept model text as authority |
| A4 / client experience | Accessible pre-choice/pre-roll disclosure, confirmation, visible dice/result/correction/fallback, dispute and safety controls | Public projection only | Hide required stakes, leak private fields, or imply rejection consumed an action |
| A5 / P0-08 content | Stable content IDs, versions, provenance, visibility, prerequisites, authored predicates, reveal triggers, outcomes, recovery text | Accepted rule/content references | Use prose to create mechanics or provide unresolved/unknown content to runtime |
| A6 / P0-13 tests | Golden, negative, property/state-machine, replay, visibility, correction, injection, and fallback cases | This contract plus P0-06/P0-10/P0-12 | Treat a document example as implementation proof or lower a severity gate |
| A7 / provenance | Rules/content classifications and contamination controls | Source/content objects | Treat `AM01-R1` as SRD text or admit unknown provenance |
| A8 / P0-09 economics | One correlated full-logical-resolution ledger covering parent proposal, child/tool/random stages, the one proposal repair, fallback, cache/stream timing, latency, and cost without raw/private content | Correlation/usage metadata from A2/A3 and the stage graph here | Count a child/random stage as a separate player turn, omit retry/fallback cost, or copy private gameplay text into telemetry |
| P0-11 dice protocol | Verification/commitment recommendation and independent-check method | Logical commitment and visibility requirements here | Claim this v0.1 token language is already cryptographic proof |

Direct downstream consumers are P0-09, P0-10, P0-12, and P0-13. P0-11 is an indirect consumer through P0-10 and consumes the logical commitment/visibility requirements without changing this lane authority. P2-03 later consumes the persona invariance boundary. Any downstream contract that requires a second bounded ruling must stop and request a versioned P0-03/P0-07 authority change.

## 13. Acceptance fixtures

These fixtures define review/test obligations, not executed implementation evidence.

| ID | Case | Expected result |
|---|---|---|
| `P007-D-00` | Player withdraws a tentative action after disclosure but before parent freeze/first-roll authorization | Release any non-gameplay pending-command lock; consume nothing and create no authoritative gameplay delta |
| `P007-D-01` | `CHK-06` Acrobatics traversal at exact DC 13 | Deterministic commitment; both branches fixed before roll; state before narration |
| `P007-D-02` | Same proposal against a stale state version | Reject; re-read once; changed stakes require new confirmation; never reuse a roll |
| `P007-D-03` | Model changes DC after seeing a 12 | Reject as invariant violation; no altered event |
| `P007-D-04` | Authored no-roll willingness predicate | Commit predicate and asset delta before mutation; no random call |
| `P007-D-05` | Attack hits, then requires damage | Retain attack result; create linked damage child using the preauthored normal/critical pool before damage randomness |
| `P007-D-06` | Player invokes Heroic Inspiration after a Rin-owned die | Original and replacement retained; selection creates no gameplay delta; checkpoint atomically consumes one resource and uses the mandatory replacement even if worse |
| `P007-D-07` | Failed ability check opens Tactical Mind | Child `1d10` committed; final Second Wind delta is one use only when failure becomes success and exactly zero otherwise; attempt audit retained without spend/refund gameplay events |
| `P007-D-08` | Qualifying Savage Attacker hit | Exactly two committed candidate damage pools; both retained; selection initially non-consuming; chosen damage and once-per-turn used state apply together |
| `P007-D-09` | Qualifying critical opens Remarkable Athlete movement | Only valid 0/5/10/15-ft. no-OA states offered; no edge crossing or banked movement |
| `P007-D-10` | Rin's qualifying melee final blow | Preauthored knockout option may be selected; thrown Javelin cannot open the window; exact state/ending applied |
| `P007-D-11` | Watcher Multiattack with two legal Slams | Fully resolve/apply the first Slam checkpoint before binding the second; terminal first Slam cancels the second |
| `P007-R-01` | Legal provoking movement, Reaction available | One `AM01-R1` Slam before movement; Reaction spent; never Multiattack |
| `P007-R-02` | Multiattack proposed as OA | Reject; no roll/movement/resource mutation |
| `P007-R-03` | Disengage or forced movement | Suppress OA; Reaction remains available |
| `P007-R-04` | Reaction already spent | Suppress OA; do not improvise another reaction |
| `P007-R-05` | OA hit would reduce Rin to 0 | Apply mandatory nonlethal order; terminal; cancel pending movement/further attacks |
| `P007-R-06` | `AM01-R1` proposed for Rin | Reject unsupported request or stop defective authored content; never generalize |
| `P007-R-07` | All Watcher OA preconditions valid but proposal declines it | Reject decline and execute first legal `AM01-R1` OA under `MON-19` |
| `P007-U-01` | Mechanical Stealth/Hide request | At most one clarification; no roll/consumption/mutation; valid nearby alternatives only |
| `P007-U-02` | Torch attack/fire effect | Unsupported; do not invent attack, damage, condition, or environmental effect |
| `P007-U-03` | Effect-free quiet narration | Permit prose only; assert no fact, state, advantage, or branch change |
| `P007-U-04` | No nearby supported alternative | State that plainly; do not invent one |
| `P007-U-05` | Single clarification answer remains materially ambiguous | `FALLBACK_CLARIFICATION_UNRESOLVED`; no unsupported claim, roll, cost, or state; validated alternatives only |
| `P007-V-01` | Public current-slice check | Exact DC/defense and all non-hidden fields visible before randomness |
| `P007-V-02` | Hidden NPC concern before `CHK-02` succeeds | Private payload committed; public result type visible; payload not leaked |
| `P007-V-03` | Narrator receives result context | Only public projection delivered; private fields absent before retrieval |
| `P007-C-01` | Invalid event with predefined compensation | Original event retained; linked visible compensation appended |
| `P007-C-02` | Valid unfavorable roll disputed | Explain/inspect; no correction, mercy, or reroll |
| `P007-C-03` | Discretionary rewind requested | Named checkpoint, explicit consent, abandoned branch preserved, no preferred reroll |
| `P007-C-04` | Model/facilitator proposes directly editing or compensating state | Allow flag/pause only; reject mutation; only authoritative boundary may apply a predefined accepted correction |
| `P007-F-01` | Invalid model proposal twice | One repair only, then typed fallback with zero mutation |
| `P007-F-02` | Missing rule locator or contradictory fixed value | Contract-defect stop, not unsupported/clarify |
| `P007-F-03` | Random result response is uncertain | Query same identity; at most one bound result; never speculative reroll |
| `P007-F-04` | State/version mismatch discovered after a bound result | Preserve result/audit under original stage, apply nothing, stop/correct; never rebind, reuse, or reroll |
| `P007-F-05` | Randomness becomes unavailable after Heroic Inspiration/Savage Attacker/Tactical Mind selection but before required result | Preserve pending child and pause; resource/action/use gameplay delta remains zero until a valid checkpoint result exists |
| `P007-S-01` | Pause during proposal/roll/apply/narration | Immediate safety halt before further randomness, mutation, narration, or retry |

## 14. Skeptical review checklist

The independent desk advisory review on 2026-09-25 checked each item below. These checks record document-level verification only; they are not named-human review, P0-07 acceptance, implementation evidence, or a gate decision.

- [x] No sentence grants a generic live bounded-ruling lane.
- [x] `AM01-R1` is limited to the Watcher's one-Slam OA and remains project-authored authority.
- [x] No example admits Stealth/Hide, Torch attack, improvised damage, new route, new ending, or unlisted tactic.
- [x] Fixed DCs, stats, damage formulas, spatial mappings, and the finite outcome/stage graph cannot change after randomness; only a named accepted intervention window may select a preauthored branch.
- [x] Heroic Inspiration, Tactical Mind, Savage Attacker, Remarkable Athlete, attack→damage, and Rin's knockout option use linked child commitments and preserve every required raw result/choice.
- [x] Missing authority/state is a system stop, not blamed on the player as unsupported.
- [x] Private data is removed before downstream retrieval, not filtered after receipt.
- [x] Rejection, clarification, proposal repair, and fallback consume/mutate nothing.
- [x] No retry/correction path can create multiple selectable random results; multiple rolls or selection occur only where an accepted feature explicitly authorizes them.
- [x] A2/model/facilitator can flag and pause but cannot directly compensate, rewind, fork, or mutate state.
- [x] Corrections preserve history, scope visibility, require consent where discretionary, and never erase a valid unfavorable result.
- [x] Safety controls preempt every lane and correction path.
- [x] Examples are contract fixtures, not claims of implemented or observed behavior.
- [x] P0-04/P0-05 fieldwork remains deferred and NO-GO; G0 and production remain closed.

## 15. Review, acceptance, and change control

P0-07 remains open after this v0.1 draft. Acceptance requires, at minimum:

1. A1 review of lane admission, authority, validators, state/correction semantics, and alignment with the final P0-06 contract;
2. A2 review of proposal/fallback limits, visibility-scoped context, and non-authoritative narration;
3. A6 review that the fixture set is testable and covers negative/authority-expansion paths;
4. A0 contract-coherence review and explicit human-owner acceptance of the complete frozen P0-07 version, including but not limited to its exact-DC/hidden-fact visibility, staged intervention, correction-authority, and fallback policies; and
5. a versioned reconciliation after P0-06 incorporates required P0-05 evidence and human traceability/provenance/test review.

Advisory desk review can improve this document but cannot substitute for those acceptances. Any added ruling, changed reveal policy, altered correction authority, or expansion of the supported envelope requires a versioned amendment and downstream impact review.

### Review record

| Review | Reviewer/date | Result | Boundary |
|---|---|---|---|
| Contract/authority audit | Independent desk red-team, 2026-09-25 | PASS after repair | Advisory only; not A1/A2/A0/human acceptance |
| Structural/link validation | Desk validation, 2026-09-25 | PASS — 28 Markdown files; zero broken local links, malformed changed-file tables, or fence errors | Document integrity only |
| Required named-human review | `[OPEN]` | Not performed | Required before P0-07 completion |
