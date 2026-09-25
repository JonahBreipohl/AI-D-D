# P0-04 — Representative player interview protocol

Status: **Ready to execute after the human research preflight is complete; no interviews are claimed by this document**  
Owner: **A10 — Product research and human playtest lead**  
Dependency: **P0-01 owner decisions plus the completed human research/privacy preflight; P0-03 may run in parallel**  
Decision context: **Private, invite-only, unpaid, adults-only alpha operated initially in California, United States**  
Minimum evidence: **Five completed interviews with eligible participants**
Review: **Independent planning-coherence audit passed 2026-09-18; human preflight and real evidence remain required**

## Purpose and limits

This protocol tests whether the charter's proposed target user has a meaningful problem and whether the proposed experience addresses it. It covers GM access, trust and fairness, response latency, interface expectations, and willingness to pay. It also captures rules-edition context because the current evidence base does not establish whether the target population prefers the 2014 or revised 2024 rules.

This is exploratory product research, not a statistically representative survey, a sales exercise, or evidence that a product works. Five interviews can reveal important patterns and contradictions; they cannot establish population percentages. No finding is to be reported as a market fact without evidence appropriate to that claim.

## Research questions and falsifiable hypotheses

| Code | Hypothesis to test | Evidence that would support it | Evidence that would challenge it |
|---|---|---|---|
| GA | Lack of a willing or available human game master materially prevents familiar fifth-edition players from playing when they want | Recent, specific attempts to play were cancelled, delayed, or avoided for this reason; existing workarounds are unsatisfactory | Scheduling, group formation, campaign commitment, social preference, or another issue dominates; a substitute GM would not change behavior |
| TR | Players can trust a rules-bounded AI game master when a ruling is immutably committed before a roll and its dice inputs, raw roll, outcome, correction, and audit evidence are inspectable; final Phase 2 reveal timing remains evidence-gated even though P0-05 uses a full-disclosure prototype convention | Participants can explain how the record establishes what was fixed before the result and how they would resolve a dispute under each counterbalanced reveal treatment | Participants reject AI adjudication regardless of auditability, require a human arbiter, cannot distinguish commitment from disclosure, or find either treatment confusing or performative |
| FR | The accepted no-secret-fudging rule, pre-roll commitment, visible mercy, and consent-based discretionary rewinds feel fair | Participants understand and accept the policy in concrete scenarios and can predict what happens | Participants regard the accepted policy as immersion-breaking or unacceptable, or reject the correction model; secret fudging is not offered as an alternative design |
| LT | A streamed text experience can preserve flow within the proposed latency bands | Participants accept the tested waits for the corresponding task and value partial meaningful content | Participants abandon, multitask, or lose confidence at materially shorter waits, or prefer a different interaction model |
| UI | A text-first interface with free text, optional choices, state, rule trace, dice audit, and separate out-of-band pause, stop, and report paths is understandable and useful | Participants correctly prioritize the surfaces and distinguish immediate control from incident/feedback routing | The surfaces create overload, obscure agency, conflate report with pause/stop, or omit a critical need |
| PM | The problem may create enough value to support a future paid offering | Participants already spend money or effort on relevant substitutes and identify a credible purchase context and payer | Interest exists only while free, nobody is a plausible payer, or another free substitute is good enough |
| ED | The selected SRD 5.2.1 baseline is acceptable to the initial target | Participants use or accept revised rules for this use case | Edition preference is strong enough to prevent adoption or creates material group incompatibility |

All hypotheses may be rejected. The interviewer must not defend the concept, teach participants what answer is preferred, or reinterpret contrary evidence as a feature request.

## Recruitment plan

### Eligibility

Each participant must:

- be 18 or older and currently located in California;
- be able to give informed, voluntary consent for this research conversation;
- have played a fifth-edition fantasy tabletop role-playing game enough to understand the roles of player and game master, normally at least three sessions within the last two years;
- have wanted to play, scheduled play, or decided whether to play within the last 12 months; and
- be willing to discuss the experience in English using text or speech, with reasonable accessibility accommodations documented without collecting a diagnosis.

Recruit seven to nine candidates to obtain at least five eligible completions after withdrawals or scheduling failures. Do not recruit only AI enthusiasts, only project friends, or only people who already agree that an AI game master is desirable.

### Minimum segmentation across completed interviews

The minimum five completions must collectively include:

