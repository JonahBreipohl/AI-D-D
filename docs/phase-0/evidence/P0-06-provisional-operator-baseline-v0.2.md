# P0-06 provisional operator baseline v0.2

> **STATUS: DRY-RUN INPUT ONLY — NOT FIELDING AUTHORIZATION.** This is a `SPEC_ONLY / NOT IMPLEMENTED` transcription of the accepted research contract. It records no participant evidence, does not complete P0-06, does not clear the P0-04/P0-05 human preflight, and authorizes no recruitment, human session, G0, or production work.

Version: **0.2**, 2026-09-23  
Scenario: *The Signal at Glasswater Weir*  
Controlling contract: [accepted P0-03](P0-03-vertical-slice-spec.md) plus [accepted Amendment 01](P0-03-amendment-01-proposed.md); Amendment 01 controls conflicts.  
Coverage source: [provisional P0-06 matrix](P0-06-coverage-matrix.md)  
Rules source: pinned SRD 5.2.1, SHA-256 `8974902d109d6e63672d7c490bde9ccf052410503d9cfa768237154fbc5e3d87`.
Advisory review: **Independent Amendment crosswalk and deterministic combat-state audits passed 2026-09-23 after repair; this is not human rules review, operational dry-run approval, or fielding authorization.**

## 1. Use and authority

This sheet is the exact operator subset required to dry-run P0-05. The rules/dice operator may execute only an entry below. The Wizard may vary presentation, never facts, mechanics, visibility, a committed consequence, dice, or state. A blank, mismatch, unrepresented state, or consequential ambiguity is a **stop**, not permission to improvise.

Order of authority:

1. PAUSE, STOP, REPORT, boundary, consent, privacy, and safety procedures halt play when invoked.
2. Accepted P0-03 plus Amendment 01 controls scenario and mechanics; Amendment 01 wins conflicts.
3. This sheet is a transcription for operation. If it conflicts with the contract, stop and repair the sheet between dry runs.
4. Narration and facilitator judgment have no state authority.

Every consequential resolution follows: **validate intent and state → select an admitted lane → write the complete public commitment → expose it → roll visibly if required → apply state → append the event → narrate the applied result**. No field changes after randomness.

Dice ownership is fixed: the participant rolls every die attributed to Rin (checks, saves, attacks, damage, healing, feature dice, Advantage/Disadvantage pairs, and rerolls); the rules/dice operator rolls every Watcher die (attacks, damage, and saves). The Watcher has no Initiative die. With an accessible independent digital roller, “ownership” means who explicitly initiates the roll attributed to that actor. Record roller, actor, ordered raw dice, and kept die.

## 2. Start-state assertions

Before the opening prompt, assert and record:

| Field | Exact value |
|---|---|
| Character | Rin Alder; Medium Human Soldier; Fighter 3 (Champion); 900 XP |
| Abilities | Str 17 (+3), Dex 14 (+2), Con 14 (+2), Int 8 (-1), Wis 12 (+1), Cha 10 (+0) |
| Defenses | AC 17; HP 28/28; 3d10 Hit Dice; PB +2; Speed 30 ft.; Passive Perception 13 |
| Initiative | Rin `+2` with Advantage; Watcher static score `12`; Rin wins a total-12 tie |
| Saves | Str +5, Dex +2, Con +4, Int -1, Wis +1, Cha +0 |
| Skills | Athletics +5 with Advantage; Acrobatics +2; Deception +0; Insight +3; Intimidation +2; Investigation +1; Perception +3; Persuasion +2; Stealth +4 with Chain Mail Disadvantage; Survival +3 |
| Languages | Rin: Common, Goblin, Dwarvish; Nera Pell and Tovin Ash: Common |
| Resources | Heroic Inspiration 1; Second Wind 2; Action Surge 1; Savage Attacker available; Tactical Mind available when its trigger permits |
| Attacks | Greatsword +5, `2d6+3` Slashing, Graze; Flail +5, `1d8+3` Bludgeoning, Sap; four Javelins +5, `1d6+3` Piercing, Thrown 30/120, Slow |
| Inventory | Chain Mail; Greatsword; Flail; Javelin x4; Backpack; Crowbar; Rope; Grappling Hook; Torch; Tinderbox; Waterskin; Traveler's Clothes; Dice Set; 58 GP, 1 SP, 9 CP |
| Scenario flags | `arrival=unset`; `service_key=no`; `route_sketch=no`; `red_pennant=no`; `lens_secured=no`; all checks unused |
| Controls | No pause/stop/report/boundary state active; no real session may use this line until the human preflight is separately GO |

