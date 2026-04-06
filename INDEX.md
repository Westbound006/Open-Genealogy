# Open-Genealogy Index

Complete catalog of prompts, scripts, and tools.

---

## Documentation

| File | Description |
|------|-------------|
| [GETTING-STARTED.md](GETTING-STARTED.md) | Guide for new users: GitHub basics, repository overview, GRA v8 usage |
| [ANNOTATED-INDEX.md](ANNOTATED-INDEX.md) | Detailed descriptions of all sections (~125 words each) |

---

## Research & GPS Methodology

| File | Description | Status |
|------|-------------|--------|
| [research-assistant-v8.5-compact.md](research/research-assistant-v8.5-compact.md) | GPS-aligned compact research assistant (~1,000 words) | **recommended** |
| [research-assistant-v8.md](research/research-assistant-v8.md) | Full GPS-based research assistant (669 lines) | stable |
| [research-assistant-v8-compact.md](research/research-assistant-v8-compact.md) | Token-efficient v8 | stable |
| [research-with-citations-v7.md](research/research-with-citations-v7.md) | Web research with GPS methodology | stable |
| [web-research-v7.md](research/web-research-v7.md) | Compact web search prompt | stable |
| [research-assistant-v7.md](research/research-assistant-v7.md) | Previous full version | archive |
| [research-assistant-v7-compressed.md](research/research-assistant-v7-compressed.md) | Token-efficient v7 | archive |
| [research-assistant-v6.1.md](research/research-assistant-v6.1.md) | Earlier full version | archive |
| [research-assistant-v6.1-compressed.md](research/research-assistant-v6.1-compressed.md) | Token-efficient v6.1 | archive |
| [contract-first-genealogy-v3.1.md](research/contract-first-genealogy-v3.1.md) | Contract-lock workflow | stable |
| [research-agent-assignment-v2.1.md](research/research-agent-assignment-v2.1.md) | Research agent specification | stable |

**Reference:** [evidence-terminology.md](research/reference/evidence-terminology.md)
**Archive:** [research/archive/](research/archive/) — legacy versions (research-assignment-v0, research-with-citations-v2)

---

## Transcription & HTR

| File | Description | Status |
|------|-------------|--------|
| [ocr-htr-v08.md](transcription/ocr-htr-v08.md) | Comprehensive diplomatic transcription | **recommended** |
| [jewish-transcription-v2.md](transcription/jewish-transcription-v2.md) | Jewish documents: Hebrew, Yiddish, Ladino, vital records, ketubot, matzevot | **recommended** |
| [humphries-method-v1.md](transcription/humphries-method-v1.md) | Minimalist HTR | stable |

**Archive:** [transcription/archive/](transcription/archive/)

---

## Image Analysis

| File | Description | Status |
|------|-------------|--------|
| [deep-look-v2.md](image-analysis/deep-look-v2.md) | 10-layer forensic image analysis with structured data extraction and catalog record | **recommended** |
| [Deep-Look-v2-Four-Models-Full-Results.pdf](image-analysis/Deep-Look-v2-Four-Models-Full-Results.pdf) | Companion: same prompt tested on Claude, GPT-5.4, Gemini, Grok with comparison matrix | reference |
| [universal-image-analysis-v3.md](image-analysis/universal-image-analysis-v3.md) | 9-layer forensic image analysis protocol | previous |

---

## Hebrew Headstones

| File | Description | Status |
|------|-------------|--------|
| [hebrew-headstone-helper-v9.md](hebrew-headstones/hebrew-headstone-helper-v9.md) | 10-phase forensic headstone analysis with gematria dating, patronymic identification, and confidence scoring (382 lines) | **recommended** |

**Related:** [jewish-transcription-v2.md](transcription/jewish-transcription-v2.md) (for documents, not headstones)

---

## Photo Restoration

| File | Description | Status |
|------|-------------|--------|
| [restoration-v2.md](photo-restoration/restoration-v2.md) | Universal restoration | **recommended** |
| [photo-conservator-v2.md](photo-restoration/photo-conservator-v2.md) | Conservation workflow | stable |
| [photo-reconstructor-v3.md](photo-restoration/photo-reconstructor-v3.md) | Severe damage reconstruction | stable |
| [damage-removal-v3.md](photo-restoration/damage-removal-v3.md) | Museum-grade restoration | stable |

**Archive:** [photo-restoration/archive/](photo-restoration/archive/)

---

## Writing Tools