- at least three people who personally experienced a recent cancellation, delay, or inability to play; do not require that they attribute it to GM access during screening;
- at least two primarily-player participants who do not regularly game-master;
- at least one participant who currently or recently game-masters, to expose substitution and trust concerns;
- at least two participants with remote or virtual-tabletop play experience and at least one with mainly in-person experience;
- both participants familiar mainly with 2014-era rules and participants exposed to revised 2024 rules, when recruiting permits; and
- a mix of prior generative-AI experience, including at least one person who has not used an AI game-master tool.

These are behavioral segments, not demographic quotas. Do not collect protected or sensitive demographic data unless a separately reviewed research need requires it. Record a segment as “not obtained” rather than inferring it.

### Exclusions

Exclude:

- anyone under 18 or whose age/location cannot be confirmed by self-attestation;
- project staff, protocol authors, contractors, or anyone with advance knowledge of the intended findings;
- anyone who has not played enough fifth-edition tabletop play to evaluate the stated target problem;
- anyone currently impaired or otherwise unable to consent; and
- anyone who would need to disclose confidential employer, client, medical, legal, or similarly sensitive information to participate.

Prior participation in a separate project activity is not automatically disqualifying, but it must be tagged because concept familiarity can bias answers. No more than two of the minimum five should be close personal contacts of the owner or research lead.

### Screener

Ask only what is needed to determine eligibility and segments:

1. Are you 18 or older and currently located in California?
2. About how many fifth-edition fantasy tabletop sessions have you played in the last two years?
3. In the last 12 months, have you wanted or attempted to play? What happened? Keep the response to one or two sentences at screening.
4. In those sessions, were you mainly a player, mainly a game master, or both?
5. Was your recent play mainly remote, mainly in person, or mixed?
6. Which rules era did your group mainly use, if you know: 2014-era, revised 2024, mixed, or not sure?
7. Have you used a generative-AI game-master or solo role-playing tool before?
8. What accessibility accommodation, if any, would help you participate? Do not request a diagnosis.

Store contact details in a scheduling roster separate from interview notes. The notes use only a study ID such as `P04-01`; this is coded/pseudonymous data, not automatically anonymous data.

## Privacy, consent, and California preflight

The following is an operational research template, **not legal advice**. Before recruitment, the human owner or qualified reviewer must confirm the notice, incentive handling, recording practice, retention period, deletion process, and any California or federal obligations that apply to the actual operator and tools. Do not begin collection while any of those items is undefined.

### Data-minimization rules

- Use a random study ID in every research artifact. Do not place names, email addresses, account handles, exact addresses, employer names, or campaign/member names in notes. Call the resulting records **coded/pseudonymous** until a documented unlinkability review supports a stronger term.
- Explain that unique play histories, phrasing, or short excerpts may still allow the participant or another person to recognize the speaker even after direct identifiers are removed. Do not promise anonymity.
- Give the participant a random deletion token at consent. Keep a restricted token-to-study-ID lookup through the stated deletion-request deadline; the participant can submit the token without restating their interview. If a contact-to-token mapping is retained to support a lost-token process, disclose it, restrict it to the privacy/data owner, and delete it on the stated earlier date.
- Keep the scheduling/contact roster separate and access-restricted. Delete scheduling and incentive fields after those operations and any separately consented follow-up window are complete; retain only the minimum deletion lookup described above through the deletion deadline.
- Take typed coded notes by default. Do not record audio, video, or a full transcript by default.
- If recording is genuinely necessary, obtain separate affirmative consent, name the tool and approved access group, state the exact deletion date, and allow the interview without recording.
- Ask participants not to share real secrets, private messages, or identifying stories. Paraphrase incidental identifiers immediately.
- Set and disclose a specific research-note retention/deletion date, deletion-request deadline, lookup method, backup behavior, and limits on deletion before the first interview. “Until no longer needed” is not sufficient.
- Restrict raw notes and the deletion lookup to the named access groups. Synthesis should prefer aggregated themes and paraphrase. Any short excerpt is coded, not claimed anonymous.
- Give every excerpt an internal evidence ID linked to the study ID through the deletion deadline. Before that deadline, an honored deletion request must remove the source record and linked excerpt from active notes and editable internal reports. The consent notice must state what can and cannot be retracted from already distributed copies or backups. Do not externally distribute a direct excerpt while promising unconditional recall that the team cannot perform.
- After the disclosed deadline and destruction of the lookup, explain that the team may no longer be able to locate a participant's contribution. Record destruction of the lookup; do not continue to imply that later individual deletion is possible.
- A participant may skip a question, pause, withdraw, or request deletion using the deletion token and stated contact path. The team must test the lookup-and-removal procedure before recruitment.

