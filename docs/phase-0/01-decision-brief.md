# Decision brief

Status: **All recommended defaults approved by the owner on 2026-09-17; provisional items remain evidence-gated as stated**  
Evidence checked: 2026-09-17

## Executive recommendation

Use SRD 5.2.1 under CC BY 4.0, ship a wholly original adventure, and validate a private adults-only text experience before building multiplayer depth. Phase 2 should use a centrally funded commercial model API behind a provider-neutral contract, theater-of-the-mind zones, one Transparent Guide persona, one pre-generated character, local-first game records, a Teen/PG-13 content ceiling with out-of-band stop, and strict full-turn spend/latency/data controls. AI party members, voice, a tactical grid, public access, module import, higher-intensity content profiles, and self-hosted inference should remain outside v1.

The project should publicly use an original name and, after review, the compatibility phrase Wizards expressly allows. “AI Dungeon Master for D&D 5e” is a working description, not an approved public product name.

## Decision triage

| ID | Decision | Recommendation | Blocks | Deferrable portion |
|---|---|---|---|---|
| D1 | Product intent | Commercial-capable product, operated first as a private unpaid alpha | Data policy, budget, ownership, launch obligations | Pricing and business model after Phase 2 |
| D2 | Adventure source | Wholly original, SRD-safe adventure | Content schema, provenance, A5 work | Importer or third-party catalog |
| D3 | Rules baseline | SRD 5.2.1, CC BY 4.0, no mixed baseline | Every rules/content identifier and test | Supporting 5.1 later |
| D4 | Model hosting | Commercial API through a provider-neutral boundary | Data flow, cost, latency, failure modes | BYOK and self-hosting |
| D5 | AI party members | Out of v1; reconsider at Phase 5 | Nothing through Phase 4 once confirmed | All implementation |
| D6 | Visual fidelity | Theater of mind with explicit zones/range bands | Movement, reach, AoE, UI, adventure data | Tactical grid |
| D7 | Voice | Text-only v1 | Accessibility copy/input design only | All voice work |
| D8a | Authority topology | Service-authoritative for eventual remote play; local authority only in Phase 2 | Dice trust, ownership, persistence, threat model | — |
| D8b | Initial scale | Invite-only; design target 10 concurrent tables / 50 connected users | Phase 3 capacity tests | Public multi-tenant scale |
| D9 | Minors | Adults-only alpha; no knowingly under-18 users initially | Safety policy, moderation, privacy | Minor support |
| D10 | Fairness/persona/correction policy | No secret fudging; transparent-guide persona; affected-player consent for discretionary rewind | Tool schema, roles, audit model, persona tests | More than one persona |
| D11 | Vertical-slice boundary | 60–90 minutes, one level-3 pregen, three play pillars, one encounter | Rules coverage, content, evals | Broad SRD coverage |
| D12 | Branding | Original name plus reviewed “5E compatible” wording | Public repo/site/marketing | Final brand identity |
| D13 | Data retention | Phase 2 local records; export/delete; centralized metadata only for 30 days | Event/memory/log schemas | Hosted-retention duration for Phase 3 |
| D14 | Content safety | Adult players, Teen/PG-13 ceiling, session boundaries, out-of-band stop | Adventure, prompt, UI, evals | User-configurable higher-intensity profiles |
| D15 | Model turn choreography | Pre-roll proposal followed by post-result narration; tierable calls; full-trace budget | AI/engine transaction, latency, cost | Advanced speculative optimization |

## D1 — Commercial product or private hobby

### Options

1. **Private hobby/local tool.** Lowest operating and moderation burden; costs can be borne by one table. It does not prove remote hosting, sustainable economics, or a public product.
2. **Commercial intent with a private unpaid alpha.** Preserves a path to a real product while constraining early privacy, abuse, support, and cost exposure. Requires clean ownership, provenance, and data practices from the start.
3. **Public commercial service immediately.** Produces broad feedback, but prematurely creates billing, consumer, privacy, moderation, uptime, and support obligations before fun and unit economics are known.

### Recommendation

Choose option 2. Design reversible interfaces and commercial-grade provenance, but operate Phases 0–2 as a small private alpha with no public signup or payment. Commercial use is permitted by CC BY 4.0 when its conditions are met, so the main D1 impact is operational and regulatory rather than whether SRD material can be used.

