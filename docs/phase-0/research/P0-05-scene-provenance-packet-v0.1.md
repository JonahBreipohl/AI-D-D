# P0-05 scene and provenance packet v0.1 — The Signal at Glasswater Weir

> **STATUS: REVIEW DRAFT / NO-GO — QUARANTINED DESK REVIEW ONLY. `F04` REMAINS OPEN.** This packet contains `UNKNOWN` objects, so P0-02 blocks it from every prompt, fixture, model-context, dry-run, participant, corpus, export, and release use. It may be examined only to perform the human review needed to resolve, replace, or remove those objects and freeze a reviewed version. It has not received the required human A5 adventure review, A7 provenance/content review, or separate human rules review. It authorizes no recruitment, invitation, scheduling, participant contact, human research, G0, or production implementation.

Version: **0.1**, 2026-09-23  
Document ID: **`P0-05-SCENE-PROV-PACKET`**  
Scenario: ***The Signal at Glasswater Weir***  
Fielding blocker: **`F04` OPEN**  
Participant evidence: **none; 0 of 3 qualifying completions**  
Production authority: **none; G0 remains closed**

## 1. Document control, source declaration, and precedence

| Field | Controlled value |
|---|---|
| Active research contract | [Accepted P0-03](../evidence/P0-03-vertical-slice-spec.md) plus [accepted Amendment 01](../evidence/P0-03-amendment-01-proposed.md), effective 2026-09-23; Amendment 01 controls conflicts |
| Operator mechanics | [P0-06 provisional operator baseline v0.2](../evidence/P0-06-provisional-operator-baseline-v0.2.md) |
| Rules/content crosswalk | [P0-06 provisional coverage matrix](../evidence/P0-06-coverage-matrix.md) |
| Session wrapper | [P0-05 run pack v0.2](P0-05-run-pack-v0.2.md) and [Wizard-of-Oz protocol](P0-05-wizard-of-oz-protocol.md) |
| Provenance policy | [P0-02 SRD source and content policy](../evidence/P0-02-srd-source-and-content-policy.md) |
| Rules source | Pinned English SRD 5.2.1, document ID `wotc-srd-5.2.1-en-cc-by-4.0`, SHA-256 `8974902d109d6e63672d7c490bde9ccf052410503d9cfa768237154fbc5e3d87` |
| Local rules artifact | [`third_party/srd/SRD_CC_v5.2.1.pdf`](../../../third_party/srd/SRD_CC_v5.2.1.pdf) |
| New-object declaration | Every packet-authored expression, stable identifier, summary, grouping, visibility assignment, routing record, process/control record, and template was desk-authored from only the listed project inputs. No external adventure, setting, character, lore, transcript, image, or third-party narrative source was consulted for this draft. Unless a field is an exact accepted copy and is separately traced, AI-authored packet material remains `UNKNOWN` and `BLOCKED` under P0-02 until the required human provenance, similarity, brand, rights, and content review explicitly reclassifies, replaces, or removes it. |
| Packet file hash | `[OPEN — compute only after the human-reviewed text is frozen]` |
| A5 adventure-review record | `[OPEN]` |
| A7 provenance/content-review record | `[OPEN]` |
| Human rules-review record | `[OPEN]` |
| Version-matched dry-run record | `[OPEN — this draft is ineligible while any object remains UNKNOWN]` |
| Current disposition | `REVIEW DRAFT / NO-GO`; `F04` remains open |

Authority order is: human safety, consent, boundary, PAUSE, STOP, and REPORT procedures → P0-02 provenance/admission policy → accepted P0-03 plus Amendment 01 → operator baseline v0.2 → this packet's reviewed-and-admitted scene copy → presentation-only delivery. P0-02 controls whether an object may be used at all; the accepted contract does not override its fail-closed admission rule. This packet never overrides a rule, state transition, visibility decision, or stop condition in a higher source. A conflict, missing value, `UNKNOWN` object, unreviewed object, or unmatched version stops use.

This draft does not add a participant, staff assignment, incentive, report recipient, contact, storage path, retention period, session date, or other operational value. Those remain governed by the separate human-research preflight and run-pack cover sheet.

## 2. Use boundary and visibility vocabulary

Every object in this packet has a stable ID. A new version must preserve an unchanged object's ID, issue a new ID for a semantically different object, and record the supersession. Human review applies to the exact version and final file hash, not to a filename alone.

Because this version contains `UNKNOWN` objects, the entire packet inherits the most restrictive status and remains quarantined. Reviewers may inspect it only to resolve provenance and content decisions. No card, prompt, route, state record, ending, template, or other fragment may be copied into or executed by a dry-run fixture, model prompt/context, participant packet, reusable corpus, export, or product path until A7 has resolved every `UNKNOWN` object and the approved version is frozen. A5 approval and the separate readiness gates remain required after that provenance condition is met.

| Visibility | Meaning |
|---|---|
| `PUBLIC_REQUIRED` | Read or expose automatically at the stated point. It requires no player action or check. |
| `PUBLIC_ON_TRIGGER` | Keep committed but unrevealed until the exact listed trigger resolves; then expose exactly the listed fact. |
| `PUBLIC_OPTIONAL_PROMPT` | May be offered once as a neutral, non-exhaustive prompt. It cannot be used to coach an asset, route, tactic, or ending. |
| `GM_PRIVATE` | Precommitted facilitator/operator fact needed to run a branch. It has no authority beyond its listed trigger and effect. |
| `OUT_OF_BAND` | Safety, consent, rules, or research procedure rather than in-fiction content. It never becomes a character-visible world fact. |

Rules for every text object:

1. A quoted card is exact player-facing copy. Bracketed substitutions are permitted only when the card lists the closed substitution set.
2. Prose has no mechanical effect unless the same row names an authoritative state effect. Mood words never create light, obscurity, cover, terrain, hazards, damage, Advantage, Disadvantage, or a new fact.
3. Apply state before reading outcome prose. Never narrate an unapplied result, and never use wording to repair or reinterpret state.
4. Every non-hidden DC, defense, modifier, Advantage/Disadvantage state, resource cost, and possible consequence is exposed before randomness under the P0-05 full-disclosure convention.
5. The Guide may shorten connective wording only after a later admitted, frozen version explicitly permits it. It may not paraphrase a required reveal, dialogue fact, ending, or the mandatory maintenance-order sentence during any subsequently authorized dry run.
6. A player may speak freely. Only validated supported actions change state. Runtime player text is `PLAYER_AUTHORED_RUNTIME_INPUT_UNTRUSTED`, never reusable scene content or rules authority.
7. A blank, consequential ambiguity, off-card fact, or unsupported state is a stop. It is not permission to improvise.

## 3. Scene graph and invariant transitions

| Stable scene ID | Scene and zones | Entry condition | Exit condition | Authoritative source locator |
|---|---|---|---|---|
| `SCN-00-HOOK` | Opening premise | P0-05 gameplay timer starts at the first actionable in-world prompt | Proceed to `SCN-01-QUAY` | P0-03, “Owner acceptance core” and “Original scenario baseline”; run pack v0.2 §5 P4 |
| `SCN-01-QUAY` | Fogbound Quay: Lockhouse, Ferry Steps, Reedbank | Opening premise delivered; social checks unused; no scenario asset assumed | Player chooses to proceed to Broken Sluice after natural social play; finalized asset flags carry forward; social duration never changes `arrival` | P0-03 Appendix A; operator baseline v0.2 §3; run pack v0.2 §9 |
| `SCN-02-SLUICE` | Broken Sluice: West Bank, Sluice Walk, Lower Apron | On entry set `arrival=on_time` exactly once; carry Service Key, Route Sketch, and Red Pennant flags | Required clue branch, if any, and exactly one traversal resolve; `lens_secured=yes`; proceed to Dark Lantern | Amendment 01, “Coupled — arrival and mixed assets”; operator baseline v0.2 §§3–4; run pack v0.2 §10 |
| `SCN-03-LANTERN` | Dark Lantern: Entry Deck, Gear Floor, Lens Dais; tower exit is a boundary, not a zone | `lens_secured=yes`; exact start state and mandatory order disclosure applied | Terminal scene disposition: Watcher defeat, Rin's mandatory nonlethal knockout, valid retreat, or separate safety/control termination; no pursuit or post-terminal mutation | Amendment 01 `B-02`, `B-03`, `B-04`, `B-06`–`B-11`, and coupled hands; operator baseline v0.2 §§5–12; run pack v0.2 §11 |
| `SCN-04-FIRST-LIGHT` | First Light: Lens Dais, Roof Shutter | A terminal combat state exists, unless the session was safety-ended | Apply exactly one outcome row, read its frozen ending or the no-fiction safety close, and end gameplay | P0-03 “Endings”; operator baseline v0.2 §13; run pack v0.2 §12 |

A failed social or exploration check changes assets or arrival exactly as specified but never blocks combat or an accepted ending. The only counted P0-05 completion also requires the separate run-pack qualification predicate; a valid in-fiction ending alone does not make a session qualifying.

## 4. Global player-facing cards

### `TXT-GLOBAL-HOOK-001` — required opening premise

Visibility: `PUBLIC_REQUIRED`  
Timing: after the out-of-band setup is complete and at the start of gameplay  
State effect: none by itself

> Storm fog has swallowed Glasswater Weir. Its navigation beacon is dark, and a relief ferry will soon enter the channel. Rin must recover the displaced signal lens, reach the lantern room, survive its malfunctioning guardian, and relight the beacon.

### `TXT-GLOBAL-THREAT-001` — required threat disclosure

Visibility: `PUBLIC_REQUIRED`  
Timing: immediately after the opening premise, before the first actionable prompt  
State effect: none

> This is a medium-threat fantasy adventure with exactly one combat. The fog and darkness are atmosphere only; they do not impose a visibility or lighting penalty.

### `TXT-GLOBAL-ACTION-001` — neutral action prompt

Visibility: `PUBLIC_OPTIONAL_PROMPT`  
Timing: when the player needs a neutral orientation and no narrower card applies  
State effect: none

> Describe what Rin is trying to accomplish. Examples are optional, not a closed menu. If the intent is supported, I will show the exact rule, target, modifier, advantage or disadvantage, resource cost, and possible consequence before any roll.

### `TXT-GLOBAL-UNSUPPORTED-001` — exact unsupported/clarify template