### Plain-language opening consent script

Read this before substantive questions and record `consent: yes/no`, not a signature, unless a qualified reviewer requires another method. Replace every bracket with a reviewed, truthful value:

> We are doing early product research for a possible private, unpaid, adults-only game alpha operated initially in California. This conversation is about your tabletop-playing experience and reactions to a concept; you are not testing a finished product. It should take about 50 minutes. Participation is voluntary. You may skip any question or stop at any time without penalty, and any stated incentive is not dependent on positive answers or finishing every question. We will take coded notes under a study ID and will not intentionally include your name, contact information, or other direct identifiers in those notes. Coded does not mean anonymous: a distinctive story or excerpt could still be recognizable. Please do not share private or sensitive information about yourself or other people. [We are not recording.] The notes will be available only to [approved roles] and deleted or transformed as described by [exact date]. We will give you a deletion token. Until [request deadline], you may use that token to ask [research contact] to locate and remove your source record and linked excerpts from [active notes/editable internal reports]; [truthful limits for backups or already distributed copies]. After that deadline and destruction of the lookup, we may no longer be able to identify your contribution. Short coded excerpts may appear in [internal report audience], subject to those limits. Do you understand this and agree to participate?

If recording is approved, replace the bracketed sentence with a separate explanation and ask a separate yes/no recording question. A “no” to recording must not end otherwise eligible participation.

## Standardized concept card

Do not expose this card until after the recent-behavior and GM-access section. This card intentionally describes commitment without selecting a final reveal policy; section 4 compares the two treatments as research stimuli. Read it exactly once, then answer factual clarification without selling the idea:

> Imagine an invite-only, text-first tool for adults that runs one original 60–90 minute, fifth-edition-compatible solo adventure with a pre-generated character. A “Transparent Guide” narrates and offers optional choices, but deterministic rules—not the narrator—apply game state. The experience commits rulings before rolls and provides dice and audit evidence; this interview will compare two ways of revealing that committed information. It does not secretly change rolls, labels unsupported actions, and provides separate out-of-band pause, stop, and report controls. This is a concept, not a description of a completed product.

### Out-of-band control definitions used in the study

Use these definitions consistently in the concept and interface materials:

- **Pause** immediately halts narration, dice, timers, and state progression, then asks whether and where the participant wants to resume.
- **Stop** immediately halts the experience and ends or exits the session without requiring a reason.
- **Report** opens a human-routed issue/feedback path independent of the narrator. When opened during active play, it automatically pauses before collecting anything; after acknowledgement, the participant chooses whether to resume or stop. A post-session report does not change completed state.

The report mockup collects only an automatically attached coded session/turn ID, one optional issue category, and optional free text. Raw transcript, backstory, contact information, and boundary details are excluded by default. After submission it shows an acknowledgement, the receiving human role, who may access the report, whether follow-up is available, the exact retention/deletion rule, and how the deletion token applies. State clearly that this is not an emergency or clinical-support channel. Before the study, the human owner must fill and approve every operational value; a placeholder report flow is not field-ready.

## Interview guide (target: 50–60 minutes)

The prompts are a guide, not a questionnaire to rush through. Ask for recent examples before opinions, use “tell me more” and “what happened next,” and avoid explaining away criticism.

### 1. Opening and context — 5 minutes

1. Read the consent script and obtain affirmative consent.
2. “To start, tell me about the last tabletop role-playing session you played.”
3. “What role did you have, and what rules era or tools did the group use?”
4. “What makes a session worth the effort for you?”

### 2. Recent behavior and GM access — 10–12 minutes

1. “Tell me about the most recent time you wanted to play but the session did not happen, or happened later than you wanted.”
2. “Walk me through how the group tried to organize it.”
3. “What prevented or delayed play?” Do not offer “no GM” as an answer.
4. “What did you do instead?”
5. “How often has something like that happened in the last six months?” Accept ranges and uncertainty; do not force a precise count.
6. “Who normally game-masters, and what happens when that person is unavailable or does not want to prepare?”
7. “Have you tried solo play, rotating game masters, prewritten tools, virtual tabletops, chatbots, or another substitute? What worked and failed?”
8. “If a substitute game master were available immediately, when would you use it, if at all?”