Stealth proficiency remains visible sheet data, but **no Stealth check and no Hide action exist in this slice**. Quiet movement may be narrated only when it creates no fact or mechanical benefit.

## 3. Fixed social and exploration checks

All non-hidden fields below, including exact DC and consequences, are public before the roll for this P0-05 prototype.

| ID | Trigger and action | Roll | Success | Failure / limit |
|---|---|---|---|---|
| `SOC-N-INSIGHT` | Before Nera's asset request, Search her concern | Wis (Insight) `+3`, DC 12 | Reveal: log storm damage without blaming her; directly address it and she becomes Willing | Concern not learned; no repeat |
| `SOC-N-INF` | Ask Nera for Service Key while not Willing | Cha (Deception `+0`, Intimidation `+2`, or Persuasion `+2`), DC 15 | Gain Service Key | No key; public route remains known; at most one attempt |
| `SOC-T-INSIGHT` | Before Tovin's asset request, Search his concern | Wis (Insight) `+3`, DC 12 | Reveal: document his warning; directly address it and he becomes Willing | Concern not learned; no repeat |
| `SOC-T-INF` | Ask Tovin for assets while not Willing | Cha (Deception `+0`, Intimidation `+2`, or Persuasion `+2`), DC 15 | Gain Route Sketch **and** Red Pennant atomically | Neither asset; at most one attempt |
| `SOC-T-DICE` | Play one open dice game instead of another successful Tovin grant | Wis with Dice Set proficiency `+3`, DC 20 | Gain Route Sketch **and** Red Pennant atomically | Neither; no replay |
| `EXP-CLUE` | Resolve facts missing after asset state is known | One DC 12 Search/Study using Perception `+3`, Survival `+3`, or Investigation `+1`, chosen to match declared method | Reveal every missing route/lens fact without delay | Reveal the same missing facts after delay; set `arrival=late`; exactly one check when required |
| `EXP-TRAVERSE` | Recover and secure the lens, then reach tower | Str (Athletics) `+5` with its existing Advantage; or Dex (Acrobatics) `+2`; or Rope-tied Grappling Hook Dex (Acrobatics) `+2`, DC 13 | Preserve current arrival state | Set `arrival=late`; slower safe route; exactly one check |

Asset and arrival algorithm:

1. On entry to Broken Sluice set `arrival=on_time` exactly once. Social duration and asset outcomes never set `late`.
2. Key + Sketch skips `EXP-CLUE`. Key only: the check reveals lens location. Sketch only: it reveals the usable public access route without creating a key. Neither: one combined check reveals both missing facts without creating either asset.
3. `EXP-CLUE` failure and `EXP-TRAVERSE` failure may set `late`; `late` is irreversible.
4. Run exactly one `EXP-TRAVERSE`. The lens is recovered and secured before combat.
5. Crowbar grants only its printed Advantage when leverage is used for the Athletics traversal. Rope plus Grappling Hook enables the hook check; rope alone grants no bonus.

## 4. Item-use allowlist

Only these mechanical uses exist:

- Chain Mail fixes AC 17 and Stealth Disadvantage.
- Greatsword, Flail, and the four individually tracked Javelins make the attacks above and apply Graze, Sap, and Slow respectively.
- Dice Set is used only for `SOC-T-DICE`.
- Crowbar is used only to grant its printed Advantage when leverage applies to the Athletics traversal; it does not stack with Rin's existing Advantage. Rope + Grappling Hook is used only for the hook traversal: tie the rope, use the Utilize action to throw at the authored catch within 50 ft., and make the fixed DC 13 Dexterity (Acrobatics) check. Success catches and permits the authored climb; failure does not attach and instead opens the slow safe route. Rope alone gives no bonus.
- Service Key, Route Sketch, Red Pennant, and secured lens perform only their authored branch functions.
- Torch/Tinderbox may be lit or extinguished only as effect-free **exploration** narration. During combat that use is unsupported. They never change light, sight, checks, attacks, damage, or range.
- Backpack, Waterskin, clothes, and coins are display-only.

All capacity, encumbrance, dehydration, spending, transfer, restraint/binding, destruction, fire/damage, improvised or other printed uses are unsupported. A thrown Javelin leaves carried inventory and is placed in the target's zone; combat recovery is unsupported.

## 5. Dark Lantern start card

Combat path: `tower exit --20 ft.-- Entry Deck --20 ft.-- Gear Floor --20 ft.-- Lens Dais`. The tower exit is a terminal boundary, not a combat zone. No other edge exists.

Initial authoritative state:

- Rin: Entry Deck; Watcher: Lens Dais; two edges / 40 ft. apart; both disengaged and mutually visible; no Surprise.
- Both begin with their normal turn economy unspent and Reaction available. The Watcher's Reaction thereafter refreshes only at the start of its turn.
- All zones have adequate light, clear line of sight, and no cover, Darkness, Dim Light, obscured, hidden, or invisible state. Fog/darkness prose is narrative only. Blindsight gives no special advantage here.
- Rin holds the Greatsword in one hand, other hand free. Everything else, including lens and scenario assets, is secured/stowed.
- Exactly one Watcher exists; there is no reinforcement, hazard, wall effect, ally, or live difficulty adjustment.
- Read verbatim after positions and before Initiative: **“The Watcher Harness is under a maintenance order to knock intruders unconscious rather than kill them.”** Record `operating_order_visible=yes`. Initiative is locked until that value exists.
- Record Watcher score 12 before Rin rolls two d20s with Advantage and adds +2. Rin acts first on total 12. Freeze the order.
- Record `combat_started=yes` only after the order and both values are committed and the first turn begins.

## 6. Zones, distance, movement, and engagement

| State | Exact operation |
|---|---|
| Adjacent zones | 20 ft.; crossing costs 20 ft. Two edges are 40 ft. No skipped or partial edge, and unused movement is not banked. |
| Same zone | Pair is disengaged at 10 ft. or engaged at 5 ft. Changing either way costs 5 ft. |
| Enter occupied zone | Arrive disengaged; pay a further 5 ft. to engage. |
| Melee / Unarmed | Requires engagement. |
| Javelin | Normal at 5/10/20 ft.; long range with Disadvantage at 40 ft.; ordinary within-5-ft. ranged Disadvantage when engaged; beyond 120 ft. impossible in this graph. |
| Shove push | A 5-ft. push changes engaged to same-zone disengaged; no wall, edge, fall, or hazard effect. |
| Opportunity Attack | Voluntarily leaving engagement triggers immediately before the first 5 ft.; Disengage, OA-free movement, forced movement, or spent Reaction prevents it. |
| Grappled | Speed 0; pair remains engaged. Dragging the same-size target makes each foot cost one extra: edge 40 ft., engagement step 10 ft. |
| Prone | Standing costs half current Speed, rounded down for Watcher policy; crawling uses applicable extra movement. |
| Dash | Spends the action and adds one current-Speed allotment to this turn's movement cap. Track it with the movement formula below. |
| Slow on Watcher | On a damaging Javelin hit, Rin may apply Speed 25 → 15 until start of Rin's next turn; never stacks beyond -10. For this full-disclosure prototype, the yes/no mastery choice is written before the attack roll. |
| Remarkable Athlete | Immediately after Rin's Critical Hit, optional movement up to 15 ft. without OA; may change engagement but cannot cross a 20-ft. edge. |
| Ready | Use the full Ready card in section 8. Trigger must be a visible state/event; range and legality are checked immediately after it finishes; the Reaction fully resolves before interrupted behavior is re-evaluated. |

