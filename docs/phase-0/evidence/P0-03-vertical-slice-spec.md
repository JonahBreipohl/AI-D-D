# P0-03 — Phase 2 vertical-slice acceptance specification

Status: **Accepted by the owner on 2026-09-18 and amended on 2026-09-23 as the active P0-05/P0-06 research baseline; does not authorize recruitment, human research, G0, or production implementation**
Baseline: Owner-approved D1–D15, 2026-09-17
Rules source: Pinned **SRD 5.2.1**, SHA-256 `8974902d109d6e63672d7c490bde9ccf052410503d9cfa768237154fbc5e3d87`
Review: **Independent planning-coherence audit passed and human acceptance recorded 2026-09-18; Amendment 01 contract audit and combat-state walk-through passed and human acceptance recorded 2026-09-23**
Active amendment: [P0-03 Amendment 01](P0-03-amendment-01-proposed.md), accepted and in force 2026-09-23. This base specification plus Amendment 01 is the active research contract; Amendment 01 controls wherever the two conflict.

## Owner acceptance core

### Accepted decision

The owner accepted **The Signal at Glasswater Weir** as the concrete Phase 2 baseline: one invited adult already familiar with fifth-edition play, one local-authority/text-only 60–90 minute solo run, the fixed level-3 pregen **Rin Alder**, and the single **Transparent Guide** persona. The playable clock begins with the first actionable in-world prompt and ends at a terminal result; boundary setup and the post-session survey are timed separately.

### Original scenario baseline

**Premise and objective.** Storm fog has swallowed Glasswater Weir. Its navigation beacon is dark, and a relief ferry will soon enter the channel. Rin must recover the displaced signal lens, reach the lantern room, survive its malfunctioning guardian, and relight the beacon.

| Scene | Named zones | Required play and failure-forward transition |
|---|---|---|
| **1. Fogbound Quay** | Lockhouse, Ferry Steps, Reedbank | Social objective: reconcile lockkeeper **Nera Pell** (defensive custodian of the service key) and salvage diver **Tovin Ash** (wrongly blamed witness). Rin may gain Nera’s key and/or Tovin’s route sketch and red signal pennant through conversation, Influence, Insight, or the dice-set affordance. Refusal or failed checks yield no asset but always reveal the public spillway route. |
| **2. Broken Sluice** | West Bank, Sluice Walk, Lower Apron | Exploration objective: recover the lens and reach the tower. Supported approaches use Perception, Investigation, Survival, Athletics, Stealth, the crowbar, rope, grappling hook, or torch. First-check success reaches the tower **on time**. Failure reveals a slower safe route and reaches it **late**; no retry loop, missed-clue lock, or damage tax is permitted. |
| **3. Dark Lantern** | Entry Deck, Gear Floor, Lens Dais | Exactly one combat: the **Watcher Harness**, using one unchanged SRD **Animated Armor** stat block. It starts at the Lens Dais; Rin starts at the Entry Deck; no surprise or reinforcement occurs. The armor’s precommitted maintenance order is to knock out rather than kill an intruder. |
| **4. First Light** | Lens Dais, Roof Shutter | Apply one authored ending below, state the consequences, and close the session. |

**Endings.** Combat victory while on time produces **success**: the beacon guides the ferry through. Combat victory while late plus Tovin’s pennant produces **recovery**: the ferry anchors safely, but delivery is delayed and the beacon is restored too late for a full success. A late victory without the pennant, retreat, or precommitted nonlethal knockout produces **failure**: the ferry turns back safely and the supplies are delayed. A failed social or exploration check changes the route; it never prevents combat or an ending. A safety-ended session is not an in-fiction failure.

### Fixed pregen and encounter

**Rin Alder** is a Medium Human Soldier, level-3 Champion Fighter: Str 17 (+3), Dex 14 (+2), Con 14 (+2), Int 8 (−1), Wis 12 (+1), Cha 10 (+0); PB +2; AC 17; HP 28; 3d10 Hit Dice; Speed 30 ft.; Initiative +2 with Advantage; Passive Perception 13. Rin has no spells or magic items. Appendix B fixes every proficiency, feature, attack, resource, and carried item.