Probe for scheduling, prep burden, campaign commitment, group availability, social preference, rules confidence, and content access without assuming which is the main problem.

### 3. Concept comprehension and fit — 5 minutes

Show the standardized concept card.

1. “In your own words, what do you think this would and would not do?”
2. “When, if ever, would this fit into how you play?”
3. “What is the strongest reason you would not try it?”
4. “How does a short solo slice compare with the session you actually want?”
5. “Would use of revised 2024 rules change your decision? Why?”

Do not count concept misunderstanding as product enthusiasm. Record which phrase caused the misunderstanding.

### 4. Trust, fairness, and correction — 10–12 minutes

Assign the treatments on a precommitted alternating or randomized schedule so approximately half of participants see A then B and half see B then A. This comparison is an explicitly authorized research stimulus, not a silent change to the P0-05 paper-prototype convention or a final product decision. Keep the wording, underlying ruling, dice result, and outcome identical; only reveal timing changes:

- **Treatment A — full pre-roll disclosure:** before the roll, show the check/ruling basis, target or DC, modifiers, advantage/disadvantage, resources, and possible consequences; then show the raw roll and result.
- **Treatment B — sealed pre-roll commitment:** before the roll, show that the same fields have been time-stamped/sealed without revealing the target/DC or consequence details; after the raw roll and authoritative outcome, reveal the committed fields and evidence that they were not changed.

Both treatments preserve the accepted no-secret-fudging rule, immutable pre-roll commitment, visible raw dice/result, and visible correction history. Secret fudging is never presented as a third treatment. After each treatment ask the same neutral questions: “What do you believe was fixed before the roll?”, “What would you inspect in a dispute?”, “What information arrived too early or too late?”, and “What would still be missing?” Only after both ask, “How did the two experiences differ for you?” Record comprehension separately from preference.

Then use these concrete scenarios in rotating order to reduce order bias:

1. **No secret fudging:** “A difficult roll fails and produces the consequence that was committed before the roll. The system does not secretly alter it. How does that affect the experience?” Do not ask whether secret alteration should be added.
2. **Audit comprehension:** “Show me how you would determine whether the ruling or consequence changed after the roll.”
3. **Visible mercy:** “Before the roll, the guide can openly offer a gentler consequence or another chance, and the choice is logged. When would that feel fair or unfair?”
4. **Correction:** “A prior game-state update is discovered to be invalid. The correction is visible. A system error is compensated automatically; a discretionary rewind happens only with the affected player's agreement. What concerns would you have?”
5. **Human boundary:** “Which decisions, if any, would you refuse to let an automated game master make?”

After each scenario ask, “Why?” and “Tell me about a past game experience that shapes that answer.” Do not ask, “Does this make it trustworthy?”

### 5. Latency and pacing — 5–7 minutes

1. “Think about a digital game or tool you stopped waiting for. What was happening and how long did it feel?”
2. Present the same turn at four preselected wait bands—approximately 2, 5, 10, and 20 seconds—using a neutral timer or storyboard. Alternate order across interviews.
3. For each band ask, “What would you assume is happening?”, “What would you do while waiting?”, and “At what point would this interrupt play?”
4. “Would early meaningful text followed by the completed ruling feel different from a blank wait? In what situations?”
5. “When, if ever, would you trade a longer wait for a better-described response?”

Do not disclose proposed performance gates until after the participant responds. Record tolerance by task type, not as one universal number.

### 6. Interface expectations — 8–10 minutes

Show neutral cards for: narrative, free-text action, suggested actions, character/resources, zone/range status, rule/commitment trace, dice audit, history/correction, pause, stop, and report. Pause, stop, and report must be separate cards.

1. “Arrange these into always visible, available on demand, and not needed. Talk through your choices.”
2. “What is missing?”
3. “When would suggested actions help, and when would they constrain you?”
4. “If you typed an unsupported action, what response would let you continue without feeling railroaded?”
5. “What would you need on a phone, with a keyboard, or with a screen reader?” Ask about use needs, not disability diagnoses.
6. “Show me where you would expect pause and stop to be. What should happen immediately for each?”
7. Show the minimal report mockup. “Without submitting a real incident, show me how you would report a concern. What information would you include or refuse to include?”
8. “The proposed active-play report pauses before collecting details, then asks whether to resume or stop. What would you expect or prefer, and why?”
9. “Who do you think receives this, who should be allowed to read it, and what acknowledgement or follow-up would you expect?”
10. “What deletion or retention information would you need before submitting?”