Movement ledger and mid-turn Speed changes:

- Track `movement_cost_spent` in movement feet, including stand, crawl, drag, edge, and engagement costs, plus `dash_actions_this_turn`.
- At every state boundary, `movement_cap = current Speed × (1 + dash_actions_this_turn)` and `remaining movement = max(0, movement_cap - movement_cost_spent)`. Never undo distance already crossed or restore a spent action.
- Recompute immediately when Speed changes or Grappled begins/ends. Example: the Watcher Dashes, spends 20 ft., then a readied damaging Javelin applies Slow; its cap becomes `15 × 2 = 30`, so 10 ft. remains.
- Remarkable Athlete's immediate movement is a separate maximum-15-ft. grant: it does not spend or replenish the normal ledger, cannot be banked, cannot cross an edge, and provokes no OA.
- Readied movement is likewise a separate Reaction payload up to the actor's current Speed; apply all zone/crawl/drag costs and do not merge it with the actor's normal-turn ledger.

## 7. Hands and weapon state

- Greatsword needs two hands only to attack. Adding or releasing the free support hand costs no action or equip interaction.
- Flail, Javelin, and Torch occupy one hand. Grapple requires and then occupies one free hand. Shove and Unarmed damage do not.
- Greatsword attack is illegal while the other hand holds an item or maintains a Grapple.
- Rin may release a Grapple at any time with no action. Apply release at the next atomic event boundary (before or after a complete 5/20-ft. movement transaction, before an attack is committed, or after an attack/event fully resolves; safety controls still halt immediately). Release frees Rin's occupied hand, ends Grappled, and restores the Watcher's current Speed. Recompute movement immediately, but schedule Watcher policy re-evaluation under the event-stack rule in section 10.
- The accepted Attack equip/unequip interaction covers one draw, stow, pick up, or drop; no free multi-item swap. Track every stowed, dropped, or thrown location.
- Action Surge grants an additional action, not extra free equip interactions beyond the admitted action rules. A terminal result cancels remaining attacks/actions.

## 8. Rin combat reference

Admitted combat actions: Attack, Dash, Disengage, Dodge, Ready, Search, Study, and Utilize; movement; Greatsword, Flail, Javelin, and Unarmed Strike (damage, Grapple, Shove); Second Wind; Action Surge; supported inspection/dispute/correction and controls. Help, Hide, Influence, Magic, rest completion, improvised attacks/effects, other equipment benefits, and all unlisted actions are unsupported.

Turn economy: at the start of its own turn, each actor receives its normal movement allotment, one action, at most one Bonus Action, and refreshes its Reaction. Spending a Reaction makes it unavailable until the start of that actor's next turn. Action Surge is the sole admitted extra-action exception. Incapacitated prevents actions, Bonus Actions, and Reactions; a terminal state prevents all further economy. Reset per-turn trackers, including Savage Attacker, at the start of each new actor turn while preserving round/session resources.

