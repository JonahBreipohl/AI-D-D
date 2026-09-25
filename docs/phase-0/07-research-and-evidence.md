# Research and evidence notes

Checked: **2026-09-17**  
Purpose: preserve the source-backed facts used by the Phase 0 recommendations. This is not legal advice and vendor prices/policies can change.

## Licensing and content

### Verified baseline

| Topic | Verified fact | Product consequence | Primary source |
|---|---|---|---|
| SRD 5.1 | Rules baseline for the 2014 rules; available under OGL 1.0a or, separately, CC BY 4.0 | A new 5.1 product should choose one route; this plan recommends the CC edition if 5.1 is selected | [Wizards announcement](https://www.dndbeyond.com/posts/1439-ogl-1-0a-creative-commons), [current SRD page](https://www.dndbeyond.com/srd) |
| SRD 5.2.1 | Current corrected English SRD for the revised 2024 rules; CC BY 4.0 only | Pin 5.2.1 rather than the earlier, still-valid 5.2.0 release if revised rules are selected | [Current SRD page](https://www.dndbeyond.com/srd), [official PDF](https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf) |
| CC BY 4.0 | Permits use, adaptation, and commercial use with attribution, license link, change indication, no implied endorsement, and no additional restriction on the licensed material | Original code/adventure need not become CC licensed, but SRD-derived material must retain the license conditions | [CC deed](https://creativecommons.org/licenses/by/4.0/), [legal code](https://creativecommons.org/licenses/by/4.0/legalcode) |
| Attribution | Each SRD PDF prescribes a version-specific two-sentence block on page 1 and says not to add other Wizards attribution | Copy the chosen block exactly into product/repo/docs containing derived material; do not use a generic mixed notice | [SRD 5.2.1 PDF](https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf), [SRD 5.1 CC PDF](https://media.dndbeyond.com/compendium-images/srd/5.1/SRD_CC_v5.1.pdf) |
| Branding | CC does not grant trademark rights; the SRD permits limited compatibility wording | Use an original product name and review branding; do not imply official status | [SRD 5.2.1 legal page](https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf), [CC legal code](https://creativecommons.org/licenses/by/4.0/legalcode) |
| Basic Rules | D&D Beyond Basic Rules are not licensed as the SRD for content creation | Ingest from the selected SRD PDF, not scraped Basic Rules pages | [Creator FAQ](https://www.dndbeyond.com/creator-faq) |
| User-owned books | Ownership of a copy does not itself transfer copyright | A module importer is not automatically safe; upload, copying, transformation, model transmission, sharing, and retention need review | [17 U.S.C. §202](https://www.copyright.gov/title17/92chap2.html), [Copyright basics](https://copyright.gov/circs/circ01.pdf) |

### Corrections to the kickoff assumptions

1. The invariant should be **“no unlicensed Wizards-derived content”**, not “only SRD content may ship.” The project’s original adventure and properly licensed original/third-party assets may ship. Every object still needs provenance.
2. SRD 5.2.1 is the current corrected 5.2-family document. “5.2” alone is not a sufficient version pin.
3. SRD 5.1 contains some incidental branded references. Their presence in a CC document does not grant trademark rights. The conservative product policy should exclude them and derive the actual usable catalog from an explicit allowlist.
4. “User supplies a module they own” is not the same as permission for a hosted service to copy, adapt, store, or transmit it.
5. A7 can maintain evidence and enforce a release checklist. Qualified counsel advises or provides clearance as appropriate; the human owner accepts residual commercial legal risk.

### Attribution implementation control

D3 and the local source-pin portion of P0-02 are complete. Items 1–3 below are implemented in the evidence pack; items 4–6 remain release controls for any later distribution:

1. Store the exact selected PDF locally or by immutable source reference, record SHA-256, release name, URL, and retrieval date.
2. Copy the exact page-1 attribution block without editing its version or URL.
3. Add a separate neutral change note that SRD material was reformatted/adapted for structured software use.
4. Include the notice in an accessible in-product Legal/Credits view and in repository/documentation distributions that contain SRD-derived material.
5. Mark every shipped object as original, selected-SRD-derived, or separately licensed. Unknown provenance fails the build/release check.
6. Review product terms so they do not purport to remove downstream rights granted by CC BY for the SRD-derived portions.

## Model cost and hosting

### Recommendation supported by evidence

A centrally funded commercial API is the lowest-risk Phase 2 default. It has negligible fixed capacity cost, current structured-output support, and the fastest path to a quality bake-off. The product should isolate provider specifics, certify multiple model/configuration pairs, and postpone the final vendor choice until game-specific evaluation.

BYOK can later transfer cost to a host but adds key security, quota/model variability, onboarding, and support burden. Self-hosting adds fixed GPU capacity and MLOps before utilization and quality parity are known.

### Rate-card snapshot

USD per million tokens; checked 2026-09-17. Prices are illustrative inputs to the sensitivity model, not endorsements.

| Model | Fresh input | Cache read | Cache write | Output | Source |
|---|---:|---:|---:|---:|---|
| OpenAI GPT-5.6 Luna | $0.20 | $0.02 | $0.25 | $1.20 | [Official model page](https://developers.openai.com/api/docs/models/gpt-5.6-luna) |
| OpenAI GPT-5.6 Terra | $2.00 | $0.20 | $2.50 | $12.00 | [Official model page](https://developers.openai.com/api/docs/models/gpt-5.6-terra) |
| OpenAI GPT-6 Astra | $10.00 | $1.00 | $12.50 | $50.00 | [Official model page](https://developers.openai.com/api/docs/models/gpt-6-astra) |
| Claude Haiku 4.5 | $1.00 | $0.10 | $1.25 | $5.00 | [Claude pricing](https://platform.claude.com/docs/en/about-claude/pricing) |
| Claude Sonnet 5 | $2.00 | $0.20 | $2.50 | $10.00 | [Claude pricing](https://platform.claude.com/docs/en/about-claude/pricing) |
| Claude Opus 5 | $5.00 | $0.50 | $6.25 | $25.00 | [Claude pricing](https://platform.claude.com/docs/en/about-claude/pricing) |
| Gemini 3.8 Flash | $0.75 | $0.075 | provider-specific storage | $3.75 | [Gemini pricing](https://ai.google.dev/gemini-api/docs/pricing) |
| Gemini 3.1 Pro Preview | $2.00 | $0.20 | provider-specific storage | $12.00 | [Gemini pricing](https://ai.google.dev/gemini-api/docs/pricing) |
| Mistral Small 4 API | $0.15 | $0.015 | — | $0.60 | [Mistral pricing](https://docs.mistral.ai/inference/pricing) |

Gemini 3.8 Flash’s displayed rates are scheduled to double on 2027-01-01. Cache semantics, tokenizers, thinking tokens, service tiers, regions, and model lifecycle differ. The session estimates below use Anthropic’s 5-minute write tier; using its 1-hour Sonnet tier changes base/heavy from about $0.89/$1.64 to $0.98/$1.85. Gemini estimates assume Standard service plus 0.5 average cache-storage hours per explicit write; actual implicit/explicit caching must be measured. Actual API traces—not a normalized spreadsheet alone—must drive selection.

### Three-hour session model

Cost model:

`input × (fresh share × fresh rate + write share × write rate + read share × read rate) + output × output rate + cache storage`

All scenarios include a 15% allowance for ordinary tool/schema overhead and occasional retry. They assume rolling summary/retrieval and low/no reasoning. They exclude voice, images, search, application hosting, tax, support, and a systematic second model pass.

| Scenario | Turns | Avg input/turn | Output/turn | Billable input | Billable output | Cache read / write / fresh |
|---|---:|---:|---:|---:|---:|---:|
| Light | 30 | 6k | 350 | 0.207M | 0.012M | 50% / 10% / 40% |
| Base | 45 | 12k | 550 | 0.621M | 0.028M | 60% / 10% / 30% |
| Heavy | 60 | 20k | 800 | 1.380M | 0.055M | 70% / 10% / 20% |

| Candidate | Light | Base | Heavy |
|---|---:|---:|---:|
| Mistral Small 4 API | $0.02 | $0.06 | $0.11 |
| OpenAI GPT-5.6 Luna | $0.04 | $0.09 | $0.18 |
| Gemini 3.8 Flash | $0.14 | $0.34 | $0.62 |
| Claude Haiku 4.5 | $0.18 | $0.44 | $0.82 |
| Claude Sonnet 5 | $0.36 | $0.89 | $1.64 |
| OpenAI GPT-5.6 Terra | $0.38 | $0.94 | $1.75 |
| Gemini 3.1 Pro Preview | $0.45 | $1.05 | $1.93 |
| Claude Opus 5 | $0.90 | $2.22 | $4.11 |
| OpenAI GPT-6 Astra | $1.79 | $4.43 | $8.21 |

Price is not a quality score. A model qualifies only after structured-action, engine-legality, injection/secret, narration, continuity, latency, and cache/cost gates. A mandatory second post-resolution generation on every turn can add roughly 40–100%; the 15% allowance is not enough for that design.

### Why self-hosting is deferred

Mistral describes Small 4 as 119B total parameters and 6B active, but its published examples mix GPU counts and complete systems. In particular, a DGX B200 contains eight B200 GPUs, so treating “one DGX B200” as one GPU materially understates capacity cost. A literal multiplication of current Fireworks per-GPU on-demand rates would put four H100 GPUs near $32/hour, two H200 GPUs near $16/hour, and the eight GPUs in one DGX B200 near $104/hour—before redundancy, storage, networking, engineering, security, or support. These are not throughput-equivalent quotes, and HGX/DGX packaging, quantization, context length, batching, and utilization can dominate the result. The project should not claim a break-even point until it pins a serving configuration and load-tests quality and sessions/hour. Sources: [Mistral Small 4 requirements](https://mistral.ai/news/mistral-small-4/), [NVIDIA DGX B200 specifications](https://www.nvidia.com/en-us/data-center/dgx-b200/), and [Fireworks per-GPU pricing](https://fireworks.ai/pricing).

### Data-policy distinction

“Commercial API” does not automatically mean training use, but it also does not mean zero retention. Current vendor policies differ:

- OpenAI states API data is not used for training by default; standard abuse-monitoring logs may be retained up to 30 days, with eligibility requirements for stronger controls. [OpenAI data controls](https://developers.openai.com/api/docs/guides/your-data)
- Anthropic states commercial inputs/outputs are not used for training by default and describes normal API retention, subject to exceptions. [Training policy](https://privacy.claude.com/en/articles/7996868-is-my-data-used-for-model-training), [retention](https://privacy.claude.com/en/articles/7996866-how-long-do-you-store-my-organization-s-data)
- Google states paid Gemini prompts/responses are not used to improve products and documents separate abuse-monitoring/ZDR conditions. [Gemini data controls](https://ai.google.dev/gemini-api/docs/zdr), [usage policy](https://ai.google.dev/gemini-api/docs/usage-policies)

The bake-off must therefore include retention, region, training, deletion, and provider-logging requirements—not just price and quality.

## Phase 2 observability baseline

One metadata-only record per model call should contain:

- hashed session and turn IDs; call purpose (DM, summary, memory, moderation);
- provider, requested/resolved model/snapshot, tier, and region;
- prompt/persona/adventure/tool-schema versions;
- start, first-content, tool-result, and completion timestamps;
- fresh/cache-write/cache-read input, visible output, and reasoning/thinking tokens;
- tool calls, schema failures, engine rejections, retries, fallback, provider error, and finish reason;
- price-catalog version, estimated cost, and provider request ID;
- no raw role-play, backstory, secret, or narrative text in ordinary operational telemetry.

Proposed measured gates:

- three-hour text-only cost p50 < $1 and p95 < $2 on the selected balanced tier;
- first meaningful streamed content p95 ≤5 seconds;
- full normal response target p95 ≤10 seconds; 20 seconds is a hard ceiling requiring explicit owner acceptance rather than a normal target;
- warm cache-read share ≥50%; input p95 ≤20k tokens; output p95 ≤800 billable tokens;
- schema/engine retry rate <5%, alongside the stricter task-level validity/fallback gates;
- internal request ledger reconciles within 2% of provider daily usage/cost;
- alert when a persona/adventure raises tokens per turn by >25% from its approved baseline.

## Evidence gaps to close in Phase 0/2

- No source establishes current player preference for 2014 vs. revised 2024 rules; representative-user research must decide the product tradeoff.
- Rate cards do not predict game-master quality, fairness, or injection resistance; the fixed bake-off must decide.
- A CSPRNG plus an append-only log is auditable but not automatically cryptographically verifiable; the authority/threat model and commitment protocol need an ADR and independent verifier.
- Event sourcing supports replay only when reducers, ordering, idempotency, versions, snapshots, and migrations are correct; Phase 1 must prove those properties.
- No automated simulation establishes fun or trust; human prototype and slice tests are mandatory.