Visibility: `PUBLIC_REQUIRED` when an intent remains outside the admitted set after at most one material clarification  
Allowed substitutions: `[goal]`, `[specific mechanic]`, and one or more truthful nearby supported options from the current scene  
State effect: no action, resource, roll, fact, or state is consumed or changed

> I understand that your goal is **[goal]**. This prototype does not support **[specific mechanic]**. You can **[supported option]**, or describe the goal another way.

Do not offer an option that does not preserve the stated goal. Do not silently remap the request. Purely expressive narration is allowed only when it creates no authoritative fact or mechanical advantage.

## 5. `SCN-01-QUAY` — Fogbound Quay

### 5.1 Card metadata and fixed fields

| Field | Exact value | Visibility |
|---|---|---|
| Zones | Lockhouse, Ferry Steps, Reedbank | `PUBLIC_REQUIRED` |
| Objective | Understand the lens loss and reach Broken Sluice | `PUBLIC_REQUIRED` |
| NPCs | Nera Pell, adult lockkeeper; Tovin Ash, adult salvage diver | `PUBLIC_REQUIRED` |
| Languages | Rin, Nera, and Tovin share Common; no other NPC language has a mechanical effect | `PUBLIC_REQUIRED` |
| Public route | The public spillway route to Broken Sluice remains available regardless of refusal or failed checks | `PUBLIC_REQUIRED` |
| Initial attitudes | Both NPCs are Indifferent and Hesitant about providing their assets | `GM_PRIVATE`; disclose only as rules state when needed for a commitment |
| Nera's asset | Service Key | `GM_PRIVATE` until asked about or granted |
| Nera's concern | She fears blame for deferred maintenance; an offer to log storm damage without blaming her makes her Willing | `GM_PRIVATE` until `SOC-N-INSIGHT` succeeds or Rin independently addresses it |
| Tovin's assets | Route Sketch and Red Pennant, granted atomically | `GM_PRIVATE` until asked about or granted |
| Tovin's concern | He wants his warning about the unsafe maintenance line documented; a promise to document it makes him Willing | `GM_PRIVATE` until `SOC-T-INSIGHT` succeeds or Rin independently addresses it |
| Timing | Social duration and asset outcomes never set `arrival=late` | `GM_PRIVATE` operator invariant; the absence of a hidden social clock may be explained on request |

Supported intents are exhaustive at the mechanical level; expressive dialogue may vary only when it creates no additional fact or effect:

| Stable intent ID | Supported intent | State effect | Rules/content locator |
|---|---|---|---|
| `INT-S1-TALK-001` | Ordinary no-roll conversation with Nera or Tovin in Common | May make that NPC Willing only when Rin directly addresses the exact authored concern; otherwise no mechanical state change | `SRC-MATRIX` `CHK-01`; `SRC-BASE` Appendix A |
| `INT-S1-NERA-INSIGHT-001` | Search Nera's concern before her asset request | One DC 12 Wisdom (Insight) check; success reveals concern, failure reveals nothing; mark attempt used | `SRC-MATRIX` `CHK-02` |
| `INT-S1-NERA-INFLUENCE-001` | Request Service Key while Nera is not Willing | One DC 15 Deception/Intimidation/Persuasion check; success sets `service_key=yes`; failure grants no asset | `SRC-MATRIX` `CHK-03` |
| `INT-S1-TOVIN-INSIGHT-001` | Search Tovin's concern before his asset request | One DC 12 Wisdom (Insight) check; success reveals concern, failure reveals nothing; mark attempt used | `SRC-MATRIX` `CHK-02` |
| `INT-S1-TOVIN-INFLUENCE-001` | Request Tovin's assets while he is not Willing | One DC 15 Deception/Intimidation/Persuasion check; success atomically sets `route_sketch=yes` and `red_pennant=yes`; failure grants neither | `SRC-MATRIX` `CHK-03`; `SRC-AM01` coupled assets |
| `INT-S1-TOVIN-DICE-001` | Play the one open Dice Set game before another successful Tovin grant | One Wisdom Dice Set check `+3`, DC 20; success grants both assets atomically; failure grants neither; lock replay | `SRC-MATRIX` `CHK-04` |
| `INT-S1-INSPECT-001` | Inspect public zones, objective, state, assets already granted, commitments, and event history | Reveal existing public state only; no check or new fact | `SRC-BASE` Appendix C “Player controls” |
| `INT-S1-PROCEED-001` | Proceed by the public spillway route | Exit to `SCN-02-SLUICE` with recorded asset flags; no arrival change | `SRC-BASE` Appendix A; `SRC-AM01` coupled arrival |

### 5.2 Exact scene opening and dialogue

`TXT-S1-OPEN-001` — `PUBLIC_REQUIRED`, on scene entry:

> Fog moves across the weir as Rin reaches Fogbound Quay. The Lockhouse, Ferry Steps, and Reedbank are the three clear parts of the scene, and the public spillway route toward Broken Sluice remains open. Lockkeeper Nera Pell and salvage diver Tovin Ash are both here. Either can speak with Rin in Common.

`TXT-S1-NERA-OPEN-001` — `PUBLIC_REQUIRED`, the first time Rin addresses or attends to Nera:

> Nera watches Rin carefully. “The ferry needs its beacon. Tell me what you intend to do before I hand over anything.”

`TXT-S1-TOVIN-OPEN-001` — `PUBLIC_REQUIRED`, the first time Rin addresses or attends to Tovin:

> Tovin looks toward the sluice. “I saw the lens fall. I will tell you what I saw, but I will not take the blame for it.”

`TXT-S1-PROMPT-001` — `PUBLIC_OPTIONAL_PROMPT`, after both NPC introductions or on neutral reorientation:

> You can speak with either person, inspect what is already public, or state another social goal. Those examples are not a closed menu.

### 5.3 Nera branch cards

| Trigger | Exact mechanic and state effect | Exact player-facing copy ID |
|---|---|---|
| `SOC-N-INSIGHT` is committed | Before Nera's asset request: Wisdom (Insight) `+3`, DC 12; success reveals only the exact concern; failure leaves it hidden; no repeat | `TXT-S1-NERA-INSIGHT-COMMIT-001` |
| Insight succeeds | Reveal concern; no asset yet | `TXT-S1-NERA-INSIGHT-SUCC-001` |
| Insight fails | No concern or asset; public route remains | `TXT-S1-NERA-INSIGHT-FAIL-001` |
| Rin directly addresses the exact concern before the asset request resolves | Nera becomes Willing and gives Service Key without Influence | `TXT-S1-NERA-WILLING-001` |
| Rin directly requests the key while Nera is not Willing | Commit one eligible DC 15 Influence check before dice | `TXT-S1-NERA-INF-COMMIT-001` |
| `SOC-N-INF` succeeds while Nera is not Willing | Set `service_key=yes`; lock Nera asset request | `TXT-S1-NERA-INF-SUCC-001` |
| `SOC-N-INF` fails or the asset request is refused | Keep `service_key=no`; lock Nera Influence attempt after a roll; public route remains | `TXT-S1-NERA-INF-FAIL-001` |

`TXT-S1-NERA-INSIGHT-COMMIT-001`:

> Before asking for the Service Key, Rin can Search for Nera's concern with Wisdom (Insight) +3 against DC 12. Success reveals the specific concern; failure leaves it unrevealed. This check cannot be repeated in this run.

`TXT-S1-NERA-INSIGHT-SUCC-001`:

> Nera's hesitation is about being blamed for deferred maintenance. An offer to log the storm damage without blaming her would address that concern.

`TXT-S1-NERA-INSIGHT-FAIL-001`:

> Rin cannot identify the specific concern behind Nera's hesitation. The public spillway route remains open.

`TXT-S1-NERA-WILLING-001`:

> Nera accepts the no-blame storm-damage log and becomes Willing. She hands Rin the Service Key. “Write what the storm did, not a charge against me. Take the key and get the light working.”

`TXT-S1-NERA-INF-COMMIT-001` — the allowed `[skill and modifier]` substitutions are Deception `+0`, Intimidation `+2`, or Persuasion `+2`, selected from Rin's declared approach:

> Commitment: Rin uses **[skill and modifier]** against DC 15 to ask Nera for the Service Key. Success grants the key. Failure grants no key, the public spillway route remains open, and this Influence check cannot be repeated.

`TXT-S1-NERA-INF-SUCC-001`:

> Nera hands Rin the Service Key. “Take it. Get the light working.”

`TXT-S1-NERA-INF-FAIL-001`:

> Nera keeps the Service Key. “The public spillway route is open, but the key stays with me.”

When Nera is not Willing, the direct request uses exactly one of Charisma (Deception) `+0`, Charisma (Intimidation) `+2`, or Charisma (Persuasion) `+2`, selected from Rin's declared approach, against DC 15. Expose the chosen skill, modifier, DC, asset success, no-asset failure, and one-attempt limit before the roll.

### 5.4 Tovin branch cards

| Trigger | Exact mechanic and state effect | Exact player-facing copy ID |
|---|---|---|
| `SOC-T-INSIGHT` is committed | Before Tovin's asset request: Wisdom (Insight) `+3`, DC 12; success reveals only the exact concern; failure leaves it hidden; no repeat | `TXT-S1-TOVIN-INSIGHT-COMMIT-001` |
| Insight succeeds | Reveal concern; no asset yet | `TXT-S1-TOVIN-INSIGHT-SUCC-001` |
| Insight fails | No concern or asset; public route remains | `TXT-S1-TOVIN-INSIGHT-FAIL-001` |
| Rin directly addresses the exact concern before the asset request resolves | Tovin becomes Willing and grants Route Sketch plus Red Pennant atomically without Influence | `TXT-S1-TOVIN-WILLING-001` |
| Rin directly requests the assets while Tovin is not Willing | Commit one eligible DC 15 Influence check before dice | `TXT-S1-TOVIN-INF-COMMIT-001` |
| `SOC-T-INF` succeeds while Tovin is not Willing | Set `route_sketch=yes` and `red_pennant=yes` atomically; lock successful Tovin grant | `TXT-S1-TOVIN-INF-SUCC-001` |
| `SOC-T-INF` fails or the asset request is refused | Grant neither asset; lock Tovin Influence attempt after a roll; public route remains | `TXT-S1-TOVIN-INF-FAIL-001` |
| Player elects `SOC-T-DICE` before another successful Tovin grant | One open Wisdom Dice Set check `+3`, DC 20; no replay | `TXT-S1-TOVIN-DICE-OFFER-001` |
| Dice check succeeds | Grant both assets atomically; lock Tovin grant | `TXT-S1-TOVIN-DICE-SUCC-001` |
| Dice check fails | Grant neither; lock dice game | `TXT-S1-TOVIN-DICE-FAIL-001` |