The only combat opponent is one Animated Armor reskinned in original fiction as the Watcher Harness: AC 18, HP 33, Speed 25 ft., Initiative +2 (12), CR 1 (200 XP), two Slam attacks per action at +4 to hit for 5 (1d6 + 2) Bludgeoning damage each. This is within the SRD’s 225-XP moderate budget for one level-3 character. No live difficulty adjustment, hidden mercy, added foe, or altered stat is allowed.

### Experience and authority contract

The Transparent Guide is concise, beginner-friendly, neutral in rules strictness, and explicit about medium threat. It explains rules on request and labels deterministic rules, bounded rulings, and unsupported intents. It may change wording and pacing, never mechanics, hidden-information access, a committed consequence, a roll, state, or correction consent.

Every authoritative action, target, rule/ruling basis, DC or defense, modifier, advantage state, resource cost, possible outcome, and visibility class is committed before randomness. The player receives the actionable stakes and all facts their character should know before choosing or rolling. For the P0-05 paper prototype only, every non-hidden committed field—including the exact DC or defense and possible consequences—is shown before the roll. P0-04 separately compares that convention with sealed-before-roll/reveal-after treatment. This evidence-generating convention does not finalize the Phase 2 product policy: P0-07 will decide whether an exact DC or hidden fact is immediately visible, sealed for later audit, or revealed after resolution; concealment never permits post-roll selection. State is applied before outcome narration.

### Acceptance

- [x] Accepted 2026-09-18: the named scenario, scene graph, NPC roles, zones, encounter, and ending routes as the P0-05/P0-06 starting baseline.
- [x] Accepted 2026-09-18: Rin Alder’s exact build and the initial supported/unsupported envelope in Appendices B–C.
- [x] Accepted 2026-09-18: the timing definition, the full-disclosure P0-05 prototype convention, and the safety, fairness, accessibility, data, correction, and measurement constraints in Appendix D.
- [x] Accepted 2026-09-23: [Amendment 01](P0-03-amendment-01-proposed.md) in full as the deterministic P0-05/P0-06 research baseline; it controls any conflict with this base text.

Human acceptance of all three original boxes completed the base P0-03 on 2026-09-18, and acceptance of Amendment 01 placed the amended contract in force on 2026-09-23. Evidence may later justify another versioned revision, but P0-05 and P0-06 must test and trace this active contract rather than originate a different slice. Neither acceptance clears the operational preflight, authorizes recruitment or human research, opens G0, or authorizes production implementation.

## Appendix A — Scene and branch detail

### Scene logic

- **Nera Pell:** an original adult lockkeeper who wants the ferry safe but fears blame for deferred maintenance. A willing or successful Influence outcome yields the service key. Failure or refusal reveals the public route without the key.
- **Tovin Ash:** an original adult salvage diver who saw the lens fall and wants the unsafe maintenance line acknowledged. Insight can expose that concern; a willing or successful Influence outcome, or the supported dice-set interaction, yields the route sketch and red signal pennant. Failure still leaves the public route.
- **Broken Sluice:** the key opens the direct maintenance walk; the route sketch identifies the lens below the walk. Without either, Search/Study reveals both facts. One declared supported traversal check is resolved. Success establishes `arrival=on_time`; failure establishes `arrival=late` and opens the slower safe route automatically.
- **Dark Lantern:** Entry Deck ↔ Gear Floor ↔ Lens Dais are adjacent; each transition is no more than 25 feet and uses normal movement. Creatures in the same zone can engage within 5 feet. Leaving an engagement without Disengage can trigger an Opportunity Attack. The armor follows its fixed stat block and, if a Slam would reduce Rin to 0 HP, uses the SRD knock-out option: Rin instead has 1 HP, becomes Unconscious, and begins a Short Rest. That operating order is discoverable before combat and committed before Initiative.
- **No secret rescue:** the public route, slow-route transition, pennant recovery, and nonlethal guardian order are authored before play. The Guide cannot add, remove, or activate them to favor a result.