### 7. Payment and alternatives — 5–7 minutes

Ask payment questions last so they do not prime the rest of the interview.

1. “What, if anything, do you currently pay for to make tabletop play possible or easier?”
2. “Who usually pays: one host, each player, or someone else?”
3. “If this concept worked as described, what would it replace, and what would it not replace?”
4. “In what situation would you consider paying for it, if any?”
5. “Which payment shape would make the most sense or least sense—per adventure, a host subscription, a group subscription, or something else? Why?”
6. Only after those answers: “At what price would you dismiss it as too expensive? At what price would you question whether it could be good enough? What price would feel plausible?”
7. “What would you use if this remained free but limited? What would you use if it were unavailable?”

Treat price answers as directional hypotheses, not forecasts. Do not average five hypothetical price points into a market estimate.

### 8. Close — 3 minutes

1. “What is the biggest assumption in this idea that you think we have wrong?”
2. “What single event would make you stop using it?”
3. “Is there anything important that I did not ask?”
4. Ask separately whether the participant agrees to be contacted for later research. Store that choice only in the separate contact roster.
5. Restate the deletion contact/deadline and thank the participant without soliciting endorsement or referrals during the recorded portion.

## Interviewer neutrality controls

- Use the same versioned, owner-decision-consistent concept card and core scenarios for every participant. Follow the precommitted reveal-treatment, scenario, and wait-order schedules; do not choose an order in response to a participant.
- Do not name the owner, sunk work, preferred answer, proposed price, or success threshold before the participant's response.
- Ask for the last real example before asking “would you” questions.
- Do not turn confusion into a tutorial. Record the confusion first, then give the minimum clarification needed to continue.
- Do not combine “fun and fair,” “fast and accurate,” or other two-part questions.
- Never tell a participant that another participant agreed with them.
- The interviewer completes the contrary-evidence field before discussing findings with the owner or designers.

## Coded/pseudonymous note and evidence template

Create one record per interview using this structure. The structure may be stored as Markdown, a spreadsheet, or an approved research system, but raw notes remain access-restricted. Do not label the record anonymous or de-identified merely because direct identifiers were removed.

```text
Study ID:
Deletion-token lookup verified (yes/no; never copy the token into the report):
Date / interviewer:
Consent obtained (yes/no); recording consent if separately applicable:
Segment tags: recent-blocked-play / player / GM / remote / in-person / 2014 / 2024 / AI-prior / no-AI-prior
Accommodation supplied (describe the accommodation, not a diagnosis):

Recent behavior timeline:
Current workaround and cost/effort:

Evidence items:
- Hypothesis code:
  Observation or coded excerpt:
  Excerpt/evidence ID and retractability deadline:
  Evidence class: B1 recent behavior / B2 observed task or reaction / B3 stated preference / B4 hypothetical prediction
  Direction: supports / challenges / mixed / unrelated
  Confidence: high / medium / low
  Researcher interpretation (separate from observation):
  Plausible alternative explanation:

Latency observations by task and wait band:
Ruling reveal order: A→B / B→A; comprehension and preference separately:
UI card placement and missing surface:
Pause / stop / report distinctions; report recipient-access-retention expectations:
Payment context and payer (do not infer willingness from enthusiasm):
Rules-edition impact:

Strongest disconfirming evidence:
New hypothesis or segment exposed:
Potential safety/privacy issue (no sensitive detail):
Follow-up allowed (stored only in contact roster): yes/no
```

### Coding vocabulary

Use the hypothesis codes `GA`, `TR`, `FR`, `LT`, `UI`, `PM`, and `ED`. Add these cross-cutting codes only when observed:

- `AG` — player agency or railroading;
- `UN` — unsupported action or unmet scope expectation;
- `SF` — content boundary, pause, stop, or report expectation;
- `RV` — ruling-commitment reveal timing or audit comprehension;
- `AC` — accessibility or device constraint;
- `CO` — concept comprehension failure; and
- `ALT` — substitute or alternative explanation.

Evidence strength is ordered `B1 > B2 > B3 > B4` for planning purposes. A memorable quote is not stronger than repeated recent behavior. Preserve disagreements; do not force every item into a majority theme.