| File | Description |
|------|-------------|
| [fact-extractor-v4.md](writing-tools/fact-extractor-v4.md) | Extract atomic facts |
| [fact-narrator-v4.md](writing-tools/fact-narrator-v4.md) | Facts to narrative |
| [conversation-abstractor-v2.md](writing-tools/conversation-abstractor-v2.md) | Conversation abstracts |
| [chat-summarizer-v3.md](writing-tools/chat-summarizer-v3.md) | Quick summaries |
| [document-distiller-v2.md](writing-tools/document-distiller-v2.md) | Distill documents |
| [lingua-maven-v9.md](writing-tools/lingua-maven-v9.md) | AHD-inspired language advisor with usage analysis and sensitivity review |
| [linguistic-profiler-v3.md](writing-tools/linguistic-profiler-v3.md) | Profile writing style |
| [narrative-assistant-v3.md](writing-tools/narrative-assistant-v3.md) | GPS-informed narratives and proof arguments |
| [image-citation-builder-v2.md](writing-tools/image-citation-builder-v2.md) | Image citations |
| [image-infographic-workflow-v1.md](writing-tools/image-infographic-workflow-v1.md) | Two-tier image/infographic workflow (Notebook LM + Claude Opus) |
| [infographic-v7.md](writing-tools/infographic-v7.md) | Infographic format (legacy) |
| [quick-editor-v3.md](writing-tools/quick-editor-v3.md) | Editorial cleanup |
| [quick-cleanup-v3.md](writing-tools/quick-cleanup-v3.md) | Grammar/readability (micro-prompt) |
| [content-decoder-v1.md](writing-tools/content-decoder-v1.md) | Clarify dense text |
| [transcript-resource-forge-v2.md](writing-tools/transcript-resource-forge-v2.md) | Transform transcripts into structured resources |

---

## AI Assistants

Complete AI personas for ongoing genealogical work.

| File | Description |
|------|-------------|
| [vibe-genealogy-assistant-v4.md](assistants/vibe-genealogy-assistant-v4.md) | Warm, story-first genealogy helper |
| [gedcom-analysis-v3.md](assistants/gedcom-analysis-v3.md) | GEDCOM file analysis specialist |
| [gedcom-builder-v1.md](assistants/gedcom-builder-v1.md) | GEDCOM file creation from research data |
| [gedcom-creator-mini.md](assistants/gedcom-creator-mini.md) | Compact GEDCOM creator for Custom GPTs |

---

## Skills (Claude Code)