| Combat action | Exact operator card |
|---|---|
| Attack | Spend the action to make exactly one fixed-weapon attack or one Unarmed Strike; Fighter 3 has no Extra Attack. The attack may include exactly one admitted equip/unequip interaction and must satisfy the hand/location rules before commitment. Action Surge can fund a second, separate Attack action on Rin's turn; it never adds an attack to the first action. |
| Dash | Spend the action; increment `dash_actions_this_turn`; recompute the movement ledger in section 6. Action Surge can fund a second Dash for Rin. |
| Disengage | Spend the action; Rin's movement does not provoke Opportunity Attacks for the rest of the current turn. It does not move Rin by itself. |
| Dodge | Spend the action. Until the start of Rin's next turn, the visible Watcher's attacks have Disadvantage and Rin has Advantage on Dexterity saves. End the benefit immediately if Rin becomes Incapacitated or Speed 0. |
| Ready | Spend the action on Rin's turn. Write one visible state/event trigger plus either one exact admitted action or movement up to Rin's current Speed. Before the start of Rin's next turn, after the trigger fully finishes, Rin may spend the Reaction to execute the payload or ignore the trigger. Check target, range, hands, resources, and legality at that moment. The payload expires at the start of Rin's next turn; a Reaction spent on Ready is unavailable for OA and vice versa. Readied spells are unsupported. |
| Search | Spend the action only after disclosing that Dark Lantern contains no concealed creature/object or hidden/invisible state. If Rin confirms, resolve automatically with no roll, new fact, or state change and show the existing public scene/state. Attempts to create a secret target or advantage are unsupported. |
| Study | Spend the action only after disclosing that no additional combat lore, weakness, clue, trap, riddle, or gadgetry result is authored. If Rin confirms, resolve automatically with no roll, new fact, or state change and show the existing public scene/state. Rules explanations and public-state inspection remain free player controls. |
| Utilize | Requires an allowlisted combat-eligible object use. This slice has none: weapons use Attack; Torch/Tinderbox is exploration-only; traversal/assets have no combat function. Reject an attempted combat Utilize before action consumption and offer the relevant supported action when one exists. |

| Mechanic | Exact operator rule |
|---|---|
| Improved Critical | Rin's weapon and Unarmed attack rolls crit on 19–20. |
| Greatsword / Graze | Hit `2d6+3`; crit `4d6+3`. Rin may choose Graze in the written pre-roll commitment; if chosen, a miss deals exactly 3 Slashing. It is not a hit and triggers no critical/Savage effect. |
| Flail / Sap | Hit `1d8+3`; crit `2d8+3`. Sap gives the Watcher Disadvantage on its next attack roll before start of Rin's next turn; consume on that roll, refresh but do not stack. |
| Javelin / Slow | Melee while engaged or Thrown 30/120; hit `1d6+3`, crit `2d6+3`. A melee Javelin remains held and can make a qualifying nonlethal final blow. A thrown Javelin leaves hand/carried inventory when thrown and lands in the target's zone on hit or miss; combat recovery is unsupported. Rin may choose Slow in the written pre-roll commitment for either mode; if chosen, a damaging hit applies the nonstacking Speed reduction and immediately recomputes movement. |
| Unarmed damage | +5 to hit while engaged; 4 Bludgeoning; eligible for Improved Critical but has no damage die to double. |
| Grapple / Shove | Save DC 13; Watcher always selects Str save +2. Grapple needs/occupies a free hand. Shove either applies Prone or the 5-ft. state change. |
| Rin's Opportunity Attack | If the visible Watcher voluntarily leaves engagement and Rin's Reaction is available, resolve immediately before its first 5 ft.: one melee attack with a currently held legal weapon or one Unarmed Strike, never an Attack action or multiple attacks. Rin may add the free support hand to the already-held Greatsword at no cost but cannot draw/stow as part of the OA. Spend Reaction; if nonterminal, resume the provoking movement and re-evaluate through the event stack. |
| Rin's nonlethal final blow | When Rin's qualifying melee attack would reduce the Watcher to 0 HP, the player may choose the pinned knockout option: set Watcher to 1 HP, apply the full Unconscious state, begin but do not complete a Short Rest, and end combat as victory. A thrown Javelin at range cannot use this option. |
| Savage Attacker | Once per turn after a weapon hit, Rin may choose to roll the weapon damage dice twice and use either roll; mark it spent for the current turn only when chosen. It can be available again on the Watcher's turn for Rin's OA or readied weapon hit. Apply critical dice as the weapon dice pool. |
| Heroic Inspiration | Start 1, maximum 1. Immediately after the participant rolls a Rin-owned die, Rin may expend it to reroll that die and must use the new result; with Advantage/Disadvantage reroll only one selected die. It cannot reroll a Watcher-owned attack, damage, or save die. Record original, selected die, replacement, and expenditure before applying the result. |
| Tactical Mind | After a failed ability check, Rin may choose to roll `1d10` and add it to the check, provisionally using one Second Wind use; the use is expended only if this changes failure to success, otherwise it is refunded. |
| Second Wind | Bonus Action; expend one of 2 uses; heal `1d10+3`, maximum 28. |
| Action Surge | On Rin's turn only, Rin may choose to immediately consume the one use to gain one additional action except Magic; unavailable during a Ready reaction or OA and no recharge during timed play. |