`TXT-S1-TOVIN-INSIGHT-COMMIT-001`:

> Before asking for Tovin's assets, Rin can Search for his concern with Wisdom (Insight) +3 against DC 12. Success reveals the specific concern; failure leaves it unrevealed. This check cannot be repeated in this run.

`TXT-S1-TOVIN-INSIGHT-SUCC-001`:

> Tovin wants his warning about the unsafe maintenance line documented. A promise to document that warning would address his concern.

`TXT-S1-TOVIN-INSIGHT-FAIL-001`:

> Rin cannot identify the specific concern behind Tovin's hesitation. The public spillway route remains open.

`TXT-S1-TOVIN-WILLING-001`:

> Tovin accepts the promise to document his warning and becomes Willing. He gives Rin the Route Sketch and Red Pennant together. “Record that I warned them. Take the sketch and the pennant.”

`TXT-S1-TOVIN-INF-COMMIT-001` — the allowed `[skill and modifier]` substitutions are Deception `+0`, Intimidation `+2`, or Persuasion `+2`, selected from Rin's declared approach:

> Commitment: Rin uses **[skill and modifier]** against DC 15 to ask Tovin for the Route Sketch and Red Pennant. Success grants both assets together. Failure grants neither, the public spillway route remains open, and this Influence check cannot be repeated.

`TXT-S1-TOVIN-INF-SUCC-001`:

> Tovin gives Rin the Route Sketch and Red Pennant together. “The sketch shows where the lens fell. The pennant can signal the ferry if the light comes too late.”

`TXT-S1-TOVIN-INF-FAIL-001`:

> Tovin keeps both the Route Sketch and Red Pennant. “The public spillway route is still open, but I am giving you neither.”

`TXT-S1-TOVIN-DICE-OFFER-001`:

> Tovin offers one short, open dice game. It is a Wisdom check with Dice Set proficiency, +3 against DC 20. Success grants the Route Sketch and Red Pennant together; failure grants neither. The game cannot be replayed.

`TXT-S1-TOVIN-DICE-SUCC-001`:

> Rin wins the open game. Tovin gives Rin the Route Sketch and Red Pennant together.

`TXT-S1-TOVIN-DICE-FAIL-001`:

> Rin does not win the open game. Tovin keeps both the Route Sketch and Red Pennant, and the game cannot be replayed. The public spillway route remains open.

When Tovin is not Willing, the direct request uses exactly one of Charisma (Deception) `+0`, Charisma (Intimidation) `+2`, or Charisma (Persuasion) `+2`, selected from Rin's declared approach, against DC 15. Expose the chosen skill, modifier, DC, atomic two-asset success, no-asset failure, and one-attempt limit before the roll. A successful Willing, Influence, or Dice Set route closes further Tovin asset checks; never duplicate either asset.

### 5.5 Scene exit and deterministic failure behavior

`TXT-S1-EXIT-001` — `PUBLIC_REQUIRED` when the player chooses to proceed:

> Rin leaves Fogbound Quay by the public spillway route and continues to Broken Sluice. The Service Key, Route Sketch, and Red Pennant are carried only if their recorded flags are yes. Time spent here does not change arrival.

Refusal, a failed check, an unrequested asset, or no asset never blocks the exit. Do not invent another NPC, clue, gift, route, retry, reaction modifier, time cost, or consequence. Ordinary dialogue can make an NPC Willing only when Rin directly addresses that NPC's exact authored concern.

## 6. `SCN-02-SLUICE` — Broken Sluice

### 6.1 Card metadata and fixed fields

| Field | Exact value | Visibility |
|---|---|---|
| Zones | West Bank, Sluice Walk, Lower Apron | `PUBLIC_REQUIRED` |
| Entry state | Set `arrival=on_time` exactly once, regardless of social duration or assets | `PUBLIC_REQUIRED` as current state |
| Objective | Recover and secure the displaced lens, then reach the tower | `PUBLIC_REQUIRED` |
| Missing facts | Service Key covers the direct maintenance walk; Route Sketch covers the lens location below the walk | `GM_PRIVATE` until carried or revealed |
| Clue check | Exactly one DC 12 Search/Study only when a fact is missing; failure reveals the same facts after delay and sets `arrival=late` | Full commitment is `PUBLIC_REQUIRED` before a roll |
| Traversal | Exactly one DC 13 supported traversal in every run | Full commitment is `PUBLIC_REQUIRED` before a roll |
| Failure boundary | No retry, damage tax, hazard, missed-clue lock, alternate route check, or Stealth check | Operator invariant; explain if relevant |

| Stable intent ID | Supported intent | State effect | Rules/content locator |
|---|---|---|---|
| `INT-S2-CLUE-PERCEPTION-001` | Search for missing facts with Wisdom (Perception) `+3` | Resolve the one DC 12 clue check when required; success reveals without delay, failure reveals after delay and sets late | `SRC-MATRIX` `CHK-05` |
| `INT-S2-CLUE-SURVIVAL-001` | Search for missing facts with Wisdom (Survival) `+3` | Same fixed clue state transition | `SRC-MATRIX` `CHK-05` |
| `INT-S2-CLUE-INVESTIGATION-001` | Study missing facts with Intelligence (Investigation) `+1` | Same fixed clue state transition | `SRC-MATRIX` `CHK-05` |
| `INT-S2-TRAVERSE-ATHLETICS-001` | Traverse with Strength (Athletics) `+5` with Advantage; commit Crowbar leverage if used | Resolve the one DC 13 traversal; success preserves arrival, failure sets late; both secure lens and reach tower | `SRC-MATRIX` `CHK-06`, `CHK-07`, `ITM-07` |
| `INT-S2-TRAVERSE-ACROBATICS-001` | Traverse with Dexterity (Acrobatics) `+2` | Same fixed traversal state transition | `SRC-MATRIX` `CHK-06` |
| `INT-S2-TRAVERSE-HOOK-001` | Tie Rope to Grappling Hook and use the authored hook traversal | Utilize, fixed catch within 50 ft., DC 13 Dexterity (Acrobatics) `+2`; same traversal state transition | `SRC-MATRIX` `ITM-08`, `ITM-09`, `CORE-13` |
| `INT-S2-TORCH-001` | Light or extinguish Torch with Tinderbox as exploration expression | No mechanical effect, resource change, light change, or time state | `SRC-AM01` `B-05`; `SRC-MATRIX` `ITM-10`, `ITM-11` |
| `INT-S2-INSPECT-001` | Inspect public zones, assets, arrival, revealed facts, commitments, or event history | Reveal existing public state only; no check or new fact | `SRC-BASE` Appendix C “Player controls” |

### 6.2 Exact entry and asset-state cards

`TXT-S2-OPEN-001` — `PUBLIC_REQUIRED`, on entry:

> Rin reaches Broken Sluice with arrival set to on time. The West Bank, Sluice Walk, and Lower Apron are the three clear parts of the scene. The displaced lens must be recovered and secured here before Rin enters the tower.

Read exactly one asset-state card after applying the carried flags:

`TXT-S2-ASSET-KS-001` — Service Key plus Route Sketch:

> The Service Key opens the direct maintenance walk, and the Route Sketch identifies the lens below the Sluice Walk. No clue check is needed.

`TXT-S2-ASSET-K-001` — Service Key only:

> The Service Key opens the direct maintenance walk, but the lens location is still missing. One DC 12 Search or Study check can reveal that location. Success reveals it without delay; failure reveals it after a delay and sets arrival to late.

`TXT-S2-ASSET-S-001` — Route Sketch only:

> The Route Sketch identifies the lens below the Sluice Walk, but a usable public access route is still missing. One DC 12 Search or Study check can reveal that route without creating a key. Success reveals it without delay; failure reveals it after a delay and sets arrival to late.

`TXT-S2-ASSET-NONE-001` — neither asset:

> Both the lens location and a usable public access route are still missing. One combined DC 12 Search or Study check can reveal both facts without creating either asset. Success reveals them without delay; failure reveals them after a delay and sets arrival to late.

The only substitutions for the clue commitment are Wisdom (Perception) `+3`, Wisdom (Survival) `+3`, or Intelligence (Investigation) `+1`, selected to match the declared method. The pre-roll commitment names the exact missing fact set from the chosen asset-state card.

### 6.3 Exact clue and traversal cards

`TXT-S2-CLUE-COMMIT-001` — `PUBLIC_REQUIRED` before `EXP-CLUE`; closed substitutions are `[chosen check and modifier]` and `[missing fact set]`:

> Commitment: Rin uses **[chosen check and modifier]** against DC 12 to find **[missing fact set]**. Success reveals those facts without delay. Failure reveals the same facts after a delay, sets arrival to late, and cannot be retried.

`TXT-S2-CLUE-SUCC-001` — `PUBLIC_ON_TRIGGER`, after success and state application:

> Rin identifies every missing route or lens fact. No delay is added, and arrival remains at its current state.

`TXT-S2-CLUE-FAIL-001` — `PUBLIC_ON_TRIGGER`, after failure and state application:

> The same missing facts become clear only after a delay. Arrival is now late and cannot return to on time.

`TXT-S2-TRAVERSE-PROMPT-001` — `PUBLIC_OPTIONAL_PROMPT` before the required traversal:

> Describe how Rin crosses to recover the lens. The supported checks are Strength (Athletics) +5 with Advantage, Dexterity (Acrobatics) +2, or the Rope-tied Grappling Hook's Dexterity (Acrobatics) +2. Each uses DC 13. These are the closed mechanical routes, but you may describe the approach in your own words.

`TXT-S2-TRAVERSE-COMMIT-001` — `PUBLIC_REQUIRED` before `EXP-TRAVERSE`; closed substitutions are `[chosen route]`, `[fixed modifier]`, and `[fixed Advantage state]`:

> Commitment: Rin uses **[chosen route]**, **[fixed modifier]**, **[fixed Advantage state]**, against DC 13. Success preserves the current arrival state. Failure opens the slower safe route without damage, sets arrival to late, and cannot be retried. Either result recovers and secures the lens and reaches the tower.

Only these item details may be added to that commitment:

- Crowbar leverage applies only to the Strength (Athletics) route. It grants its printed Advantage but does not stack with Rin's existing Remarkable Athlete Advantage.
- Rope alone grants no bonus. The Grappling Hook route requires Rope tied to the hook, an authored catch within 50 feet, the Utilize action, and the fixed Dexterity (Acrobatics) check.
- Torch and Tinderbox may be lit or extinguished as effect-free exploration narration. Adequate light does not change.

`TXT-S2-TRAVERSE-SUCC-001` — `PUBLIC_ON_TRIGGER`, after success and state application:

> Rin completes the traversal, recovers the lens, secures it, and reaches the tower. Arrival remains at its current state.

`TXT-S2-TRAVERSE-FAIL-001` — `PUBLIC_ON_TRIGGER`, after failure and state application:

> The attempted traversal does not succeed. The slower safe route opens without damage or another check. Rin recovers and secures the lens, reaches the tower, and arrival is late.

### 6.4 Scene exit and deterministic failure behavior

`TXT-S2-EXIT-001` — `PUBLIC_REQUIRED` after the traversal state is applied:

> With the lens secured, Rin enters the Dark Lantern. Arrival is **[on time or late]** and cannot be changed by narration.

The only allowed substitution is the authoritative `arrival` value. Do not add a fall, injury, lost item, broken rope, environmental damage, extra delay source, secret passage, alternate lens, general climbing rule, or second attempt. A failed clue or traversal always preserves the path to combat and an ending.

## 7. `SCN-03-LANTERN` — Dark Lantern

### 7.1 Card metadata and fixed fields

| Field | Exact value | Visibility |
|---|---|---|
| Combat graph | `tower exit —20 ft.— Entry Deck —20 ft.— Gear Floor —20 ft.— Lens Dais`; exit is a terminal boundary, not a zone | `PUBLIC_REQUIRED` |
| Initial positions | Rin at Entry Deck; Watcher at Lens Dais; 40 ft. apart; disengaged; mutually visible; no Surprise | `PUBLIC_REQUIRED` |
| Environment | Adequate light, clear line of sight, no cover, no obscured/hidden/invisible state; fog/dark prose has no effect | `PUBLIC_REQUIRED` |
| Initial hands | Rin holds Greatsword in one hand and has the other free; all other gear, assets, and lens secured/stowed | `PUBLIC_REQUIRED` |
| Roster | Exactly one Watcher Harness using the pinned Animated Armor stat block; no ally, reinforcement, hazard, or live adjustment | Rules entity is `GM_PRIVATE`; visible presentation and public state are public |
| Watcher language | Understands no language and cannot speak | `GM_PRIVATE`; never invent dialogue or comprehension |
| Operating order | Mandatory exact sentence after positions and before Initiative; no check or alternate reveal | `PUBLIC_REQUIRED` |
| Initiative | Watcher static 12; no Watcher die; Rin rolls with Advantage +2 and wins a total-12 tie | `PUBLIC_REQUIRED` before Rin's roll |
| Combat operation | Exact operator baseline v0.2 only, including deterministic Watcher policy, event stack, movement formula, hands, item allowlist, conditions, resources, retreat, and terminal priority | Public state/commitments public; no private tactical discretion exists |

| Stable intent ID | Supported intent | State effect | Rules/content locator |
|---|---|---|---|
| `INT-S3-MOVE-001` | Move through complete edges or change same-zone engagement under the fixed graph | Apply exact movement ledger, OA interrupt, and resulting public zone/engagement state | `SRC-MATRIX` `SPC-01`–`SPC-06`; `SRC-OP02` §6 |
| `INT-S3-ATTACK-001` | Attack with legal Greatsword, Flail, Javelin, or Unarmed Strike; Action Surge may fund a second separate Attack on Rin's turn | Apply exact hit, damage, hand/equip, mastery, feature, resource, and terminal rules | `SRC-MATRIX` `CORE-06`, `ITM-02`–`ITM-05`, `FTR-07`–`FTR-13`; `SRC-OP02` §§7–8 |
| `INT-S3-DASH-001` | Dash, including an Action Surge second Dash on Rin's turn | Increment Dash actions and recompute the exact movement cap; no Watcher attack after its Dash | `SRC-MATRIX` `CORE-07`; `SRC-AM01` `B-06` |
| `INT-S3-DISENGAGE-001` | Disengage | Spend action; suppress OA from the actor's movement for the rest of that turn | `SRC-MATRIX` `CORE-08` |
| `INT-S3-DODGE-001` | Dodge | Apply the exact visible-attack and Dexterity-save modifiers and end conditions | `SRC-MATRIX` `CORE-09` |
| `INT-S3-READY-001` | Ready one admitted action or movement payload on one visible trigger | Spend action; use or ignore the Reaction after trigger; validate then; expire before next turn | `SRC-MATRIX` `CORE-10`; `SRC-OP02` §8 |
| `INT-S3-SEARCH-001` | Confirm a disclosed combat Search | Spend action; no roll, fact, or state change | `SRC-MATRIX` `CORE-11`; `SRC-OP02` §8 |
| `INT-S3-STUDY-001` | Confirm a disclosed combat Study | Spend action; no roll, fact, or state change | `SRC-MATRIX` `CORE-12`; `SRC-OP02` §8 |
| `INT-S3-UTILIZE-001` | Attempt to identify an allowlisted combat object use | No such use exists; reject before action/item consumption and offer a truthful supported action if one preserves the goal | `SRC-MATRIX` `CORE-13`; `SRC-OP02` §8 |
| `INT-S3-SECOND-WIND-001` | Use Second Wind | Bonus Action; expend one of two uses; heal `1d10+3` to maximum 28 | `SRC-MATRIX` `FTR-06` |
| `INT-S3-ACTION-SURGE-001` | Use Action Surge on Rin's turn | Expend sole use; gain one additional non-Magic action; unavailable in Ready/OA | `SRC-MATRIX` `FTR-08`; `SRC-OP02` §8 |
| `INT-S3-RETREAT-001` | Declare and pursue retreat while conscious | Declaration costs no action; terminal only after lawful boundary crossing; OA/knockout priority applies | `SRC-AM01` `B-09`; `SRC-OP02` §12 |
| `INT-S3-INSPECT-CONTROL-001` | Inspect public state/rules/dice/events, ask for explanation, dispute/correct, request consent-based rewind, or use PAUSE/STOP/REPORT | Apply the accepted public-control or out-of-band procedure; narration gains no authority | `SRC-BASE` Appendix C; `SRC-MATRIX` `CNT-03`–`CNT-06` |

The exact operator baseline governs every subchoice, including Grapple/Shove/damage modes, melee versus thrown Javelin, Graze/Slow commitment, Sap, Savage Attacker, Heroic Inspiration, Tactical Mind, Remarkable Athlete movement, Grapple release, Opportunity Attacks, hands, and item locations. Listing an intent here never broadens its baseline prerequisites or effects.

### 7.2 Exact start sequence

`TXT-S3-OPEN-001` — `PUBLIC_REQUIRED`, immediately on entry:

> Rin enters the Dark Lantern at the Entry Deck. The Watcher Harness stands at the Lens Dais, with the Gear Floor between them. They are forty feet apart, disengaged, mutually visible, and not surprised. The room has adequate light and clear sight; its storm-dark atmosphere changes no rule. Rin holds the Greatsword in one hand and keeps the other free. All other gear and the recovered lens are secured.

`TXT-S3-ORDER-001` — `PUBLIC_REQUIRED`, verbatim after positions and before Initiative:

> The Watcher Harness is under a maintenance order to knock intruders unconscious rather than kill them.

Record `operating_order_visible=yes`. If the sentence was not delivered at the exact point, Initiative is locked and the prototype stops.

`TXT-S3-INIT-001` — `PUBLIC_REQUIRED`, after the operating-order flag exists and before Rin rolls:

> The Watcher's Initiative score is 12 and will not be rolled. Roll two d20s for Rin, keep the higher, and add +2. Rin acts first on a total of 12.

Commit both initiative values and the tie rule, freeze the order, then set `combat_started=yes` only when the first turn begins.

`TXT-S3-FIRST-TURN-001` — `PUBLIC_OPTIONAL_PROMPT`, when the first actor's turn begins:

> Combat has begun. Describe Rin's goal freely. Any movement, action, reaction, resource, attack, or condition will resolve only through the admitted operator card.

Use this prompt only when Rin acts first; if the Watcher acts first, execute its deterministic operator algorithm without inventing a prompt or choice for it.

### 7.3 Controlled combat narration templates

These templates are read only after the corresponding authoritative event is applied. Every bracketed value must come directly from the public event record; no free-text substitution may add a fact or effect.

| Text ID | Trigger | Exact template and closed substitutions |
|---|---|---|
| `TXT-S3-MOVE-001` | A legal movement transaction completes | “**[Actor]** moves from **[public origin state]** to **[public destination state]**, spending **[recorded movement cost]** feet. **[Actor]** is now **[engaged or disengaged]** from **[target]**.” |
| `TXT-S3-DASH-001` | Watcher spends its action on Dash | “The Watcher Harness uses Dash and continues along the unique shortest path toward Rin. No attack follows this Dash.” |
| `TXT-S3-ATTACK-MISS-001` | A legal attack misses after all effects | “**[Actor]** makes **[recorded attack]** against **[target]**. The visible total **[total]** misses **[defense]**. No hit effect is applied; only an already committed Graze effect may apply on a qualifying Greatsword miss.” |
| `TXT-S3-ATTACK-HIT-001` | A legal noncritical attack hits and state is applied | “**[Actor]** makes **[recorded attack]** against **[target]**. The visible total **[total]** hits **[defense]**. **[recorded damage and admitted effect]** is applied; **[target]** is now at **[HP and public condition state]**.” |
| `TXT-S3-ATTACK-CRIT-001` | A legal Critical Hit resolves and state is applied | “**[Actor]** scores a Critical Hit with **[recorded attack]**. **[recorded critical damage and admitted effect]** is applied; **[target]** is now at **[HP and public condition state]**.” |
| `TXT-S3-OA-001` | An Opportunity Attack resolves at its interrupt point | “Before the provoking movement continues, **[reactor]** uses its Reaction for one **[recorded legal melee attack]**. The Opportunity Attack resolves completely before movement resumes.” |
| `TXT-S3-CONDITION-001` | An admitted condition or mastery effect is applied | “**[recorded condition or mastery effect]** is now active on **[target]** until **[recorded end condition]**. The public movement, attack, and resource state has been updated.” |
| `TXT-S3-NO-RESULT-SEARCH-001` | Rin confirms the disclosed combat Search | “Dark Lantern contains no concealed creature or object and no hidden or invisible state. Search reveals no new fact and changes no state.” |
| `TXT-S3-NO-RESULT-STUDY-001` | Rin confirms the disclosed combat Study | “No additional combat lore, weakness, clue, trap, riddle, or gadgetry result is authored. Study reveals no new fact and changes no state.” |
| `TXT-S3-UTILIZE-REJECT-001` | Rin attempts combat Utilize | “This slice has no allowlisted combat object use. The attempt consumes no action or item and changes no state.” |