### Fixed P0-05 check sheet

These are paper-prototype values needed to run P0-05 without facilitator invention. P0-06 traces their mechanics, and P0-07 may recommend a versioned production-policy change from evidence; neither task may pretend these values were left unspecified.

- Nera and Tovin begin **Indifferent** and **Hesitant** about giving their respective assets. A direct supported Influence attempt uses DC 15 and Charisma (Deception, Intimidation, or Persuasion) according to the stated approach. Each asset request receives at most one Influence check in the timed run.
- Before that attempt, a Wisdom (Insight) Search check at DC 12 can reveal the NPC’s stated concern. If the player then directly addresses it—offering to log Nera’s storm damage without blaming her, or promising to document Tovin’s warning—the NPC becomes **Willing** for that request and provides the asset without an Influence roll. The facilitator uses only these authored criteria.
- Tovin’s dice-set alternative is the SRD Gaming Set Utilize check to win: Wisdom with Dice Set proficiency at DC 20. It represents one short, open game. Success yields both the sketch and pennant; failure yields neither and cannot be replayed during the timed run.
- At Broken Sluice, a missing key or sketch is recovered functionally through one DC 12 Search/Study check using Wisdom (Perception or Survival) or Intelligence (Investigation), as appropriate to the declared method. Failure still reveals the necessary route/lens after a delay and sets `arrival=late`.
- Traversal then uses one DC 13 check: Strength (Athletics), Dexterity (Acrobatics), or the Grappling Hook’s printed Dexterity (Acrobatics) check. Crowbar leverage grants its printed Advantage when applicable; rope alone changes fiction but grants no unlisted bonus. Success preserves the current timing state; failure opens the safe route and sets `arrival=late`. No exploration failure deals damage or blocks the tower.
- Tactical Mind, Heroic Inspiration, Advantage/Disadvantage, and other accepted character resources resolve before the final success/failure state is recorded. All DCs, modifiers, possible state changes, and allowed resource uses are face-up under the P0-05 prototype convention.

### Scenario provenance

The working title, Glasswater Weir, Rin Alder, Nera Pell, Tovin Ash, the Watcher Harness label, scene/zone names, premise, dialogue, state flags, and branch graph are `PROJECT_ORIGINAL` content identifiers requiring P0-08 originality/brand review. They are not rules authority. Animated Armor and every resolution mechanic remain `SRD_5_2_1_CC_BY_4_0`; no mechanic may be relabeled original merely because its prose or identifier changes.

## Appendix B — Exact level-3 pregen and SRD verification

### Build record