## 9. Watcher Harness complete operator card

Use one unchanged SRD Animated Armor stat block, reskinned only in fiction:

| Field | Value |
|---|---|
| Type / size / alignment | Medium Construct; Unaligned |
| AC / HP / Speed | AC 18; HP 33; Speed 25 ft. |
| Abilities | Str 14 (+2), Dex 11 (+0), Con 13 (+1), Int 1 (-5), Wis 3 (-4), Cha 1 (-5) |
| Initiative | Static score 12; modifier stored as +2 but never rolled in this encounter |
| Senses | Blindsight 60 ft.; Passive Perception 6; environment makes this non-advantageous |
| Immunities | Poison and Psychic damage; Charmed, Deafened, Exhaustion, Frightened, Paralyzed, Petrified, Poisoned |
| Languages | Understands no language; cannot speak |
| CR / XP / PB | CR 1; 200 XP; PB +2 |
| Traits / gear / special speeds | None listed in the pinned SRD 5.2.1 entry. Legacy-version Antimagic Susceptibility and False Appearance are absent and unsupported; do not import them. |
| Multiattack | On its action, exactly two separate Slams when the tactics branch permits; fully resolve each and stop on terminal state |
| Slam | +4 to hit; engaged 5-ft. reach; one target; visible `1d6+2` Bludgeoning; critical `2d6+2`; static 5 never used |
| Opportunity Attack | Bounded project ruling `AM01-R1`: exactly one Slam, never Multiattack; Reaction consumed; resolve before movement |
| Nonlethal order | Every Slam/OA that would reduce Rin to 0 instead leaves Rin at 1 HP; atomically applies Unconscious, including Incapacitated, Prone, Speed 0, dropped held items, unaware, Advantage to attacks, automatic Str/Dex save failure, and 5-ft. hit criticality; begins (but does not complete) a Short Rest; stops further attacks; and produces the failure ending |

## 10. Deterministic Watcher algorithm

The Watcher targets only Rin and never retreats. At the start of its turn refresh its Reaction, then:

1. If terminal or Incapacitated, do nothing.
2. If Prone and remaining movement is at least half current Speed rounded down, spend that amount to stand. Otherwise remain Prone and continue the applicable branch. Speed 0 cannot stand.
3. If engaged, spend the action on Multiattack: make exactly two Slams against Rin, each resolved separately, stopping immediately on a terminal result. A later Ready interruption can forfeit a remaining Slam only when the accepted re-evaluation rule makes that Slam illegal.
4. Otherwise follow the unique shortest path toward Rin. If remaining normal movement reaches engagement, move/engage and Multiattack.
5. Otherwise Dash and cross as many complete edges as possible. After crossing, engage only if in Rin's zone with at least 5 ft. remaining. No attack follows Dash.

While Grappled, never escape; attack Rin if possible. Against Grapple/Shove always use Str +2. Never Dodge, Disengage, Ready, Search, Study, Utilize, Grapple, or Shove. Take the first legal OA when Reaction is available; never spend Reaction otherwise. Refresh Reaction only at start of its turn.

During the Watcher's current turn, after **any** authoritative mid-turn state change that can affect its policy or legality—including a Ready payload, Grapple release, position, engagement, Speed/movement effect, hand/resource change, condition, HP, or terminal state—fully resolve the atomic event, including any OA at its normal interrupt point, recompute movement under section 6, and re-evaluate without restoring spent movement, action, Reaction, or Slams. Re-evaluation occurs at the atomic boundaries defined in section 7; never split a die roll or state application. An off-turn change is recorded immediately but never invokes Watcher policy off turn; it is first considered by step 1 at the start of the Watcher's next turn.