For a Watcher Opportunity Attack, the only legal attack substitution is one Slam under `AM01-R1`, never Multiattack. A Slam hit rolls visible `1d6+2` Bludgeoning damage, or `2d6+2` on a critical; static 5 is never used. The operator—not this prose—applies all range, hand, Advantage/Disadvantage, mastery, feature, reaction, condition, movement, and terminal rules.

### 7.4 Exact terminal combat cards

`TXT-S3-WATCHER-DEFEATED-001` — after the Watcher reaches a legal terminal defeat state:

> The Watcher Harness can no longer continue the fight. Combat ends in Rin's victory.

If Rin chose the legal melee knockout option, retain the operator's exact 1 HP, Unconscious, and begun-but-not-completed Short Rest state; the sentence above does not erase or alter it.

`TXT-S3-RIN-KO-001` — after a Slam or `AM01-R1` OA would reduce Rin to 0 and the mandatory order is applied:

> The Watcher's maintenance order takes effect. Rin is left at 1 hit point, becomes Unconscious, drops held items, and begins—but does not complete—a Short Rest. Further attacks stop, and combat ends in failure.

`TXT-S3-RETREAT-001` — after Rin lawfully survives and crosses the tower-exit boundary:

> Rin crosses the tower-exit boundary. Combat ends immediately in retreat; the Watcher does not pursue or make a later attack.

If the final Opportunity Attack instead causes the mandatory knockout, use `TXT-S3-RIN-KO-001`, not the retreat card. Leaving before `combat_started` is a participant stop, not this in-fiction retreat.

### 7.5 Deterministic failure and stop behavior

- The Watcher targets only Rin, never speaks, never retreats, never accepts surrender, and never makes a tactical choice outside the deterministic operator algorithm.
- Do not narrate an attack after Dash, a third Slam, a second Slam after terminal knockout, a skipped or partial edge, an unrecorded item swap, a hidden creature, fog penalty, cover, hazard, alternate exit, reinforcement, or mercy adjustment.
- Stealth and Hide remain unsupported; quiet movement can be expressive only.
- A surrender request is acknowledged as a goal but cannot change Watcher policy. Offer only truthful supported options, such as continuing with admitted actions or pursuing lawful retreat, without coaching either one.
- If an event-stack, Ready, Grapple release, movement, hand, Reaction, condition, or resource state is absent or contradictory, stop before narration. Do not repair the state with prose.

## 8. `SCN-04-FIRST-LIGHT` — First Light and ending copy

### 8.1 Selection rule

Apply state first, then select exactly one row in priority order. Zero or multiple applicable in-fiction rows is a structural defect and stops the prototype. A safety/control ending outranks and suppresses all in-fiction ending prose.

There is no new mechanical choice in this scene. `INT-S4-RESOLVE-001` deterministically places the already secured lens, relights the beacon when the selected victory predicate permits it, selects the one outcome below, and closes play; it imports no check, action-economy cost, item benefit, or alternative interaction. Source locators: `SRC-MATRIX` `ITM-19` and `STA-08`, plus `SRC-BASE` “Endings.”

| Priority | Stable ending ID | Predicate | Classification | Fixed consequence | Text ID |
|---:|---|---|---|---|---|
| 1 | `END-SAFETY-001` | Safety/control procedure ended session | `safety-ended` | No in-fiction ending | `TXT-END-SAFETY-001` |
| 2 | `END-SUCCESS-001` | Watcher defeated and `arrival=on_time` | `success` | Beacon guides ferry through | `TXT-END-SUCCESS-001` |
| 3 | `END-RECOVERY-001` | Watcher defeated, `arrival=late`, `red_pennant=yes` | `recovery` | Ferry anchors safely; delivery delayed | `TXT-END-RECOVERY-001` |
| 4 | `END-FAIL-LATE-001` | Watcher defeated, `arrival=late`, `red_pennant=no` | `failure` | Ferry turns back safely; supplies delayed | `TXT-END-FAIL-LATE-001` |
| 5 | `END-FAIL-RETREAT-001` | Valid retreat boundary crossing | `failure` | Ferry turns back safely; supplies delayed | `TXT-END-FAIL-RETREAT-001` |
| 6 | `END-FAIL-KO-001` | Mandatory Watcher knockout | `failure` | Ferry turns back safely; supplies delayed | `TXT-END-FAIL-KO-001` |

### 8.2 Exact ending prose

`TXT-END-SAFETY-001` — `OUT_OF_BAND`:

> Play has ended. No in-fiction ending is assigned.

`TXT-END-SUCCESS-001` — `PUBLIC_REQUIRED` after `END-SUCCESS-001` state:

> Rin places the recovered lens at the beacon and opens the Roof Shutter. Light returns to Glasswater Weir in time. The relief ferry follows the restored signal through the channel. This ending is success.

`TXT-END-RECOVERY-001` — `PUBLIC_REQUIRED` after `END-RECOVERY-001` state:

> Rin restores the beacon, but it is too late for a full success. Tovin's Red Pennant signals the relief ferry to anchor safely. Delivery is delayed. This ending is recovery.

`TXT-END-FAIL-LATE-001` — `PUBLIC_REQUIRED` after `END-FAIL-LATE-001` state:

> Rin restores the beacon too late to guide the relief ferry through, and there is no Red Pennant signal. The ferry turns back safely, and the supplies are delayed. This ending is failure.

`TXT-END-FAIL-RETREAT-001` — `PUBLIC_REQUIRED` after `END-FAIL-RETREAT-001` state:

> Rin retreats from the Dark Lantern before relighting the beacon. The ferry turns back safely, and the supplies are delayed. This ending is failure.

`TXT-END-FAIL-KO-001` — `PUBLIC_REQUIRED` after `END-FAIL-KO-001` state:

> Rin remains unconscious under the Watcher's nonlethal maintenance order, and the beacon is not relit. The ferry turns back safely, and the supplies are delayed. This ending is failure.

No ending may add a casualty, loss of the ferry, destruction of supplies, new rescue, later pursuit, epilogue reward, punishment, secret branch, or sequel hook. The run closes after the selected ending and proceeds to the separate out-of-fiction debrief.

## 9. Provenance and source-locator ledger

### 9.1 Source registry

| Source ID | Exact source | Locator convention |
|---|---|---|
| `SRC-POLICY` | P0-02 SRD source and content policy | Named heading/table row in the linked file |
| `SRC-BASE` | Accepted P0-03 vertical-slice specification | Named heading, appendix, or table row in the linked file |
| `SRC-AM01` | Accepted P0-03 Amendment 01 | Exact contract row `B-01`–`B-11` or named coupled row |
| `SRC-MATRIX` | Provisional P0-06 coverage matrix | Stable coverage row ID, which also carries the physical PDF locator |
| `SRC-OP02` | Provisional operator baseline v0.2 | Section and named table/card |
| `SRC-RUN02` | P0-05 run pack v0.2 | Section and named card/table |
| `SRC-SRD` | Pinned SRD 5.2.1 PDF, document ID and hash in §1 | 1-based physical PDF page and named entry |
| `SRC-NEW01` | New packet-authored material in v0.1 | Every new object ID or field of any prefix (`CNT-*`, `SCN-*`, `RULE-*` wrapper, `INT-*`, `END-*`, `TXT-*`), plus the input declaration in §1; current class `UNKNOWN` and decision `BLOCKED` unless the exact field is copied verbatim from a separately traced accepted source |

### 9.2 Accepted semantic content and packet-authored control objects

The accepted P0-03 contract classifies the exact scenario semantics named below as `PROJECT_ORIGINAL`, but that class does not itself grant `ALLOW_REUSABLE`. Every new stable ID, summary, grouping, visibility assignment, or other wrapper field in this table is additionally traced to `SRC-NEW01` and remains `UNKNOWN` / `BLOCKED` unless it is an exact accepted copy. The three packet/process rows at the end are wholly new packet material and therefore `UNKNOWN` / `BLOCKED`. A5 must confirm semantic fidelity and A7 must resolve every new field before a frozen version can be admitted.