| Field | Fixed value | Pinned SRD locator |
|---|---|---|
| Identity | Rin Alder; Medium Human; Soldier; Fighter 3 (Champion); 900 XP; Common, Goblin, Dwarvish | PDF pp. 20, 23, 47, 49, 83, 86 |
| Ability method | Standard Array assigned 15/13/14/8/12/10; Soldier adds +2 Str and +1 Dex → 17/14/14/8/12/10 | p. 21, “Generate/Assign/Adjust Ability Scores”; p. 83, “Soldier” |
| Human traits | Resourceful; Skillful → Investigation; Versatile → Skilled (Insight, Stealth, Survival) | p. 86, “Human”; p. 87, “Skilled” |
| Soldier benefits | Athletics, Intimidation, Dice gaming-set proficiency; Savage Attacker; choose 50 GP equipment option | p. 83, “Soldier”; p. 87, “Savage Attacker” |
| Fighter proficiencies | Str and Con saves; all Simple/Martial weapons; Light/Medium/Heavy armor and Shields; class skills Perception and Persuasion | p. 47, “Core Fighter Traits” |
| Derived defenses | PB +2; HP 28 = 12 at level 1 + 8 + 8 fixed; 3d10 Hit Dice; AC 17 = Chain Mail 16 + Defense 1; Speed 30 ft.; Initiative +2 with Advantage; Passive Perception 13 | pp. 22–23, “Fill In Numbers/Level Advancement”; pp. 47–49; pp. 86, 88, 92 |
| Saves | Str +5, Con +4; Dex +2, Int −1, Wis +1, Cha +0 | pp. 22–23; p. 47 |
| Proficient skills | Athletics +5 with Advantage; Intimidation +2; Perception +3; Persuasion +2; Investigation +1; Insight +3; Stealth +4 with Disadvantage in Chain Mail; Survival +3 | pp. 22, 49, 83, 86–87, 92 |
| Fighter resources | Second Wind 2 uses (Bonus Action, 1d10 + 3 HP); Action Surge 1/Short or Long Rest; Tactical Mind; three Weapon Masteries | pp. 47–48, “Fighter Features” |
| Champion features | Improved Critical (weapon/Unarmed Strike critical on 19–20); Remarkable Athlete (Advantage on Initiative and Athletics; post-critical movement) | p. 49, “Fighter Subclass: Champion” |
| Other resources | Heroic Inspiration 1 after a Long Rest; Savage Attacker once per turn; no spells | pp. 86–87; p. 183, “Heroic Inspiration” |

Fixed attacks and masteries:

- **Greatsword:** +5 to hit; 2d6 + 3 Slashing; Heavy, Two-Handed; Graze mastery.
- **Flail:** +5 to hit; 1d8 + 3 Bludgeoning; Sap mastery.
- **Javelin (four carried):** +5 to hit; 1d6 + 3 Piercing; Thrown 30/120; Slow mastery.

Attack math and weapon data trace to SRD pp. 22, 48, and 89–91. Critical hits trace to pp. 16 and 49; Graze/Sap/Slow trace to p. 90.

Equipment uses the Fighter 155 GP option plus Soldier 50 GP option (205 GP), then purchases Chain Mail (75), Greatsword (50), Flail (10), four Javelins (2), Backpack (2), Crowbar (2), Rope (1), Grappling Hook (2), Torch (0.01), Tinderbox (0.5), Waterskin (0.2), Traveler’s Clothes (2), and Dice gaming set (0.1), leaving **58 GP, 1 SP, 9 CP**. Costs and uses trace to SRD pp. 47, 83, and 91–100. The GM declines the optional higher-level common magic item (p. 24).

### Combat roster verification

The single Animated Armor’s summarized values above trace to SRD p. 259, “Animated Objects — Animated Armor,” including its Construct type, Blindsight, immunities, Multiattack, and Slam. The one-character level-3 moderate budget of 225 XP traces to p. 202, “Combat Encounter Difficulty.” The precommitted knock-out result traces to p. 184, “Knocking Out a Creature.” P0-06 must carry these locators field by field and may not use `PROJECT_ORIGINAL` as provenance for any rule or number.

## Appendix C — Initial supported action and mechanic envelope

### Supported in P0-05; traced and frozen in P0-06

- **Core resolution:** D20 Tests; proficiency; Advantage/Disadvantage; ability checks; saving throws; attack rolls; critical hits; damage/healing; Initiative and turn order; actions, Bonus Actions, Reactions; movement; Opportunity Attacks; Short Rest state initiation only for the knock-out ending, with no completed rest or recharge during timed play.
- **Social:** ordinary no-roll conversation; Influence using Deception, Intimidation, or Persuasion; Search using Insight; Study using Investigation; Utilize with the Dice set. The SRD-fixed check to win the dice game is Wisdom DC 20. NPC willingness/hesitation/refusal must be authored, not improvised after a roll.
- **Exploration:** Search with Perception or Survival; Study with Investigation; Strength (Athletics), Dexterity (Acrobatics), and Dexterity (Stealth); crowbar leverage; rope; grappling-hook use (the SRD-fixed Dexterity [Acrobatics] DC 13); torch/tinderbox; the direct and slow routes; the three named zone sets.
- **Combat actions:** Attack, Dash, Disengage, Dodge, Ready, Search, Study, and Utilize; normal movement between adjacent zones; melee engagement and Opportunity Attacks; Greatsword, Flail, Javelin, and Unarmed Strike (damage, grapple, or shove); the Grappled, Prone, Unconscious, and Bloodied states; the armor’s Multiattack/Slam; nonlethal knock-out.
- **Character mechanics:** all values, proficiencies, feats, masteries, Fighter/Champion features, resources, equipment, and recovery rules in Appendix B; tracking weapon hands, four Javelins, HP, Second Wind, Action Surge, Heroic Inspiration, and once-per-turn Savage Attacker.
- **Player controls:** inspect public state, inventory, resources, zone relations, rule/ruling basis, dice record, event history, and current objective; ask for a rules explanation; raise a dispute; request correction/rewind; pause, stop, or report.