Event-stack rule: a Ready payload, OA, attack, or movement transaction is an enclosing atomic payload. State changes inside it apply immediately to that payload's legality and state. During the Watcher's turn only, they queue Watcher **policy** re-evaluation until the outermost payload fully resolves; off turn, they never execute Watcher policy. A nested OA resolves at its normal interrupt point and then returns to the enclosing payload. A terminal result interrupts and cancels every remaining payload immediately. Example: if Rin releases a Prone+Grappled Watcher after a Ready trigger during the Watcher's turn and before committing the readied Greatsword attack, release immediately frees the second hand, but the Watcher remains Prone for that readied attack; after the full Ready reaction resolves, a nonterminal Watcher re-evaluates and may stand using remaining movement.

- action unspent: resume the same priority algorithm from step 1;
- Multiattack begun: recheck terminal state, then the Prone stand rule and engagement using only remaining movement; use only remaining Slams and forfeit any one that cannot legally re-engage; never grant a new action or replace an already resolved Slam;
- Dash begun: recheck terminal state and the Prone stand rule, then use only recomputed remaining Dash movement along the same shortest path; no attack.

If a state has no exact result under these rules, stop the prototype.

## 11. Conditions, attack order, and terminal handling

- Apply Advantage and Disadvantage once each; if both exist they cancel, regardless of count.
- Attack order: commit actor/target/weapon, legality/range/hands, AC, modifier, Advantage state, resource/mastery choices, possible hit/miss/critical effects → roll → determine hit/critical → roll/apply damage/effect → test terminal state → append → narrate.
- Grappled: Speed 0; conditions above; ends on separation, Incapacitated grappler, admitted escape, or the grappler's release at any time with no action. Rin's release frees the occupied hand and invokes immediate movement recomputation; Watcher policy re-evaluation follows the event stack only during the Watcher's turn, while an off-turn release is first considered at the Watcher's next turn start. Watcher never attempts escape.
- Prone: standing/movement as above; own attacks Disadvantage; attacks from engaged 5 ft. have Advantage, attacks farther away Disadvantage.
- Unconscious includes Incapacitated and Prone: cannot act or take reactions; Speed 0; drop held items; unaware; attacks have Advantage; Str/Dex saves fail automatically; an attack hit from engaged 5 ft. is Critical. The mandatory knockout **of Rin** and an optional qualifying melee knockout of the Watcher are immediately terminal, so no additional attack, death save, completed rest, or recovery occurs.
- Bloodied is display-only at half HP or less and creates no rule effect.
- Watcher damage immunity is applied before HP change. HP stays within 0..maximum. No post-terminal mutation.

## 12. Retreat and combat classification

Rin may declare a retreat goal on a conscious turn at no action cost. It is not terminal until lawful movement crosses the tower-exit boundary 20 ft. beyond Entry Deck.

- Leaving engagement first costs 5 ft. and may trigger OA; Disengage suppresses it.
- Rin cannot cross while Grappling the Watcher and must release first.
- If the final OA causes mandatory knockout, record knockout, not retreat.
- If Rin survives and crosses, immediately emit `retreat`, end combat, apply failure; the Watcher does not pursue or cross.
- Leaving before `combat_started` is a participant stop, not retreat.
- `exactly_one_combat_played=yes` only after both actors have begun a turn, or earlier when a valid attack/damage/condition sequence reaches a terminal combat result.
- An immediate first-turn retreat may be a valid in-fiction failure, but records `exactly_one_combat_played=no` and cannot enter P0-05's three-completion denominator.
- A later retreat counts only if all other criteria also hold: natural social and exploration play, accepted ending, 60–90 gameplay minutes, core debrief, and no disqualifying protocol/rescue issue. Never coach continued combat to obtain a denominator.

## 13. Outcome truth table