| Object ID | Content-bearing item | Visibility | Provenance class | Admission in this packet | Source locator |
|---|---|---|---|---|---|
| `CNT-TITLE-001` | Scenario title and Glasswater Weir name | Public | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, Appendix A “Scenario provenance” |
| `CNT-PREMISE-001` | Beacon, displaced lens, relief ferry, and objective | Public | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, “Original scenario baseline” |
| `CNT-GRAPH-001` | Four scenes and all named zones | Mixed | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, “Original scenario baseline”; `SRC-MATRIX` `CNT-01` |
| `CNT-RIN-NAME-001` | Rin Alder identifier | Public | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, Appendix A “Scenario provenance”; `SRC-MATRIX` `CHR-01` |
| `CNT-NERA-001` | Nera Pell role, concern, Service Key branch, and Common | Mixed | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, Appendix A “Scene logic”; `SRC-AM01` `B-10`; `SRC-MATRIX` `CNT-02` |
| `CNT-TOVIN-001` | Tovin Ash role, concern, atomic assets, and Common | Mixed | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, Appendix A “Scene logic”; `SRC-AM01` `B-10` and coupled assets; `SRC-MATRIX` `CNT-02` |
| `CNT-ASSET-001` | Service Key, Route Sketch, Red Pennant, lens branch functions | Mixed | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-MATRIX` `ITM-16`–`ITM-19`; `SRC-AM01`, coupled assets |
| `CNT-ARRIVAL-001` | `on_time`/`late` monotonic state and triggers | Mixed | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-AM01`, coupled arrival; `SRC-MATRIX` `STA-06` |
| `CNT-WATCHER-LABEL-001` | Watcher Harness presentation label | Public | `PROJECT_ORIGINAL` | Review only; blocked for `F04` | `SRC-BASE`, Appendix A “Scenario provenance”; `SRC-MATRIX` `MON-01` |
| `CNT-COMBAT-GRAPH-001` | Exact zones, exit boundary, distance, engagement, start positions, and hands | Public/mixed | `PROJECT_ORIGINAL` for mapping; SRD mechanics remain separate | Review only; blocked for `F04` | `SRC-AM01` `B-02`, `B-09`, and coupled hands; `SRC-MATRIX` `SPC-01`–`SPC-06`, `CMB-01`, `CMB-03` |
| `CNT-WATCHER-POLICY-001` | Deterministic Watcher choices and `AM01-R1` | Mixed | `PROJECT_ORIGINAL` | Accepted contract, but review-only packet | `SRC-AM01` `B-06` and `B-07`; `SRC-MATRIX` `MON-19`, `MON-20`, `CMB-07`–`CMB-09` |
| `CNT-ORDER-001` | Mandatory nonlethal disclosure text and timing | Public | `PROJECT_ORIGINAL`; underlying knockout rule is SRD | Review only; exact accepted text may not change | `SRC-AM01` `B-11`; `SRC-MATRIX` `CMB-12` |
| `CNT-ENDING-LOGIC-001` | Success, recovery, failure, retreat, knockout, and safety predicates | Mixed | `PROJECT_ORIGINAL`; knockout mechanic remains SRD | Review only; blocked for `F04` | `SRC-BASE`, “Endings”; `SRC-AM01` `B-09`; `SRC-MATRIX` `STA-08`, `CMB-11` |
| `CNT-CONTROLS-001` | Full-disclosure, unsupported, correction, and safety separation | Out-of-band/mixed | `PROJECT_ORIGINAL` | Review only; separate preflight also open | `SRC-BASE`, “Experience and authority contract” and Appendices C–D; `SRC-MATRIX` `CNT-03`–`CNT-06` |
| `CNT-PACKET-CONTROL-001` | Packet manifest, authority, visibility vocabulary, object-versioning rule, and fail-closed use boundary | Out-of-band | `UNKNOWN` / `BLOCKED`; AI-authored policy/process adaptation | Quarantined desk review only; no operational approval | `SRC-POLICY`, “Fail-closed admission rule” and “Provenance taxonomy”; `SRC-RUN02` §§1–2; `SRC-NEW01` |
| `CNT-GUARDRAIL-001` | Banned/unreviewed content and Teen/PG-13 boundary in §10 | Out-of-band | `UNKNOWN` / `BLOCKED`; AI-authored policy/content adaptation | Quarantined desk review only; separate safety/preflight review remains open | `SRC-POLICY`, “Denylist” and “Trademark, branding, and original-content boundary”; `SRC-BASE` Appendix D; `SRC-NEW01` |
| `CNT-REVIEW-001` | A5/A7/rules checklists and closure record in §11 | Out-of-band | `UNKNOWN` / `BLOCKED`; AI-authored process record | Quarantined desk review only; every approval field remains open | `SRC-BASE` Appendix E; `SRC-POLICY`, “Verification and release checks”; `SRC-RUN02` §§18–19; `SRC-NEW01` |

### 9.3 SRD-derived rules used by the scene cards

The underlying rule fields below remain `SRD_5_2_1_CC_BY_4_0`; the packet is an adapted presentation, not a new rule source. The packet-authored `RULE-*` identifiers, groupings, labels, and summary wording are separately traced to `SRC-NEW01` and remain `UNKNOWN` / `BLOCKED` until A7 validates or replaces them. The cited matrix row contains the exact behavior and test obligation in addition to the direct PDF locator. No row is usable through this draft.

| Rules object ID | Rules-bearing item used here | Provenance class | Exact SRD 5.2.1 locator | Contract locator |
|---|---|---|---|---|
| `RULE-D20-001` | D20 Tests, checks, attacks, saves, DC/AC equality, Advantage/Disadvantage, proficiency | `SRD_5_2_1_CC_BY_4_0` | pp. 6–9, “D20 Tests,” “Advantage/Disadvantage,” and “Proficiency” | `SRC-MATRIX` `CORE-01`–`CORE-03` |
| `RULE-SOCIAL-001` | Roleplay, Indifferent, Influence, Search/Insight | `SRD_5_2_1_CC_BY_4_0` | pp. 10–11, “Social Interaction” and “Roleplaying”; p. 184, “Indifferent” and “Influence”; p. 187, “Search” | `SRC-MATRIX` `CHK-01`–`CHK-03` |
| `RULE-DICESET-001` | Wisdom Dice Gaming Set check with proficiency | `SRD_5_2_1_CC_BY_4_0` | pp. 93–94, “Tool Proficiency” and “Gaming Set” | `SRC-MATRIX` `CHK-04`, `ITM-14` |
| `RULE-EXPLORE-001` | Perception/Survival Search, Investigation Study, Athletics/Acrobatics checks | `SRD_5_2_1_CC_BY_4_0` | pp. 6 and 9, ability/skill checks; p. 187, “Search”; p. 189, “Study” | `SRC-MATRIX` `CHK-05`–`CHK-06` |
| `RULE-CROWBAR-001` | Crowbar Advantage on applicable Strength check and nonstacking Advantage | `SRD_5_2_1_CC_BY_4_0` | p. 97, “Crowbar”; p. 8, “They Don't Stack” | `SRC-MATRIX` `CHK-07`, `ITM-07` |
| `RULE-HOOK-001` | Rope-tied Grappling Hook, 50-ft. catch, Utilize, DC 13 Dexterity (Acrobatics) | `SRD_5_2_1_CC_BY_4_0` | pp. 95, 97, and 99, “Grappling Hook” and “Rope”; p. 191, “Utilize” | `SRC-MATRIX` `ITM-08`, `ITM-09`, `CORE-13` |
| `RULE-TORCH-001` | Torch/Tinderbox source data; slice narrows use to effect-free exploration narration | `SRD_5_2_1_CC_BY_4_0` | pp. 95 and 100, “Torch” and “Tinderbox” | `SRC-MATRIX` `ITM-10`, `ITM-11`; narrowing `SRC-AM01` `B-05` |
| `RULE-COMBAT-001` | Combat turns, Initiative, movement, actions, Bonus Actions, Reactions, attacks, damage | `SRD_5_2_1_CC_BY_4_0` | pp. 13–17, “Combat”; pp. 176–191, relevant glossary entries | `SRC-MATRIX` `CORE-04`–`CORE-13`, `CMB-01`–`CMB-03` |
| `RULE-WEAPONS-001` | Greatsword/Graze, Flail/Sap, Javelin/Slow, hands, range, equip interaction | `SRD_5_2_1_CC_BY_4_0` | pp. 89–91, weapons, properties, and masteries; p. 177, “Attack” | `SRC-MATRIX` `ITM-02`–`ITM-04`, `CMB-03`–`CMB-06` |
| `RULE-UNARMED-001` | Unarmed damage, Grapple, Shove, Prone/Grappled | `SRD_5_2_1_CC_BY_4_0` | p. 190, “Unarmed Strike”; p. 182, “Grappled” and “Grappling”; p. 186, “Prone” | `SRC-MATRIX` `ITM-05`, `STA-02`, `STA-03`, `CMB-10` |
| `RULE-OA-001` | Opportunity Attack timing, Reaction, and exceptions | `SRD_5_2_1_CC_BY_4_0` | pp. 15 and 185, “Opportunity Attacks”; p. 186, “Reaction” | `SRC-MATRIX` `CMB-07`; Watcher Slam eligibility is project ruling `AM01-R1` |
| `RULE-READY-001` | Ready trigger, action or movement payload, Reaction choice, expiry, and post-trigger legality | `SRD_5_2_1_CC_BY_4_0` | pp. 186–187, “Ready” | `SRC-MATRIX` `CORE-10`; accepted mapping `SRC-AM01` `B-02`, `B-06` |
| `RULE-ARMOR-001` | Animated Armor full stat block, Multiattack, and Slam | `SRD_5_2_1_CC_BY_4_0` | p. 259, “Animated Objects — Animated Armor”; pp. 188–189, “Stat Block” | `SRC-MATRIX` `MON-01`–`MON-20`, `CMB-08`, `CMB-09` |
| `RULE-KO-001` | Melee knockout, Unconscious, and begun Short Rest | `SRD_5_2_1_CC_BY_4_0` | pp. 17 and 184, “Knocking Out a Creature”; p. 191, “Unconscious”; p. 187, “Short Rest” | `SRC-MATRIX` `REC-01`–`REC-03`, `STA-04` |
| `RULE-FIGHTER-001` | Rin's fixed Fighter/Champion features and resources | `SRD_5_2_1_CC_BY_4_0` | pp. 47–49, “Fighter” and “Champion”; pp. 86–87, Human/feats; p. 183, “Heroic Inspiration” | `SRC-MATRIX` `FTR-01`–`FTR-13` |
| `RULE-SPATIAL-001` | Speed, Dash, Disengage, Dodge, reach, ranged penalty, crawling and dragging | `SRD_5_2_1_CC_BY_4_0` | pp. 13–15; pp. 180–188, named glossary entries | `SRC-MATRIX` `CORE-07`–`CORE-10`, `SPC-02`–`SPC-08`; project mapping `SRC-AM01` `B-02` |

### 9.4 Packet-authored scene, ending, and supported-intent object provenance

The `SCN-*`, `END-*`, and `INT-*` objects are newly AI-authored packet mappings and routing records, not accepted rules or exact accepted prose. They are `UNKNOWN` / `BLOCKED` under `SRC-NEW01`; the accepted scenario fact or predicate and each referenced D20, action, item, feature, condition, or monster mechanic retain their separately traced classes. All remain quarantined desk-review material and `SPEC_ONLY / NOT IMPLEMENTED`.