Coverage locators for these groups are SRD pp. 5–18 (“Playing the Game”), pp. 47–49 (“Fighter/Champion”), pp. 83–100 (“Character Origins,” “Feats,” and “Equipment”), pp. 176–191 (“Rules Glossary”), p. 202 (“Combat Encounters”), and p. 259 (“Animated Armor”). P0-06 must narrow these to entry/field locators; it may not substitute original provenance for a mechanic.

### Unsupported in this slice

Spells, spellcasting, magic items, character creation/advancement, multiclassing, rests chosen during the timed adventure, additional weapons/armor/tools, mounted/vehicle/aerial/underwater combat, exact-grid positioning, environmental or falling damage, crafting, shopping, hirelings, allies or summons, extra monsters, reinforcements, improvised damage/effects, PvP, AI party members, and any rule/content not listed above are unsupported. Purely expressive narration is allowed only when it creates no authoritative fact or mechanical advantage.

For ambiguity, the Guide asks one neutral clarification when interpretations would change actor, target, rule, cost, visibility, or consequence. An out-of-envelope intent is acknowledged plainly, consumes no action/resource, changes no state, and receives nearby supported alternatives. The Guide cannot silently remap it or invent a mechanic.

### Deterministic, ruling, and correction boundary

- **Deterministic:** all listed SRD mechanics, character/monster values, inventory/resources, zone transitions, random results, state changes, and authored branch predicates are validated and event-backed. Narration has no authority.
- **Bounded pre-roll ruling:** P0-07 may define a closed schema for contextual feasibility or approach selection, but it cannot add a rule, effect, condition, item, creature ability, or branch. All authoritative inputs are committed before randomness; only their reveal timing may vary under the accepted visibility policy.
- **Unsupported/clarify:** behavior is fixed above; capped retry/fallback details belong to P0-07/P0-12.
- **Correction/dispute:** a dispute pauses dependent resolution and exposes the committed record as visibility permits. Invalid system events receive visible compensation or a preserved fork, never a silent edit. A discretionary solo rewind needs Rin’s player’s explicit consent, identifies the checkpoint, preserves the abandoned branch, and never selects a preferred reroll. A valid unfavorable roll is not an error. Safety pause/stop is not a rewind.

## Appendix D — Safety, accessibility, data, and evidence gates

### Safety and accessibility

The alpha is invite-only and adults-only with a Teen/PG-13 ceiling: ordinary fantasy violence and mild horror are allowed; explicit sexual content, sexual violence, hate-based targeting, encouragement of self-harm, and graphic torture/gore are excluded. Lines, veils, and phobias are set before play. The keyboard- and screen-reader-operable out-of-band controls bypass the model. **Pause** immediately halts generation, timers, rolls, and state progression; **Stop** does the same and offers session exit; **Report** invoked during active play automatically pauses before collecting the minimum issue details, while a post-session report cannot alter completed state. Resume always requires an explicit player action, and no reason is required.

Prompts, choices, free-text input, state, objective, zones, errors, rules/ruling trace, dice audit, corrections, and safety controls must work by keyboard and screen reader; meaning cannot depend on color, a pointer, a map, audio, or voice.