Evaluate in priority order after state is applied:

| Priority | Predicate | Classification | Consequence |
|---:|---|---|---|
| 1 | Safety/control procedure ends session | `safety-ended` | No in-fiction ending |
| 2 | Watcher defeated and `arrival=on_time` | `success` | Beacon guides ferry through |
| 3 | Watcher defeated, `arrival=late`, `red_pennant=yes` | `recovery` | Ferry anchors safely; delivery delayed |
| 4 | Watcher defeated, `arrival=late`, `red_pennant=no` | `failure` | Ferry turns back safely; supplies delayed |
| 5 | Valid retreat boundary crossing | `failure` | Ferry turns back safely; supplies delayed |
| 6 | Mandatory Watcher knockout | `failure` | Ferry turns back safely; supplies delayed |

Zero or multiple applicable in-fiction outcomes is a contract defect: stop; do not select one.

## 14. Unsupported and clarification rule

Ask one neutral clarification only when actor, target, rule, cost, visibility, or consequence would differ. If still outside the admitted set, state: “I understand that your goal is **[goal]**. This prototype does not support **[specific mechanic]**. You can **[supported option]**, or describe the goal another way.” The request consumes no action/resource and changes no state. Never silently remap it. Purely expressive narration is allowed only when it creates no authoritative fact or advantage.

Unsupported includes every unlisted SRD rule/content field, spells/magic, extra creatures, exact grid, cover/terrain/hazards/falling, additional items or item benefits, Stealth/Hide, improvised damage/effects, torch attack, rest completion, shopping/crafting/encumbrance, allies/summons/PvP, surrender, Watcher tactics not listed, and any alternative route or ending.

## 15. Minimum dry-run assertions

The version-matched independent dry run must pass at least:

- all four Key/Sketch combinations, atomic Tovin assets, monotonic arrival, one clue check when required, and exactly one traversal;
- every fixed check at below/equal/above DC, resource interaction, and failure-forward transition;
- every item allowlist positive case and one no-consumption rejection per excluded category;
- Initiative below/equal/above 12, no Watcher Initiative die, exact public operating-order lock;
- all 5/10/20/40-ft. range states; edge/engagement movement under normal, Dash, Slow, Prone, Grappled drag, Shove, Ready, and Remarkable Athlete;
- exhaustive hand states, equip interaction, Grapple, Action Surge, dropped/thrown locations;
- Watcher cards for engaged, same-zone disengaged, adjacent, two-edge, Slowed, Prone with sufficient/insufficient movement, Grappled, Prone+Grappled, spent Reaction, Ready interruption before/within Multiattack and Dash, and terminal state;
- normal/critical/two-Slam damage, Sap/Slow/Graze, OA `AM01-R1`, mandatory knockout, and no post-terminal attack;
- retreat with engagement/OA/Disengage/knockout priority, immediate-retreat exclusion, no pursuit, every outcome, and safety-ended separation;
- every unsupported category, missing-field stop, state-before-narration, immutable commitment, and append-only correction trace.

Passing these assertions does not itself authorize participants.

## 16. Stop conditions and sign-off boundary

Stop before or during any dry run when a required value is missing or contradictory, an action/state is unrepresented, the commitment was not exposed before randomness, hidden information is mishandled, state changed before validation or after a halt, the operator would need to improvise, or the frozen version does not match the manifest.

Before human fielding, this baseline still requires named P0-06 owner and independent rules-reviewer sign-off, a version-matched dry-run evidence ID, incorporation into the frozen P0-05 manifest, and every human preflight/fielding requirement. AI/Codex output is not a human approval, live check, or operational result.

```text
Baseline version: 0.2
P0-06 owner (named human): [OPEN]
Independent rules reviewer (named human): [OPEN]
Review date / evidence ID: [OPEN]
Version-matched dry-run ID/result: [OPEN]
Disposition: NOT REVIEWED / DRY-RUN BLOCKED / DRY-RUN PASSED
Human fielding authorization: NONE — separate preflight required
```