### Blocking status

Blocks the production data policy, ownership/IP paperwork, model budget, and hosting posture. It need not block paper prototypes or other reversible discovery.

## D2 — Adventure source

### Options

1. **Original adventure.** Lowest rights uncertainty, best fit to the machine-readable format, and fully controllable scope. It costs original design and playtest time.
2. **User-supplied module importer.** Attractive to users, but materially more engineering and legal work. Buying a copy does not itself grant rights to reproduce, transform, store, share, or transmit it to a model provider. Hosted ingestion, output, retention, and takedown behavior all require separate review.
3. **Third-party open/licensed adventure.** Can reduce writing time, but only after chain-of-title, license compatibility, attribution, adaptation, and embedded-asset audits. A third party cannot license Wizards material it never owned.

### Recommendation

Choose option 1 for v1. Defer importers entirely. Consider option 3 only after the content format and play loop are proven and qualified counsel has reviewed or cleared the specific license chain as appropriate.

### Evidence

Wizards directs creators to the SRD for publishable material and distinguishes it from non-SRD books and the D&D Beyond Basic Rules in the [official Creator FAQ](https://www.dndbeyond.com/creator-faq). The U.S. Copyright Office explains that owning a material copy does not transfer copyright in the work in [17 U.S.C. §202](https://www.copyright.gov/title17/92chap2.html).

### Blocking status

Blocks the adventure schema examples, content corpus, and A5’s mandate.

## D3 — Rules baseline

### Options

1. **SRD 5.1 CC edition.** Matches the 2014 rule set and a mature player/tool ecosystem. Its document contains incidental branded references that require a conservative denylist, and it is no longer the current revised-rules SRD.
2. **SRD 5.2.1.** Current corrected SRD for the revised 2024 rules, CC BY 4.0 only. It adds current mechanics such as weapon masteries and intentionally removes or renames some protected references. Some players and tools will still expect 2014 behavior.
3. **Dual 5.1 + 5.2.1.** Maximizes compatibility but roughly doubles rule identity, conversion, testing, content, and attribution complexity. Mixing is legally possible with proper attribution; it is a poor v1 engineering choice.

### Recommendation

Choose SRD 5.2.1 under CC BY 4.0 and pin the exact PDF plus checksum. Do not mix 5.1 into v1. If user research strongly favors 2014 rules, switching to the CC edition of 5.1 is a valid product choice, but it must happen before domain identifiers and fixtures are created.

### Evidence and correction to the kickoff brief

The current [official SRD page](https://www.dndbeyond.com/srd) lists SRD 5.2.1 and documents its differences from 5.1. Its [official PDF](https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf) contains the version-specific legal notice on page 1.

The safe content rule is not “all named material is forbidden.” It is: only Wizards material explicitly present in the pinned SRD may be copied or adapted under this posture; original project content is allowed; all other material requires separately documented rights. A generated allowlist and provenance manifest are safer than model memory or a hand-maintained list.

### Blocking status

Hard blocker for the domain model, rules ingestion, pregens, adventure mechanics, tests, and attribution.

## D4 — Model hosting

### Options

1. **Commercial API.** Fastest path to quality and structured output; variable token cost, provider latency/outage risk, and external data processing. Requires a vendor-neutral adapter, pinned model versions, spend caps, and retention/training review.
2. **Self-hosted open weights.** Maximum operational control and potentially attractive economics at steady high utilization. It adds GPU capacity, model serving, security, upgrades, evaluation, and on-call work before demand is known; small loads commonly waste idle capacity.
3. **Bring your own key (BYOK).** Transfers inference billing to users and enables provider choice. It produces difficult onboarding, secret handling, inconsistent models/limits, support fragmentation, and unpredictable quality.

### Recommendation

Use option 1 for Phase 2 and v1, funded centrally in the private alpha. Freeze a provider-neutral request/response/tool contract, benchmark at least one balanced and one low-cost model on the same evaluation set, pin the selected version, and define a deterministic no-model fallback. Consider BYOK later as an advanced deployment option; reconsider self-hosting only after measured steady demand supports it.

### Illustrative base-inference cost

The following conservative table assumes no cache discount. It is a planning model, not a quote. Aggregate billable tokens include tool/retry/summarization overhead and exclude speech, storage, networking, human support, taxes, and provider-specific extras.

| Three-hour session shape | Input tokens | Output tokens | Gemini 3.8 Flash at $0.75/$3.75 per 1M | Claude Sonnet 5 at $2/$10 per 1M |
|---|---:|---:|---:|---:|
| Lean | 0.24M | 0.02M | $0.26 | $0.68 |
| Planning base | 0.70M | 0.05M | $0.71 | $1.90 |
| Stress | 1.90M | 0.10M | $1.80 | $4.80 |

Rates are examples from the providers’ official pages as checked on 2026-09-17: [Gemini API pricing](https://ai.google.dev/gemini-api/docs/pricing) and [Claude API pricing](https://platform.claude.com/docs/en/about-claude/pricing). Google’s shown Flash price is promotional through 2026-12-31; caching and routing can materially change both cost and latency. Quality must be measured rather than inferred from price.

A more detailed 45-turn, single-pass-equivalent base model with 0.621M input, 0.028M output, 15% retry/tool allowance, and 60% cache reads yields roughly $0.34–$1.05 across current balanced API candidates. Stronger balanced/flagship models span about $0.89–$2.22; a premium frontier example is about $4.43. This makes p50 under $1 and p95 under $2 a useful target, not yet an accepted gate: a systematic post-result model pass can add roughly 40–100%. D15 therefore requires the complete multi-call logical turn to be measured before those thresholds are approved.

### Blocking status

The provider class, data constraints, and budget ceiling block Phase 2. The final vendor does not need to be chosen until the bake-off.

## D5 — AI party members

### Options

1. AI DM only.
2. AI DM plus one or more AI player characters.

### Recommendation

Choose option 1 through Phase 4. AI players add separate hidden-information boundaries, tactics, personalities, turn latency, balance, and player-agency risks. They do not help prove the core model/engine contract.

### Blocking status

Not technically blocking once explicitly deferred. It must stay out of event, prompt, and UI requirements through Phase 4.

## D6 — Visual fidelity

### Options

1. **Pure prose theater of mind.** Smallest UI, but insufficiently precise for reach, movement, opportunity attacks, cover, and areas of effect.
2. **Theater of mind with named zones/range bands.** Keeps the product text-first while giving deterministic mechanics a bounded spatial model.
3. **Tactical grid/VTT.** Highest positional fidelity; introduces pathfinding, line of sight, templates, maps, tokens, and a large asset/editor surface.

### Recommendation

Choose option 2. Use encounter-defined zones and relationships such as engaged, near, far, and out-of-scene, with explicit transitions and rule-aware distances. Do not promise exact-grid equivalence.

### Blocking status

Blocks movement/action contracts, encounter authoring, and the client state projection.

## D7 — Voice

### Options

1. Text only.
2. Speech-to-text input only.
3. Full speech input and generated voice output.

### Recommendation

Choose option 1 for v1 while meeting keyboard and screen-reader accessibility requirements. Voice multiplies cost, streaming, moderation, interruption, consent, and accessibility concerns before the text loop is proven.

### Blocking status

Deferrable through Phase 4. Confirm now so it does not leak into Phase 2 requirements.

## D8 — Authority topology and scale

The original question combines two decisions that should be separated.

### D8a options: who is authoritative?

1. **Host device.** Cheap and private but disconnect-prone; the host can alter state or dice and cannot honestly be treated as a neutral authority.
2. **Hosted service.** Supports reconnect, remote join, neutral audit, access control, and centralized updates; creates operating cost and data responsibility.
3. **User-operated dedicated server.** Good for technical/private groups, difficult onboarding and support, and no neutral service trust.

### D8a recommendation

Use local authority only for the Phase 2 slice. Design Phase 3 for a hosted authoritative service if arbitrary-network multiplayer remains a product requirement. Be explicit that a host-authoritative deployment provides auditability, not protection from a cheating host.

### D8b options: how much initial scale?

1. One table at a time.
2. Invite-only multi-table alpha.
3. Public multi-tenant service.

### D8b recommendation

Choose option 2 with an initial design target of 10 concurrent tables and 50 connected users. This is a capacity-test target, not a demand forecast. Defer autoscaling and public abuse controls until human play and unit economics pass.

### Blocking status

Authority is a hard blocker for dice claims, session ownership, and persistence contracts. Scale beyond a stated alpha target is deferrable to Phase 3.

## D9 — Minors

### Options

1. Adults-only private alpha.
2. Teen users with an age floor and tailored safety/privacy controls.
3. Children and families as an intended audience.

### Recommendation

Choose option 1. Supporting minors is not a copy change; it affects age assurance, data collection, consent, retention, moderation, reporting, model behavior, and marketing. For example, the U.S. [COPPA rule](https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa) applies to covered services directed to children under 13 or with actual knowledge of collection from them. Other jurisdictions differ; qualified counsel must review any future expansion.

### Blocking status

Hard blocker for safety and privacy policy. It does not block a genuinely private adults-only slice.

## Additional decisions surfaced by review

### D10 — Fairness, personas, overrides, and rewind

#### Options

1. **Hidden fudging and host-only correction.** Familiar to some human tables and fast, but incompatible with verifiable fairness and vulnerable to host abuse.
2. **No correction and strict simulation.** Maximizes procedural consistency, but traps players in software/rules defects and accidental input.
3. **Declared difficulty plus consent-based correction.** Commit rulings before rolls, expose any mercy resource, and preserve correction/fork history. A system-detected invalid event can be automatically compensated with visible notice; a discretionary rewind is proposed by the host and requires consent from every directly affected player. If an affected player is unavailable, the proposal waits or is abandoned rather than inferring consent. In solo Phase 2, the player authorizes it. Any player may invoke the safety stop without a vote; that pauses rather than rewrites the game.

#### Recommendation

Choose option 3. The persona may affect voice, pacing, encounter selection, and an explicitly bounded pre-roll DC policy. It may not alter committed modifiers, outcomes, rules semantics, secret visibility, or correction consent. Use one **Transparent Guide** persona in Phase 2: concise and beginner-friendly, neutral rules strictness, medium declared threat, no hidden mercy, rules explanation on request, and a duty to ask for clarification rather than invent authority.

#### Blocking status

Hard blocker for command roles, dispute UX, event correction/fork semantics, action schemas, persona tests, and what “fair” means.

### D11 — Exact Phase 2 slice

#### Options

1. **Bounded solo slice.** One pregen and short scenario; fastest proof of the model/engine contract, but does not validate group dynamics.
2. **Local hot-seat party slice.** Better spotlight evidence, but adds multi-seat visibility and turn UX before networking.
3. **Broad rules sandbox.** Looks flexible, but lacks a testable content/rules boundary and delays human value validation.

#### Recommendation

Choose option 1: one level-3 pre-generated character, 60–90 minutes, one social objective, one exploration obstacle, one combat encounter, and success/failure/recovery endings. Declare every supported action, class feature, spell, item, condition, and monster ability before Phase 1. Use facilitated group prototypes in Phase 0 to learn about future spotlight behavior without expanding the production slice.

#### Blocking status

Hard blocker for coverage, content, fixtures, cost/latency projections, and human evaluation. Broad SRD coverage is deferrable to Phase 4.

### D12 — Branding

#### Options

1. **Use D&D/Dungeon Master branding.** Strong recognition, but material trademark/endorsement risk outside the CC license.
2. **Original name plus reviewed compatibility wording.** Lower recognition but the cleanest independent-product posture.
3. **Neutral original name with no compatibility wording.** Lowest branding association, but makes discovery and player expectations harder.

#### Recommendation

Choose option 2. SRD 5.2.1 says a work may identify itself as compatible with fifth edition or 5E compatible, while CC BY does not license trademarks. Treat “AI Dungeon Master for D&D 5e” as an internal description. “D&D,” its logos, and “Dungeon Master” require separate branding review. Qualified counsel advises or provides clearance as appropriate; the human owner accepts any residual business/legal risk.

#### Blocking status

Blocks public naming, repository presentation, domains, marketing, and launch; it does not block internal mechanics prototypes using a neutral codename.

### D13 — Data retention and visibility

#### Options

1. **Ephemeral sessions.** Delete game data when play ends. Lowest retention risk, but no resume, replay, or longitudinal debugging.
2. **Local-first Phase 2 with user control.** Store game events and exact narration on the tester’s device until the user exports or deletes them; send only privacy-safe operational metadata to the project and retain that centrally for 30 days. Defer hosted game-record duration until Phase 3.
3. **Indefinite hosted history.** Best continuity and analytics, but largest privacy, breach, deletion, and cost exposure.

All options still require four data classes: public table state, player-private state, GM-private state, and operational metadata. Authorization filtering occurs before retrieval/model access, not after an over-broad object is returned.

#### Recommendation

Choose option 2. Phase 2 offers explicit export and delete controls. Raw prompts, backstories, role-play, and narrative do not enter project-operated centralized telemetry; model-provider retention remains a separate D4/Q9 constraint. Append-only authority applies inside a retained session; deleting the whole user/session record remains possible, and backup/key-erasure behavior must be documented. Before Phase 3, set a hosted inactivity period, account/session deletion SLA, backup purge window, and legal-hold process with qualified guidance.

#### Blocking status

Hard blocker for event payloads, memory, telemetry, encryption, export/delete UX, provider review, and test-consent language. The precise hosted duration is deferrable to Phase 3 if Phase 2 remains local-first.

### D14 — Content boundaries and safety controls

#### Options

1. **Unrestricted adult content.** Maximizes creative range but sharply increases safety, model-policy, moderation, and participant-harm risk.
2. **Adults-only audience with a Teen/PG-13 content ceiling.** Ordinary fantasy violence and mild horror are allowed; explicit sexual content, sexual violence, hate-based targeting, encouragement of self-harm, and graphic torture/gore are excluded. Players set lines/veils and phobias before play, can pause/stop out of band at any time, and can report a scene.
3. **Family/minor-safe design.** Broadest safeguarding burden and requires the minor/privacy decision D9 to change.

#### Recommendation

Choose option 2 for v1. A safety stop bypasses the model and immediately pauses generation and state progression. Lines/veils are policy inputs, not prompt text with authority. The adventure and fixed evaluation corpus include fantasy violence/horror cases and attempts to cross every excluded boundary.

#### Blocking status

Hard blocker for A5 content, A2 behavior, A4 controls, A7 policy, A6 attack/safety corpus, and A10 consent/playtest protocol. Higher-intensity profiles are out of v1.

### D15 — Model turn and transaction choreography

#### Options

1. **One model pass plus deterministic result templates.** The model proposes before the roll; the engine resolves; a template reports the result. Cheapest/fastest, but outcome narration is less natural.
2. **Two-stage same-model tool continuation.** The model proposes, the engine commits/rolls/applies, then the model receives the authorized delta and narrates. Best continuity, but adds a billed latency leg and can nearly double some turn costs.
3. **Tiered hybrid.** Use a certified low-cost/fast model or deterministic parser for intent/proposal where possible, the chosen narrative model after resolution, and deterministic templates as timeout/budget fallback. More evaluation/routing complexity, but preserves truth and controls spend.

#### Recommendation

Choose option 3 as the Phase 2 hypothesis, with option 1 as the mandatory fallback. Never stream an outcome before the authoritative result exists. P0-09 must model and P1B/P2F must measure the **entire logical turn**—all calls, tool round trips, retries, cache traffic, and final narration—before the owner accepts cost/latency thresholds.

#### Blocking status

Hard blocker for the AI proposal contract, transaction boundary, narration timing, cache layout, fallback UX, and meaningful cost/latency gates. Model-routing optimization remains reversible after the full-trace baseline is measured.

## Attribution control

D3 is accepted. P0-02 now pins the official SRD 5.2.1 PDF and checksum, reproduces its exact two-sentence attribution block in the local legal notice, and adds a separate neutral change statement for the structured-software adaptation. Every distribution that contains SRD-derived material must reuse that version-specific notice; generic or mixed-version notices remain prohibited.

This brief is a planning and risk document, not legal advice. Commercial launch, branding, user content/import, privacy terms, and final notices require qualified review.