## Synthesis and disconfirming-evidence review

After each interview, the interviewer has 20 minutes to clean identifiers, separate observation from interpretation, and complete the strongest-disconfirming-evidence field. After the minimum five:

1. Build a participant-by-hypothesis matrix with one cell per `supports`, `challenges`, `mixed`, or `no evidence`, linked to coded notes.
2. Rank findings by evidence class, recurrence across independent participants, relevance to the target segment, and consequence if wrong.
3. For every proposed conclusion, write the strongest contrary evidence and at least one plausible alternative explanation.
4. Report segment differences explicitly. Do not turn “three of five” into a population percentage.
5. Classify implications as `proceed`, `change`, `investigate`, or `stop/reframe`; name the affected Phase 0 artifact.
6. Keep raw evidence, interpretation, and product decision in separate fields so a later reviewer can trace each conclusion.

A finding that challenges the target problem, trust model, or short solo format returns the affected assumption to discovery. It is not to be downgraded to copy polish without evidence.

## Stopping and saturation guidance

- Five eligible completed interviews is the minimum, never a reason to stop early after favorable answers.
- At five, stop only if all minimum segments are represented, the last two interviews introduced no new high-consequence theme, and no unresolved contradiction would materially change the target user or prototype.
- Otherwise continue recruiting, normally to eight and at most ten in this discovery round, prioritizing the missing or contradictory segment.
- If a new high-consequence theme appears in either of the latest two interviews, continue until two later interviews in relevant segments add no such theme or the ten-interview cap is reached.
- If ten interviews still produce material new themes, report that thematic saturation was **not reached**. Narrow the conclusion, revise segmentation, and plan a follow-on study rather than declaring validation.
- A withdrawal, failed consent, screener-only exchange, or interview missing most core sections does not count toward the minimum. Never pressure a participant to continue to preserve sample size.

## Done criteria and required evidence

P0-04 is complete only when all of the following exist:

- at least five eligible, consenting, completed interviews meeting the segmentation floor;
- a preflight record naming the owner-decision baseline and exact concept/vignette versions, approved consent notice, data owner, access groups, incentive if any, recording posture, exact retention/deletion dates, deletion token/lookup method, tested removal procedure, backup/distribution limits, and deletion-request path;
- a coded/pseudonymous note record for every counted participant, with no direct identifiers in the research corpus and no unsupported anonymity claim;
- evidence in every required topic: recent GM-access behavior, trust, fairness/correction, latency, UI, payment, and rules-edition context;
- balanced exposure to both neutral reveal treatments, with comprehension and preference reported separately and no claim that the interview selects the final policy by itself;
- evidence that participants distinguished pause, stop, and the minimal human-routed report flow, including expected acknowledgement, recipient/access, retention/deletion, and whether report should also pause or stop;
- a participant-by-hypothesis synthesis linked to the source note IDs;
- ranked findings that distinguish observed behavior, observed reactions, preferences, and hypotheticals;
- a dedicated disconfirming-evidence section for every core hypothesis, including null or contradictory findings;
- a recruitment/segment limitations statement and an honest saturation status;
- recommended `proceed`, `change`, `investigate`, or `stop/reframe` implications for P0-03, P0-05, P0-09, P0-10, and P0-14 as applicable; and
- human A10 review confirming that no interview or result has been invented and that participant deletion/withdrawal requests have been honored.

## Human-only actions before execution

1. Name the human research lead, privacy/data owner, approved note takers, and research contact.
2. Obtain qualified review of the actual California-facing consent/privacy/incentive/recording process as appropriate; this protocol is not legal advice.
3. Choose and disclose exact retention/deletion dates, deletion-token lookup and destruction dates, excerpt/backups/distribution limits, report recipients/access, and approved storage locations; test deletion lookup and linked-excerpt removal.
4. Recruit and screen participants, schedule accommodations, and deliver any incentive without conditioning it on favorable answers.
5. Freeze the concept card, counterbalanced reveal vignettes, scenarios, and wait-order schedule against the active owner-approved P0-03 contract (base plus Amendment 01); label and version any future proposed change as proposed rather than implying it is accepted.
6. Conduct the interviews, remove incidental identifiers while retaining coded/pseudonymous status, perform the synthesis, and decide whether the evidence changes the target user or prototype.