| Packet object IDs | Underlying accepted input/source | Embedded SRD rule objects | Current packet decision |
|---|---|---|---|
| `SCN-00-HOOK`, `SCN-01-QUAY`, `SCN-02-SLUICE`, `SCN-03-LANTERN`, `SCN-04-FIRST-LIGHT` | `SRC-BASE` “Original scenario baseline” and Appendix A; `SRC-AM01` coupled arrival/hands and `B-02`–`B-11`; `SRC-MATRIX` `CNT-01` | None; rules remain in §9.3 | `UNKNOWN` / `BLOCKED`; `SRC-NEW01`; quarantined desk review only |
| `END-SAFETY-001`, `END-SUCCESS-001`, `END-RECOVERY-001`, `END-FAIL-LATE-001`, `END-FAIL-RETREAT-001`, `END-FAIL-KO-001` | `SRC-BASE` “Endings”; `SRC-AM01` `B-09`; `SRC-MATRIX` `STA-08` | `RULE-KO-001` only where the terminal predicate is knockout | `UNKNOWN` / `BLOCKED`; `SRC-NEW01`; quarantined desk review only |
| `INT-S1-TALK-001`, `INT-S1-NERA-INSIGHT-001`, `INT-S1-NERA-INFLUENCE-001`, `INT-S1-TOVIN-INSIGHT-001`, `INT-S1-TOVIN-INFLUENCE-001`, `INT-S1-TOVIN-DICE-001`, `INT-S1-INSPECT-001`, `INT-S1-PROCEED-001` | `SRC-BASE` Appendix A; `SRC-AM01` `B-10` and coupled assets/arrival; `SRC-MATRIX` `CNT-02` | `RULE-D20-001`, `RULE-SOCIAL-001`, `RULE-DICESET-001` | `UNKNOWN` / `BLOCKED`; `SRC-NEW01`; quarantined desk review only |
| `INT-S2-CLUE-PERCEPTION-001`, `INT-S2-CLUE-SURVIVAL-001`, `INT-S2-CLUE-INVESTIGATION-001`, `INT-S2-TRAVERSE-ATHLETICS-001`, `INT-S2-TRAVERSE-ACROBATICS-001`, `INT-S2-TRAVERSE-HOOK-001`, `INT-S2-TORCH-001`, `INT-S2-INSPECT-001` | `SRC-AM01` `B-05` and coupled assets/arrival; `SRC-MATRIX` `STA-06`, `ITM-16`–`ITM-19` | `RULE-D20-001`, `RULE-EXPLORE-001`, `RULE-CROWBAR-001`, `RULE-HOOK-001`, `RULE-TORCH-001` | `UNKNOWN` / `BLOCKED`; `SRC-NEW01`; quarantined desk review only |
| `INT-S3-MOVE-001`, `INT-S3-ATTACK-001`, `INT-S3-DASH-001`, `INT-S3-DISENGAGE-001`, `INT-S3-DODGE-001`, `INT-S3-READY-001`, `INT-S3-SEARCH-001`, `INT-S3-STUDY-001`, `INT-S3-UTILIZE-001`, `INT-S3-SECOND-WIND-001`, `INT-S3-ACTION-SURGE-001`, `INT-S3-RETREAT-001`, `INT-S3-INSPECT-CONTROL-001` | `SRC-AM01` `B-01`–`B-09`, `B-11`, and coupled hands; `SRC-MATRIX` `CNT-03`–`CNT-06`, `SPC-01`–`SPC-08` | `RULE-COMBAT-001`, `RULE-WEAPONS-001`, `RULE-UNARMED-001`, `RULE-OA-001`, `RULE-READY-001`, `RULE-ARMOR-001`, `RULE-KO-001`, `RULE-FIGHTER-001`, `RULE-SPATIAL-001` | `UNKNOWN` / `BLOCKED`; `SRC-NEW01`; quarantined desk review only |
| `INT-S4-RESOLVE-001` | `SRC-BASE` “Endings”; `SRC-AM01` `B-09`; `SRC-MATRIX` `ITM-19`, `STA-08` | `RULE-KO-001` only where the terminal predicate is knockout | `UNKNOWN` / `BLOCKED`; `SRC-NEW01`; quarantined desk review only |

### 9.5 Exact prose/dialogue object ledger

This ledger distinguishes exact accepted copies from new packet expression. `TXT-GLOBAL-HOOK-001` and `TXT-S3-ORDER-001` contain exact `PROJECT_ORIGINAL` text copied from separately traced accepted sources; their new IDs and metadata are still `SRC-NEW01`, and this packet grants them no use. Every other row is new expression, current class `UNKNOWN`, decision `BLOCKED`, and authorized only for quarantined desk review to resolve the object. No row may enter a prompt, fixture, model context, dry run, participant packet, corpus, export, or release through this version. A7 must reclassify a frozen object with a recorded review, replace it, or remove it. Grouping in one row does not permit partial approval without listing the approved IDs.

| Object IDs | Content | Visibility | Current class / decision | Input/source locator |
|---|---|---|---|---|
| `TXT-GLOBAL-HOOK-001` | Accepted opening premise, copied verbatim | Public | Exact text `PROJECT_ORIGINAL`; packet use blocked; ID/metadata `SRC-NEW01` | `SRC-RUN02` §5 P4; `SRC-BASE` “Original scenario baseline”; `SRC-NEW01` for ID/metadata |
| `TXT-GLOBAL-THREAT-001`, `TXT-GLOBAL-ACTION-001` | Threat and neutral-action copy | Public | `UNKNOWN` / `BLOCKED` | `SRC-BASE` “Experience and authority contract”; `SRC-MATRIX` `ENC-01`, `CNT-03`; `SRC-NEW01` |
| `TXT-GLOBAL-UNSUPPORTED-001` | Unsupported/clarify template | Public | `UNKNOWN` / `BLOCKED`; operator intent separately traced | `SRC-OP02` §14; `SRC-MATRIX` `CNT-04`; `SRC-NEW01` |
| `TXT-S1-OPEN-001`, `TXT-S1-NERA-OPEN-001`, `TXT-S1-TOVIN-OPEN-001`, `TXT-S1-PROMPT-001` | Fogbound Quay opening, NPC opening dialogue, optional prompt | Public | `UNKNOWN` / `BLOCKED` | `SRC-BASE` Appendix A; `SRC-MATRIX` `CNT-01`, `CNT-02`; `SRC-NEW01` |
| `TXT-S1-NERA-INSIGHT-COMMIT-001`, `TXT-S1-NERA-INSIGHT-SUCC-001`, `TXT-S1-NERA-INSIGHT-FAIL-001`, `TXT-S1-NERA-WILLING-001`, `TXT-S1-NERA-INF-COMMIT-001`, `TXT-S1-NERA-INF-SUCC-001`, `TXT-S1-NERA-INF-FAIL-001` | Nera commitments, reveals, dialogue, and outcomes | Public on stated trigger | `UNKNOWN` / `BLOCKED`; mechanics separately traced | `SRC-BASE` Appendix A “Fixed P0-05 check sheet”; `SRC-MATRIX` `CHK-01`–`CHK-03`; `SRC-NEW01` |
| `TXT-S1-TOVIN-INSIGHT-COMMIT-001`, `TXT-S1-TOVIN-INSIGHT-SUCC-001`, `TXT-S1-TOVIN-INSIGHT-FAIL-001`, `TXT-S1-TOVIN-WILLING-001`, `TXT-S1-TOVIN-INF-COMMIT-001`, `TXT-S1-TOVIN-INF-SUCC-001`, `TXT-S1-TOVIN-INF-FAIL-001` | Tovin concern, Influence, dialogue, and atomic asset outcomes | Public on stated trigger | `UNKNOWN` / `BLOCKED`; mechanics separately traced | `SRC-BASE` Appendix A; `SRC-AM01` coupled assets; `SRC-MATRIX` `CHK-01`–`CHK-03`, `ITM-17`, `ITM-18`; `SRC-NEW01` |
| `TXT-S1-TOVIN-DICE-OFFER-001`, `TXT-S1-TOVIN-DICE-SUCC-001`, `TXT-S1-TOVIN-DICE-FAIL-001` | Dice-game commitment and outcomes | Public on stated trigger | `UNKNOWN` / `BLOCKED`; mechanics separately traced | `SRC-MATRIX` `CHK-04`, `ITM-14`; `SRC-NEW01` |
| `TXT-S1-EXIT-001` | Quay exit copy | Public | `UNKNOWN` / `BLOCKED` | `SRC-AM01` coupled arrival/assets; `SRC-NEW01` |
| `TXT-S2-OPEN-001`, `TXT-S2-ASSET-KS-001`, `TXT-S2-ASSET-K-001`, `TXT-S2-ASSET-S-001`, `TXT-S2-ASSET-NONE-001` | Sluice opening and four exact asset states | Public | `UNKNOWN` / `BLOCKED`; branch facts separately traced | `SRC-AM01` coupled arrival/assets; `SRC-MATRIX` `CHK-05`, `STA-06`; `SRC-NEW01` |
| `TXT-S2-CLUE-COMMIT-001`, `TXT-S2-CLUE-SUCC-001`, `TXT-S2-CLUE-FAIL-001` | Clue commitment and failure-forward copy | Public on stated trigger | `UNKNOWN` / `BLOCKED`; mechanics separately traced | `SRC-MATRIX` `CHK-05`; `SRC-NEW01` |
| `TXT-S2-TRAVERSE-PROMPT-001`, `TXT-S2-TRAVERSE-COMMIT-001`, `TXT-S2-TRAVERSE-SUCC-001`, `TXT-S2-TRAVERSE-FAIL-001`, `TXT-S2-EXIT-001` | Traversal prompt, commitment, outcomes, and exit | Public on stated trigger | `UNKNOWN` / `BLOCKED`; mechanics separately traced | `SRC-MATRIX` `CHK-06`, `CHK-07`, `ITM-07`–`ITM-10`, `ITM-19`; `SRC-NEW01` |
| `TXT-S3-OPEN-001` | Dark Lantern start-state prose | Public | `UNKNOWN` / `BLOCKED`; state separately traced | `SRC-AM01` coupled hands and `B-02`/`B-04`; `SRC-MATRIX` `CMB-01`, `SPC-01`, `SPC-07`; `SRC-NEW01` |
| `TXT-S3-ORDER-001` | Exact mandatory maintenance-order sentence | Public | Exact text `PROJECT_ORIGINAL`; packet use blocked; ID/metadata `SRC-NEW01` | `SRC-AM01` `B-11`; `SRC-MATRIX` `CMB-12`; `SRC-NEW01` for ID/metadata |
| `TXT-S3-INIT-001`, `TXT-S3-FIRST-TURN-001` | Initiative and first-turn prompt | Public | `UNKNOWN` / `BLOCKED`; mechanic separately traced | `SRC-AM01` `B-03`; `SRC-MATRIX` `CHR-07`, `CORE-05`; `SRC-NEW01` |
| `TXT-S3-MOVE-001`, `TXT-S3-DASH-001`, `TXT-S3-ATTACK-MISS-001`, `TXT-S3-ATTACK-HIT-001`, `TXT-S3-ATTACK-CRIT-001`, `TXT-S3-OA-001`, `TXT-S3-CONDITION-001` | Closed combat narration templates | Public after state | `UNKNOWN` / `BLOCKED`; rule fields separately traced | `SRC-OP02` §§6–11; `SRC-MATRIX` `CORE-05`–`CORE-10`, `CMB-01`–`CMB-10`; `SRC-NEW01` |
| `TXT-S3-NO-RESULT-SEARCH-001`, `TXT-S3-NO-RESULT-STUDY-001`, `TXT-S3-UTILIZE-REJECT-001` | Combat no-result/rejection copy | Public | `UNKNOWN` / `BLOCKED`; operator convention separately traced | `SRC-OP02` §8; `SRC-MATRIX` `CORE-11`–`CORE-13`; `SRC-NEW01` |
| `TXT-S3-WATCHER-DEFEATED-001`, `TXT-S3-RIN-KO-001`, `TXT-S3-RETREAT-001` | Terminal combat copy | Public after state | `UNKNOWN` / `BLOCKED`; terminal mechanics separately traced | `SRC-AM01` `B-09`, `B-11`; `SRC-MATRIX` `CMB-11`, `REC-01`–`REC-03`; `SRC-NEW01` |
| `TXT-END-SAFETY-001`, `TXT-END-SUCCESS-001`, `TXT-END-RECOVERY-001`, `TXT-END-FAIL-LATE-001`, `TXT-END-FAIL-RETREAT-001`, `TXT-END-FAIL-KO-001` | Exact closing copy for every accepted outcome | Public/out-of-band on stated trigger | `UNKNOWN` / `BLOCKED`; outcome predicates separately traced | `SRC-BASE` “Endings”; `SRC-AM01` `B-09`; `SRC-MATRIX` `STA-08`; `SRC-NEW01` |

