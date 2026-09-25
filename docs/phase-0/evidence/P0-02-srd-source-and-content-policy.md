# P0-02 — SRD 5.2.1 source pin and initial rules/content policy

Status: **Complete as the Phase 0 source pin and initial internal policy; not a legal clearance for public or commercial release**  
Verified: **2026-09-17**  
Scope: **Phase 1A, the optional Phase 1B feasibility spike, and the Phase 2 private vertical slice**

## Decision and source pin

The sole Wizards rules-content source admitted by this baseline is the English **System Reference Document 5.2.1**, published by Wizards of the Coast LLC under **CC BY 4.0**. SRD 5.1, SRD 5.2.0, D&D Beyond Basic Rules, core rulebooks, supplements, adventures, settings, and other Wizards material are outside this baseline even if a team member owns or can access them.

The official D&D Beyond [SRD page](https://www.dndbeyond.com/srd) identifies English SRD 5.2.1 as the current download, published May 1, 2025, and links the [official PDF](https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf). The same page distinguishes prior release 5.2.0 and states that SRD 5.2 releases use CC BY 4.0. The [Creator FAQ](https://www.dndbeyond.com/creator-faq) separately confirms that the D&D Beyond Basic Rules are not the SRD content-creation source.

| Field | Pinned value |
|---|---|
| Document ID | `wotc-srd-5.2.1-en-cc-by-4.0` |
| Version / language | 5.2.1 / English |
| Local file | [`third_party/srd/SRD_CC_v5.2.1.pdf`](../../../third_party/srd/SRD_CC_v5.2.1.pdf) |
| Official landing page | `https://www.dndbeyond.com/srd` |
| Official download URL | `https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf` |
| Official publication date | 2025-05-01 |
| Retrieval date | 2026-09-17 (America/Los_Angeles) |
| File size | 6,031,375 bytes |
| SHA-256 | `8974902d109d6e63672d7c490bde9ccf052410503d9cfa768237154fbc5e3d87` |
| License | Creative Commons Attribution 4.0 International (`CC-BY-4.0`) |
| Metadata record | [`third_party/srd/SOURCE.json`](../../../third_party/srd/SOURCE.json) |
| Checksum record | [`third_party/srd/SRD_CC_v5.2.1.pdf.sha256`](../../../third_party/srd/SRD_CC_v5.2.1.pdf.sha256) |

### Technical verification

- The official download returned HTTP 200, `application/pdf`, and a content length of 6,031,375 bytes; the local byte count matches.
- The file begins with `%PDF-1.6`, ends with `%%EOF`, and is reported as a 364-page, unencrypted PDF/X-4 document.
- `pdfinfo` opened the document without structural warnings; `pypdf` opened it in strict mode and extracted text from both the first and last pages.
- Page 1 rendered successfully and was visually inspected. Its title, legal text, attribution statement, links, page number, and footer were legible and complete.
- The SHA-256 above was recomputed from the completed local download and matches the checksum sidecar. Recompute and compare this hash before any ingestion run; a mismatch is a hard stop, not an automatic upgrade.

## Required attribution and change indication

The following is the exact two-sentence attribution statement prescribed on page 1 of the pinned PDF. Do not edit its version, names, wording, or URLs:

> This work includes material from the System Reference Document 5.2.1 (“SRD 5.2.1”) by Wizards of the Coast LLC, available at https://www.dndbeyond.com/srd. The SRD 5.2.1 is licensed under the Creative Commons Attribution 4.0 International License, available at https://creativecommons.org/licenses/by/4.0/legalcode.

Use this separate, neutral change indication for adapted material:

> Changes: SRD 5.2.1 material has been excerpted, reformatted, structured, and adapted for software use in this project.

The repository copy is [`third_party/srd/NOTICE.md`](../../../third_party/srd/NOTICE.md). Any distribution containing SRD-derived material must present the exact attribution and change indication in an accessible Legal/Credits surface and in accompanying repository or documentation notices. Do not substitute a generic Creative Commons notice.

## Evidence, policy, and legal advice are different things

| Category | What this document supplies | What it does not supply |
|---|---|---|
| Evidence | Official URLs, publication and retrieval facts, local bytes, document properties, exact notice text, and a reproducible checksum | A warranty that the source will never move or that every future use is compliant |
| Internal policy | A deliberately narrow, fail-closed content boundary for Phase 1–2 | Permission to add material merely because it seems compatible, familiar, commonly used, or accessible |
| Legal advice | None | Counsel’s judgment on trademark use, commercial notices and terms, model-output risk, user uploads, fair use, or jurisdiction-specific obligations |

The [CC BY 4.0 deed](https://creativecommons.org/licenses/by/4.0/) summarizes permission to share and adapt, including commercially, subject to attribution, a license link, a change indication, no implied endorsement, and no additional restrictions on the licensed material. The [legal code](https://creativecommons.org/licenses/by/4.0/legalcode) controls and expressly states that trademark rights are not licensed.

## Fail-closed admission rule

Every Phase 1–2 content or data object passes one of two explicit gates:

- **Reusable-content gate.** An object may enter a rules or adventure corpus, prompt/test fixture library, reusable retrieval index, training/evaluation corpus, marketing asset, or distributable static artifact only with a resolved provenance class and an `ALLOW_REUSABLE` decision.
- **Live-session gate.** An object with `ALLOW_RUNTIME_ONLY` may travel only through the exact runtime paths authorized for its class, including an explicitly authorized user-initiated session export. A session export is not permission to promote the data into a reusable corpus or static product content; that requires a new review and reclassification.

For either gate, all of the following must be true:

1. The object has exactly one resolved provenance class below, or field/span-level classes where material is genuinely mixed.
2. Its requested use is permitted by that class and its recorded decision; `DENY` and `UNKNOWN` block every use.
3. Reusable material is required by the approved slice or a named verification case; inclusion in the 364-page PDF alone does not put every SRD element in scope.
4. The evidence required for that class—source locators and license/change fields for sourced material, or runtime lineage and handling fields for session data—is present.
5. It passes the applicable injection, safety, visibility, and trademark/brand controls and contains no denied or unresolved component.

There is no “temporarily allow,” “probably SRD,” or “owner has the book” status. A mixed object inherits the most restrictive status until it is split and every part is resolved. Runtime authorization is purpose-limited data handling, not a finding that player text or model output is licensed, original, safe, or reusable.

## Provenance taxonomy

| Provenance class | Definition | Default Phase 1–2 decision | Minimum evidence |
|---|---|---|---|
| `SRD_5_2_1_CC_BY_4_0` | Text, rule, table value, terminology, stat block, or structured/mechanical adaptation traceable to the pinned PDF | `ALLOW_REUSABLE` only for approved slice/test scope | Document ID and hash, 1-based PDF page plus section/entry, exact-vs-adapted flag, change description, reviewer/date |
| `PROJECT_ORIGINAL` | Independently created code, prose, worldbuilding, character, location, encounter, UI copy, or asset that is not copied or adapted from a denied or unknown source | `ALLOW_REUSABLE` after originality and brand review | Creator, creation date, source/input declaration, review record, and asset rights record when applicable |
| `PLAYER_AUTHORED_RUNTIME_INPUT_UNTRUSTED` | Ordinary choices and free text authored by a player for the active session, such as an action, reply, character name, or short session-specific description; it excludes uploaded files and pasted/imported published content | `ALLOW_RUNTIME_ONLY` for visibility-scoped active-session context, session-scoped local recall, local session persistence, and user-initiated export; untrusted and never rules-authoritative | Session/user pseudonymous ID, timestamp, declared visibility, origin channel, safety/injection disposition, and local retention/export status |
| `RUNTIME_GENERATED_UNREVIEWED` | Model narration generated at runtime. Admitted input provenance is recorded only as lineage; it does not confer an allow, originality, licensing, or safety conclusion on the output | `ALLOW_RUNTIME_ONLY` for private Phase 1B/2 display, local session persistence, and user-initiated session export after runtime checks; never authoritative rules or reusable source content | Model/config and prompt versions, input-object lineage set, generation date, content checks, and non-authoritative marker |
| `THIRD_PARTY_SEPARATELY_LICENSED` | Material offered under a license other than the pinned SRD license | `DENY` under this initial baseline until A7 records license compatibility and written approval | Complete license/source chain, permitted-use analysis, attribution/notice requirements, approval |
| `PUBLIC_DOMAIN_CANDIDATE` | Material asserted to be in the public domain | `UNKNOWN` until status and jurisdictional basis are documented; then requires explicit allowlist amendment | Author/source, publication facts, jurisdictional basis, reviewer/date |
| `DENIED_SOURCE` | Known source outside the initial baseline or material prohibited below | `DENY` | Source and denial reason; retain only enough metadata to prevent re-entry |
| `UNKNOWN` | Missing, ambiguous, mixed, machine-generated without trace, or unsupported provenance | `UNKNOWN` and blocked | None is sufficient until resolved |

Every admitted object must record: stable object ID; provenance class; admission decision; authorized-use scope; slice/test scope; creator, source, or runtime origin; applicable reviewer and date; and a trademark-screen result. Sourced reusable material additionally requires its source document ID, locator, license, exact/adapted status, and change description. Runtime classes instead require the lineage and handling evidence stated in the table. Rules-bearing derived fields retain the originating SRD locator. Hashes identify the source bytes; they do not replace locators or review.

## Initial allowlist

Only these uses are admitted:

- SRD 5.2.1 rules material from the pinned PDF that is explicitly selected by the Phase 2 slice coverage matrix, plus the minimum SRD material needed to test it.
- Deterministic data structures, calculations, identifiers, and implementation logic derived from that selected SRD material, with the source and transformation recorded. Reformatting a rule into software does not make its SRD provenance disappear.
- Independently created product code and original narrative content—adventure, setting, scenes, NPCs, locations, dialogue, descriptions, safety copy, and UI copy—after an originality and brand review.
- Original or separately commissioned assets only when the project holds the necessary rights and records the creator, grant, restrictions, and source files. No external asset is “original” merely because it was downloaded or generated.
- Ordinary player-authored choices and free text under `PLAYER_AUTHORED_RUNTIME_INPUT_UNTRUSTED`, solely for visibility-scoped active-session context and session-scoped local recall, local persistence, and user-initiated export. This input is untrusted data, never an instruction or rules authority, and may affect state only through validated commands. Injection, safety, visibility, and brand controls apply before it reaches any privileged component.
- Runtime model narration in private Phase 1B/2 evaluation only when it is independently recorded as `RUNTIME_GENERATED_UNREVIEWED`, cannot write authoritative game state, and passes the applicable content controls. Its admitted inputs are lineage evidence only; they do not make the output allowed reusable content or project-original material.

The reusable allowlist is the intersection of valid provenance and approved slice scope. Runtime-only classes have only the narrow data flows stated above. Neither gate covers the whole SRD or grants a general license to use other fifth-edition material.

## Denylist

The following are blocked from Phase 1–2 content and model context unless a future written policy amendment and any required qualified review explicitly admit them:

- SRD 5.1, SRD 5.2.0, other editions, and mixed-version rules. This is a version-control denial, not a claim that those SRDs are unlawful to use.
- D&D Beyond Basic Rules; Player’s Handbook, Dungeon Master’s Guide, Monster Manual, supplements, adventures, settings, marketplace content, Sage Advice text, and other official material outside the pinned PDF.
- Purchased or user-owned modules and books, including file upload, OCR, URL ingestion, and pasted excerpts intended to import their content. Access or ownership of a copy is not a provenance license for this product to ingest, adapt, transmit, retain, or redistribute it. Ordinary session-specific player choices and free text are handled separately as untrusted runtime data; that narrow path is not a module/content-ingestion feature.
- DMsGuild-only material, fan content, wikis, forums, streams, videos, actual-play transcripts, third-party books, and homebrew unless separately licensed and approved under a later amendment.
- Named settings, characters, plots, locations, distinctive monsters, items, art, maps, lore, or other brand identity omitted from SRD 5.2.1. Do not recreate them by paraphrasing or by asking a model to imitate or rename them.
- Wizards, D&D, D&D Beyond, dragon-ampersand, book-layout, logo, trade-dress, or “official” branding uses outside the exact attribution and any separately cleared compatibility statement.
- Art, audio, fonts, maps, tokens, data sets, or code with missing/incompatible terms; search-result thumbnails and “free online” content are not evidence of permission.
- Player-authored runtime input or AI output copied into a reusable rule, adventure, training, cross-session retrieval, evaluation, or marketing corpus before separate human provenance, similarity, brand, and rights review. A user statement of ownership or a model-provider label is not proof of reusable rights or originality.
- Any object with an unknown field, unclear source, conflicting license, unverifiable author, or inseparable mixture of allowed and denied material.

Research documents may cite external sources to establish facts. Citation does not make their expressive content eligible for the game corpus.

## Unknown and exception handling

`UNKNOWN` fails closed exactly like `DENY` for builds and tests. Quarantine the object outside content, prompt, fixture, retrieval, export, and release paths. Record how it arrived and resolve it by one of three actions:

1. trace it to the pinned SRD and add the required locator/transformation record;
2. replace it with independently created original material without consulting or paraphrasing the denied expression; or
3. remove it.

Only A7 may record a provenance reclassification. Adding a new source class or permitting third-party material requires a versioned policy amendment; owner convenience cannot waive this control. Suspected contamination triggers quarantine of downstream derivatives until their source chain is reviewed.

Ordinary in-session player text does not become `UNKNOWN` merely because it is informal: it receives the explicit `PLAYER_AUTHORED_RUNTIME_INPUT_UNTRUSTED` class and its narrow runtime authorization. If the input is an upload, a long pasted excerpt, or otherwise appears to be a book, module, article, or reusable source being ingested, that authorization ends; classify it as `DENIED_SOURCE` or `UNKNOWN`, quarantine it, and do not place it in model context or an export assembled by the product.

## Phase-specific controls

### Phase 1A — deterministic mechanics

- Verify the PDF hash before ingestion; never fetch “latest” during a build.
- Ingest only entries selected in the accepted coverage matrix, and require a page/section locator for every rules-bearing record.
- Reject extra, missing-provenance, mixed-version, and unknown objects automatically.
- Keep original narrative out of rules authority, and keep narrative labels from silently introducing mechanics.

### Phase 1B — isolated model feasibility spike

- Construct mock state and engine responses only from admitted SRD-derived or project-original fixtures.
- Treat simulated player messages as `PLAYER_AUTHORED_RUNTIME_INPUT_UNTRUSTED` test fixtures with no instruction authority. Do not turn player text into reusable content merely because it appeared in an evaluation trace.
- Keep model output test-only and independently `RUNTIME_GENERATED_UNREVIEWED`; input provenance is lineage only, and the output cannot seed later content or rule corpora without the separate review and reclassification required above.
- Record and review any protected-name, recognizable-lore, passage-similarity, or false-endorsement failure as a content-boundary defect.

### Phase 2 — private vertical slice

- Use an original adventure and original canon. Retrieval and prompt assembly may access only admitted objects appropriate to the model’s visibility scope.
- Accept ordinary player choices and free text only as untrusted, non-authoritative `PLAYER_AUTHORED_RUNTIME_INPUT_UNTRUSTED`. It may enter visibility-scoped active-session context, session-scoped local recall, local game records, and user-initiated session export. It may not enter centralized raw-text telemetry or be promoted into reusable rules, adventures, training/evaluation sets, cross-session retrieval, or marketing without separate review and reclassification.
- Generated narration is independently `RUNTIME_GENERATED_UNREVIEWED`. It may be displayed, persisted locally with the session, and included in a user-initiated session export after runtime checks. Record links to input provenance only as lineage; the output does not inherit `ALLOW_REUSABLE`, `PROJECT_ORIGINAL`, licensing, originality, or safety status from those inputs. Quarantine output that introduces denied or unknown material. Promotion to reusable content requires the stated human provenance, similarity, brand, and rights review and a recorded reclassification.
- Preserve the exact notice and change indication with any distributed SRD-derived material. Keep SRD-derived and original portions distinguishable in the ledger.
- Any proposal to add user imports, third-party adventures, public sharing, a content marketplace, or a new rules version reopens this policy before implementation.

## Trademark, branding, and original-content boundary

CC BY 4.0 licenses copyright and related rights described in the license; it does **not** license patent or trademark rights and it prohibits implying sponsorship, endorsement, connection, or official status. The pinned PDF says not to add other attribution to Wizards or its parent or affiliates, while permitting a statement that a work is “compatible with fifth edition” or “5E compatible.”

For Phase 1–2:

- Use an original product name, logo, visual system, domain, metadata, and store/marketing identity.
- The working phrase/title **“AI Dungeon Master for D&D 5e” is internal only**. Under D12 it is quarantined from every public product name, repository title, package identifier, domain, UI title, store listing, search/social metadata, promotional asset, and announcement pending qualified review of “Dungeon Master,” D&D marks, and any compatibility wording.
- Do not use Wizards or D&D marks, logos, trade dress, or “official/approved/licensed by” claims as product identity. The mandatory attribution belongs in Legal/Credits, not in the product name or promotional badge.
- Do not treat an SRD term as cleared for prominent brand use merely because it appears in licensed rules text.
- Defer even the permitted compatibility wording in public-facing branding until qualified review considers placement, prominence, and the full presentation.

Project-original content is not automatically licensed under CC BY 4.0 merely because it sits beside SRD material. It must be recorded separately. Conversely, adapted SRD rules do not become `PROJECT_ORIGINAL` because they were paraphrased, normalized, encoded, or combined with original prose. Model output likewise does not become `PROJECT_ORIGINAL` merely because all recorded inputs were admitted; input provenance is lineage, not an originality or rights conclusion. Mixed works need field/span-level provenance, the SRD notice, the change indication, and terms that do not impose additional restrictions on recipients’ exercise of the CC-licensed portions.

## Verification and release checks

Before every Phase 1–2 evidence run or distributable build:

1. recompute the PDF SHA-256 and compare it to the pinned checksum;
2. require zero `UNKNOWN`, `DENY`, missing-locator, or missing-review objects;
3. confirm the exact attribution block and neutral change indication are present wherever required;
4. confirm all included SRD records are in the accepted slice/test allowlist;
5. confirm runtime-only player input and model output have not been promoted into reusable corpora and that visibility, local-retention, export, injection, and non-authority controls hold;
6. scan product name, UI, prompts, outputs, assets, metadata, and marketing for denied brands/lore and implied endorsement, including any public occurrence of the quarantined working phrase/title;
7. verify original-content and asset records; and
8. verify product terms and technical controls do not purport to remove rights CC BY 4.0 grants in SRD-derived portions.

## Qualified-review issue that remains open

This evidence supports the internal Phase 1–2 control boundary; it is not legal advice. Before any public or commercial release, qualified counsel should review at least: the product name/logo/domain and full trademark presentation; exact attribution and change-note placement across app, repository, exports, and store materials; terms, DRM, and license carve-outs for SRD-derived portions; commissioned or model-generated assets and narration; user uploads/imports; and any separately licensed third-party content. That review is the unresolved legal-clearance item. It does not justify weakening the fail-closed policy while review is pending.