### Local-first data posture

Canonical events and exact narration remain local until export or deletion. **Delete session** must remove every product-controlled local copy and derivative—events, narration, snapshots, indexes, summaries, caches, and queued diagnostics—not merely hide it from the interface. User-created exports are separate copies and are not silently deleted. P0-10 must document and minimize unavoidable OS temporary files, provider handling, crash residue, and any backup lifecycle, including what the product cannot erase immediately. Central telemetry is privacy-safe metadata only, contains no raw prompt/backstory/role-play/narrative, and is retained 30 days.

### Precommitted Phase 2 measures

- At least 80% of at least 10 representative players finish in 60–90 minutes without developer rescue or softlock; at least 70% would voluntarily replay; median fun and fairness/trust are each ≥4/5.
- All required scenes and success/failure/recovery routes are reachable and directly tested; unsupported intents fail safely; every declared mechanic has an SRD locator and automated test; original content identifiers have approved provenance.
- Across at least 10,000 generated state transitions: zero invariant/replay mismatch. Across fixed release corpora: zero illegal mutation, visibility disclosure, disallowed-content success, or stop bypass.
- **Model tool-call denominator:** of every model tool call in the fixed evaluation set, ≥95% is valid on the first attempt, ≥99.5% is valid after at most one retry, and <1% ends in deterministic fallback. Do not substitute proposals, turns, or sessions as the denominator.
- **Provisional planning targets:** time to first meaningful content p50 ≤2 s and p95 ≤5 s, complete resolution p95 ≤10 s; projected three-hour text-session inference spend p50 <$1 and p95 <$2. **Both latency and cost figures are provisional** until complete multi-call logical-turn evidence finalizes or replaces them with explicit owner acceptance at P1B-05.
- P0-14 must predeclare how legitimately safety-stopped sessions are censored or excluded from completion-time/completion-rate denominators and how they are separately analyzed and reported. They are neither softlocks nor silent omissions, and safety outcomes remain in the safety evidence set.

## Appendix E — Explicit non-goals and evidence dependencies

This slice does not prove multiplayer/networking, hosted authority, AI party members, character creation/advancement, campaign memory, broad SRD coverage, homebrew, additional adventures or personas, secret dynamic difficulty, a tactical grid/general VTT, voice, public/minor access, higher-intensity content, published-adventure import, final branding, any provider/model, or any implementation technology.

Downstream work must refine this accepted baseline without replacing it silently:

- **P0-05:** run at least three facilitated versions, validate timing/agency/clarity/safety and every route, and recommend evidence-linked revisions.
- **P0-06:** trace and freeze every listed mechanic, value, item, feature, monster field, condition, spatial rule, and explicit exclusion; it does not choose a new build or encounter.
- **P0-07:** fix ruling schemas, exact check/DC authoring, hidden-fact and DC reveal timing, validators, and fallback while preserving pre-roll commitment. P0-05’s current participant-visible DC convention is permitted only as a prototype convention and is not acceptance of the Phase 2 reveal policy.
- **P0-08:** author final prose/dialogue and the provenance ledger for the accepted original graph.
- **P0-10:** validate visibility, deletion, provider, temporary/backup, stop-path, and hostile-input boundaries.
- **P0-14:** predeclare recruitment, consent, rescue/softlock rules, safety-stop statistical handling, and scoring before Phase 2 results.
- **P0-15/P0-16:** accept the relevant ADRs and baseline contracts before implementation.

The owner accepted the playable-clock boundary, named scenario/build, and exact envelope through the three core checkboxes on 2026-09-18, then accepted Amendment 01's deterministic refinements on 2026-09-23. This base specification and Amendment 01 must be read together, with Amendment 01 controlling any conflict. Any later change to duration, solo scope, character level/count, persona, pillar mix, combat roster/count, endings, fairness, age/content ceiling, local-first data posture, or an Amendment 01 value is an explicit owner decision change.