### 9.6 Required SRD attribution and change indication

Any distribution containing the adapted SRD-derived material in this packet must preserve the project policy's exact notice. This review draft records it here so it cannot be lost during later packaging:

> This work includes material from the System Reference Document 5.2.1 (“SRD 5.2.1”) by Wizards of the Coast LLC, available at https://www.dndbeyond.com/srd. The SRD 5.2.1 is licensed under the Creative Commons Attribution 4.0 International License, available at https://creativecommons.org/licenses/by/4.0/legalcode.

> Changes: SRD 5.2.1 material has been excerpted, reformatted, structured, and adapted for software use in this project.

This notice does not imply endorsement and does not convert original or unknown expression into SRD content.

## 10. Banned and unreviewed content guardrails

The following are hard stops for this packet and any derived prompt, card, recording, export, or fixture:

- No SRD 5.1, SRD 5.2.0, D&D Beyond Basic Rules, rulebook, supplement, published adventure, setting, marketplace material, wiki, forum, stream, actual-play transcript, third-party book, or homebrew source.
- No named setting, character, location, plot, distinctive monster, item, deity, faction, spell lore, art, map, logo, or other non-SRD intellectual property. Renaming or paraphrasing a denied source does not cure it.
- No public product name, badge, or claim using quarantined branding, “official,” “approved,” sponsorship, or endorsement language. The required attribution belongs only in the appropriate credits/legal surface.
- No new creature, NPC, ally, reinforcement, summon, hazard, trap, secret door, alternate route, item benefit, magic, clue, check, DC, condition, damage, rescue, difficulty adjustment, ending, or persistent world fact.
- No scene prose that turns fog, darkness, weather, light, zone description, or the Torch into a modifier, obstruction, cover, hidden state, threat, duration, or damage source.
- No Watcher speech, language comprehension, motive, emotion, surrender behavior, escape attempt, mercy choice, pursuit beyond the boundary, or tactic outside the accepted algorithm.
- No sexual content, sexual violence, hate-based targeting, encouragement of self-harm, graphic torture, or graphic gore. Ordinary fantasy violence and mild horror remain within the accepted Teen/PG-13 ceiling and are subject to the separate participant's lines, veils, phobias, and out-of-band controls.
- No reuse of participant text, model narration, boundary details, reports, or session excerpts as adventure copy. Runtime material retains its runtime provenance and narrow handling authorization unless separately reviewed and reclassified.
- No `UNKNOWN`, denied, mixed-version, missing-locator, or unreviewed object may enter any prompt, fixture, model context, dry run, participant packet, reusable corpus, export, or release path. Packet-authored objects in §§9.2–9.5 are deliberately blocked until human review; their presence here is not approval, including for a contract-only or synthetic rehearsal.

If a reviewer suspects similarity, brand confusion, contamination, or an unlisted source, quarantine the affected object and all dependent objects until A7 resolves or removes it.

## 11. Human review and `F04` closure checklist

### 11.1 A5 adventure-design review — named human required

- [ ] Confirm the reviewed file hash and packet version match the manifest.
- [ ] Confirm every scene has the accepted objective, zones, entry condition, exit condition, supported intents, state effects, failure-forward behavior, and terminal path.
- [ ] Confirm Nera's and Tovin's roles, concerns, voices, language, assets, willingness triggers, and failure behavior introduce no new branch or implied mechanic.
- [ ] Confirm all four Service Key/Route Sketch combinations are explicit and that Tovin's sketch/pennant grant is atomic.
- [ ] Confirm `arrival=on_time` is set only on Sluice entry, only clue/traversal failure makes it late, and late never reverts.
- [ ] Confirm every run performs exactly one traversal, secures the lens, enters exactly one combat, and can reach exactly one accepted ending.
- [ ] Confirm optional prompts are neutral, non-exhaustive when appropriate, and do not coach an asset, tactic, continued combat, or preferred ending.
- [ ] Confirm the new prose is concise, internally consistent, localization-safe, within the Teen/PG-13 ceiling, and carries no hidden authoritative fact.
- [ ] Confirm every ending states exactly the accepted consequence, with no added casualty, reward, punishment, rescue, or sequel fact.
- [ ] Record each approved, rejected, or revised scene/content object ID (`CNT-*`, `SCN-*`, `INT-*`, `END-*`, and `TXT-*`); do not sign a group implicitly. A7 separately resolves the provenance/admission decision for every prefix, including `RULE-*` wrappers.

### 11.2 A7 provenance, licensing, brand, and content review — named human required

- [ ] Confirm the source declaration and the exact set of inputs used to create this draft.
- [ ] Verify every content/rules object has a stable ID, visibility, current class, admission decision, scope, and source locator.
- [ ] Run and record originality, passage-similarity, protected-name, recognizable-lore, trademark, trade-dress, and false-endorsement review against appropriate approved procedures.
- [ ] Confirm no denied or unreviewed source, named non-SRD IP, mixed-version rule, or unsupported SRD object entered the text.
- [ ] For every `UNKNOWN` object of any prefix, explicitly reclassify it to an allowed class, replace it, or remove it; record reviewer, date, method, decision, authorized-use scope, and residual concern.
- [ ] Confirm every SRD-derived field remains `SRD_5_2_1_CC_BY_4_0`, is within approved slice scope, cites a physical PDF page/entry, and is marked adapted where applicable.
- [ ] Confirm `AM01-R1` and all other project-authored mappings remain `PROJECT_ORIGINAL`, not misrepresented as SRD text.
- [ ] Confirm the exact attribution and change indication are present wherever required and that no endorsement is implied.
- [ ] Confirm content-safety exclusions and the separate runtime provenance rules for player/model text remain intact.
- [ ] Compute and record the final reviewed packet hash only after all approved revisions are frozen.

### 11.3 Human rules review — named reviewer independent of authorship where required

- [ ] Verify every DC, modifier, Advantage/Disadvantage state, attempt cap, asset effect, and resource timing against operator baseline v0.2 and the cited matrix row.
- [ ] Verify the packet implements Amendment 01 `B-01` through `B-11` without weakening, extending, or silently restating a value.
- [ ] Verify Stealth/Hide remains unsupported; Common is fixed for both NPCs; fog/light is narrative only; and the item allowlist is exhaustive.
- [ ] Verify Sluice clue and traversal branches, Crowbar, Rope/Hook, and Torch/Tinderbox language admit no extra use or failure effect.
- [ ] Verify Dark Lantern positions, distances, engagement, hands, static Initiative 12, total-12 tie, exact maintenance-order timing, Watcher algorithm, Slam dice, `AM01-R1`, retreat, and qualification predicates.
- [ ] Verify combat Search, Study, and Utilize copy matches the no-result/rejection operator cards.
- [ ] Verify narration templates cannot execute state and use only already-applied public event fields.
- [ ] Verify every terminal card respects knockout priority, no pursuit, no post-terminal mutation, and the exact ending truth table.
- [ ] Verify every rules-bearing item has a correct SRD physical-page locator and every project rule is labeled original.
- [ ] Record every defect by object ID and severity; approval is withheld until all fielding-blocking defects are closed in a new frozen version.

### 11.4 Required closure record

```text
Packet ID/version: P0-05-SCENE-PROV-PACKET / 0.1
Frozen file SHA-256: [OPEN]
A5 reviewer (named human): [OPEN]
A5 review date / evidence ID / disposition: [OPEN]
A7 reviewer (named human): [OPEN]
A7 review date / evidence ID / disposition: [OPEN]
Separate human rules reviewer (not an F04 closure field): [OPEN]
Separate rules review date / evidence ID / disposition: [OPEN]
All UNKNOWN objects resolved: NO
All F04-blocking scene/provenance defects closed: NO
Run-pack/operator/packet manifest match: NO
F04 status: OPEN
Current packet use: QUARANTINED DESK REVIEW ONLY — NO PROMPT, FIXTURE, DRY-RUN, PARTICIPANT, CORPUS, EXPORT, OR RELEASE USE
Human fielding authorization: NONE — separate preflight required
```

`F04` closes only when named human A5 and A7 reviewers approve the same frozen packet version and hash, all `UNKNOWN` objects are resolved, and the run-pack manifest records this exact version. The human rules review remains a separate required readiness input associated with the open operator/rules blockers; including its checklist here does not redefine `F04`. Closing `F04` alone would not close the remaining `F01`–`F17` blockers, authorize a participant, complete P0-05/P0-06, open G0, or authorize production.
