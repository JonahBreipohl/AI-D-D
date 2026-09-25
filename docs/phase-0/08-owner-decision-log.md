# Owner decision log

## Decision batch OD-2026-09-17-01

**Recorded:** 2026-09-17  
**Owner response:** “Approve all recommended defaults.”  
**Scope:** All seventeen questions in the Phase 0 planning pack.  
**Effect:** P0-01 is complete. Phase 0 discovery work is unblocked. No production implementation or Phase 1 build work is authorized until G0.  
**Operator and initial-alpha jurisdiction:** California, United States.

## Accepted product decisions

| ID | Accepted decision | Qualification / later gate |
|---|---|---|
| D1 | Commercial-capable product beginning as a private unpaid alpha in California, United States | Pricing and public-launch business model remain deferred until after Phase 2 evidence |
| D2 | Wholly original SRD-safe v1 adventure | Published-module import and third-party adventures deferred |
| D3 | SRD 5.2.1 under CC BY 4.0; no mixed rules baseline | Pin PDF/checksum and install exact version-specific notice in P0-02 |
| D4 | Centrally funded commercial API behind a provider-neutral boundary | Provider/model remains provisional until the bake-off; provider data terms remain a gate |
| D5 | AI game master only through Phase 4 | AI party members may be reconsidered only at Phase 5 |
| D6 | Theater of mind with explicit zones/range bands | Tactical grid/VTT features deferred |
| D7 | Text-only v1 with keyboard and screen-reader accessibility | Voice deferred |
| D8a | Local authority for Phase 2; hosted neutral authority for eventual multiplayer | Exact hosting design remains an ADR/task |
| D8b | Invite-only alpha sized initially for 10 simultaneous tables / 50 connected users | Public multi-tenant scale deferred |
| D9 | Adults-only, invite-only alpha; no public signup | Support for minors requires a separate legal/privacy/safety gate |
| D10 | No secret fudging; pre-roll commitments; visible mercy; consent-based discretionary rewinds; Transparent Guide persona | System corrections remain visible; absent affected players never have consent inferred |
| D11 | One 60–90 minute level-3 solo slice covering social, exploration, one combat, and success/failure/recovery | Broad SRD coverage deferred |
| D12 | Original public product name; current “AI Dungeon Master for D&D 5e” wording is internal only | Public compatibility wording and “Dungeon Master” use require qualified review |
| D13 | Phase 2 records local until export/delete; centralized metadata-only telemetry retained 30 days | Hosted retention/deletion SLA deferred to Phase 3; provider retention handled under D4 |
| D14 | Adults-only audience with a Teen/PG-13 content ceiling, lines/veils/phobias, and out-of-band pause/stop/report | Higher-intensity profiles deferred |
| D15 | Tiered-hybrid turn: proposal, authoritative validation/roll/apply, then narration; deterministic fallback | Provisional until full-turn evidence amends/finalizes ADR-0007/0015 at P1B-05 |

## Accepted execution and gate decisions

- **Phase 1B approved:** A2/A6/A8 may later run the bounded, mock-only feasibility spike once its prerequisites are complete. It cannot access or mutate authoritative state.
- **Success-gate approach approved:** Completion, replay intent, fun/trust, correctness, zero visibility leaks, content safety/stop behavior, latency, and cost remain the go/change/stop dimensions.
- **Cost and latency remain provisional:** p50 under $1 and p95 under $2 per three-hour text session, plus the stated latency targets, must be measured over the complete multi-call logical turn and finalized or replaced—with owner acceptance—at P1B-05 before AI integration.

## Factual-input status

All factual inputs requested with the decision batch are resolved. No additional provider prohibition, region requirement, zero-retention mandate, or monthly-spend constraint applies beyond the accepted defaults unless the owner later states one. California and applicable United States requirements are the starting jurisdictional frame for P0 legal/privacy research; qualified review remains required where the planning pack specifies it.

## Decision batch OD-2026-09-18-01

**Recorded:** 2026-09-18  
**Owner response:** “continue” in response to the request to approve the audited Phase 0 slice.  
**Scope:** All three acceptance areas in P0-03: the named scenario/graph/encounter/endings; Rin Alder’s build and supported/unsupported envelope; and the timing, full-disclosure paper-prototype, safety, fairness, accessibility, data, correction, and measurement constraints.  
**Effect:** P0-03 is complete and becomes the accepted P0-05/P0-06 research baseline. Versioned research-material preparation and the required human research/privacy/safety preflight may proceed. No interviews or sessions are claimed, G0 remains closed, and no Phase 1 production implementation is authorized.

## Decision batch OD-2026-09-23-01

**Recorded:** 2026-09-23  
**Owner response:** “Approve Amendment 01.”  
**Scope:** [P0-03 Amendment 01](evidence/P0-03-amendment-01-proposed.md) in full, including the deterministic values and downstream contract/test changes for `B-01` through `B-11`, bounded ruling `AM01-R1`, and the coupled arrival, asset, combat-start, and hand-state conventions.  
**Effect:** Amendment 01 is accepted and in force as of 2026-09-23. The accepted base P0-03 specification plus Amendment 01 is the active P0-05/P0-06 research contract, and Amendment 01 controls wherever the two conflict. The decision resolves the eleven P0-03 contract choices but does not itself incorporate them into P0-06 or the run pack, clear any fielding preflight, authorize recruitment or human research, complete P0-06, open G0, or authorize Phase 1 production implementation.

**Downstream record, 2026-09-23:** The accepted values were subsequently incorporated into the [provisional P0-06 matrix](evidence/P0-06-coverage-matrix.md), [operator baseline v0.2](evidence/P0-06-provisional-operator-baseline-v0.2.md), and [P0-05 run pack v0.2](research/P0-05-run-pack-v0.2.md). Those drafts require independent human review, operational preflight, and a version-matched dry run; their existence does not authorize participant contact or change G0.

## Decision batch OD-2026-09-25-01

**Recorded:** 2026-09-25  
**Owner response:** Authorized the initial Git commit and push, approved continued desk-only Phase 0 work, and directed that human research be deferred for now.  
**Scope:** Source-control publication of the existing planning baseline and continued work on artifacts that can be drafted, checked, and reviewed without recruiting, contacting, scheduling, or observing participants.  
**Effect:** The planning baseline may be maintained in the canonical GitHub repository, and desk-authorable Phase 0 tasks may continue in dependency order. P0-04 and P0-05 fieldwork remain `NO-GO`; no invitation, recruitment, screening, interview, prototype session, or participant evidence is authorized. This decision does not satisfy required human or qualified reviews, close G0, or authorize Phase 1 production implementation.