Platform-specific tools combining prompts with companion scripts.
Requires [Claude Code](https://claude.ai/code).

| Folder | Description | Status |
| ------ | ----------- | ------ |
| [gra/](skills/gra/) | GPS-aligned genealogical research assistant (v8.5.1c + full + companion) | stable |
| [gedcom-creator/](skills/gedcom-creator/) | GEDCOM 5.5.1 file generator from natural language, JSON, or markdown | stable |

---

## GPT Configs

| File | Description |
|------|-------------|
| [open-geneagpt-v0.4.txt](gpt-configs/open-geneagpt-v0.4.txt) | Open GeneaGPT spec |
| [website-frontend-v3.txt](gpt-configs/website-frontend-v3.txt) | Domain-fronted GPT |

---

## Scripts

| File | Description | Status |
|------|-------------|--------|
| [transcribe-4o-chunk-v2.py](scripts/transcribe-4o-chunk-v2.py) | Long-audio transcription with chunking and overlap trimming | **recommended** |
| [batch_transcribe_v2.py](scripts/batch_transcribe_v2.py) | Batch wrapper — process a folder of audio files | **recommended** |
| [transcribe-4.py](scripts/transcribe-4.py) | Single-file transcription | stable |
| [transcribe-4o-chunk.py](scripts/transcribe-4o-chunk.py) | Long-audio chunking (v1) | legacy |
| [transcribe-v02.py](scripts/transcribe_v02.py) | Minimal reference | stable |

---

## Evaluation Framework

| Resource | Description |
|----------|-------------|
| [genealogical-writing-rubric.md](benchmark/rubrics/genealogical-writing-rubric.md) | GPS-derived 60-point rubric for evaluating published genealogical writing |
| [benchmark/](benchmark/) | Framework overview, methodology, and case study invitations |
| [ashe-county-nc/](benchmark/case-studies/ashe-county-nc/) | Case study: Claude, ChatGPT, Gemini, Grok on Ashe County research |

---

## Autonomous Research Prompts

12 Claude Code workflows for structured autonomous research. Each defines a goal, search strategy, and verification steps.

| File | Description |
|------|-------------|
| [01-tree-expansion.md](prompts/01-tree-expansion.md) | Expand the family tree by finding new ancestors |
| [02-cross-reference-audit.md](prompts/02-cross-reference-audit.md) | Audit and resolve cross-reference discrepancies |
| [03-findagrave-sweep.md](prompts/03-findagrave-sweep.md) | Locate burial records via Find a Grave |
| [04-gedcom-completeness.md](prompts/04-gedcom-completeness.md) | Identify gaps in a GEDCOM file |
| [05-source-citation-audit.md](prompts/05-source-citation-audit.md) | Audit source citations for completeness |
| [06-unresolved-persons.md](prompts/06-unresolved-persons.md) | Work through unidentified individuals |
| [07-timeline-gap-analysis.md](prompts/07-timeline-gap-analysis.md) | Find and fill timeline gaps |
| [08-open-question-resolution.md](prompts/08-open-question-resolution.md) | Systematically resolve open research questions |
| [09-bygdebok-extraction.md](prompts/09-bygdebok-extraction.md) | Extract data from Norwegian farm books |
| [10-colonial-records-search.md](prompts/10-colonial-records-search.md) | Search colonial American records |
| [11-immigration-search.md](prompts/11-immigration-search.md) | Trace immigration and emigration records |
| [12-dna-chromosome-analysis.md](prompts/12-dna-chromosome-analysis.md) | Analyse DNA chromosome painting results |

---

## Workflows

Step-by-step procedures for common research tasks.

| File | Description |
|------|-------------|
| [getting-started.md](workflows/getting-started.md) | Set up your vault and run your first research session |
| [new-ancestor-intake.md](workflows/new-ancestor-intake.md) | Process a newly discovered ancestor |
| [discrepancy-resolution.md](workflows/discrepancy-resolution.md) | Resolve conflicts between sources |
| [document-triage.md](workflows/document-triage.md) | Triage and prioritise incoming documents |
| [ocr-pipeline.md](workflows/ocr-pipeline.md) | OCR and transcription pipeline |
| [oral-history-protocol.md](workflows/oral-history-protocol.md) | Record and integrate oral histories |
| [phase-planning.md](workflows/phase-planning.md) | Plan a research phase with defined goals |

---

## Archives — Regional Record Guides

Where to find records by country and region. Notes on free vs. subscription access.

| File | Region |
|------|--------|
| [england-wales.md](archives/england-wales.md) | England & Wales |
| [scotland.md](archives/scotland.md) | Scotland |
| [ireland.md](archives/ireland.md) | Ireland |
| [france.md](archives/france.md) | France |
| [germany.md](archives/germany.md) | Germany |
| [austria.md](archives/austria.md) | Austria |
| [hungary.md](archives/hungary.md) | Hungary |
| [netherlands.md](archives/netherlands.md) | Netherlands |
| [norway.md](archives/norway.md) | Norway |
| [sweden.md](archives/sweden.md) | Sweden |
| [poland.md](archives/poland.md) | Poland |
| [russia-ukraine.md](archives/russia-ukraine.md) | Russia & Ukraine |
| [spain-portugal.md](archives/spain-portugal.md) | Spain & Portugal |
| [italy.md](archives/italy.md) | Italy |
| [jewish-genealogy.md](archives/jewish-genealogy.md) | Jewish genealogy (cross-national) |
| [african-american.md](archives/african-american.md) | African American records |
| [usa-census.md](archives/usa-census.md) | USA — Census |
| [usa-vital-records.md](archives/usa-vital-records.md) | USA — Vital records |
| [usa-immigration.md](archives/usa-immigration.md) | USA — Immigration |
| [usa-colonial.md](archives/usa-colonial.md) | USA — Colonial records |
| [canada.md](archives/canada.md) | Canada |
| [mexico-latin-america.md](archives/mexico-latin-america.md) | Mexico & Latin America |
| [australia-nz.md](archives/australia-nz.md) | Australia & New Zealand |

---

## Vault Template

Obsidian-compatible markdown templates for organising research. Works with any text editor.

| File | Description |
|------|-------------|
| [_Index.md](vault-template/_Index.md) | Master index for your research vault |
| [Family_Tree.md](vault-template/Family_Tree.md) | Family tree overview |
| [Research_Log.md](vault-template/Research_Log.md) | Dated log of research sessions |
| [Research_Strategy.md](vault-template/Research_Strategy.md) | Current research strategy and priorities |
| [Open_Questions.md](vault-template/Open_Questions.md) | Tracked open research questions |
| [Unresolved_Persons.md](vault-template/Unresolved_Persons.md) | Individuals not yet placed in the tree |
| [Timeline.md](vault-template/Timeline.md) | Chronological event timeline |
| [Data_Inventory.md](vault-template/Data_Inventory.md) | Inventory of sources and documents held |
| [Witness_Network.md](vault-template/Witness_Network.md) | FAN cluster tracking |
| [Genetic_Profile.md](vault-template/Genetic_Profile.md) | DNA test results and interpretation |
| [Chromosome_Painting.md](vault-template/Chromosome_Painting.md) | Chromosome segment mapping |
| [vault-template/templates/](vault-template/templates/) | Per-person, transcription, certificate templates |

---

## Examples

Anonymised worked examples showing research patterns and decision-making.

| File | Demonstrates |
|------|-------------|
| [tree-expansion-session.md](examples/tree-expansion-session.md) | Tree expansion over 8 iterations |
| [cross-reference-audit.md](examples/cross-reference-audit.md) | Finding and resolving discrepancies |
| [dna-to-genealogy-mapping.md](examples/dna-to-genealogy-mapping.md) | Connecting DNA results to documented lines |
| [name-resolution.md](examples/name-resolution.md) | One ancestor appearing under multiple names |
| [colonial-deep-dive.md](examples/colonial-deep-dive.md) | Researching a colonial American ancestor |

---

## License

[Creative Commons BY-NC-SA 4.0](LICENSE)
