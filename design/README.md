# Design Team & Pipeline

This document describes how the Harmonic Breach design team is structured and how artifacts flow between tools and the repo. It is a working description and will be refined through discussion.

## Design Team Roles

| Role | Tool | Function |
|------|------|----------|
| **Executive producer / designer** | Human lead | Final decisions, direction, and prioritisation. Integrates feedback and owns the published design. |
| **Paired game developer** | [GameGrammar](https://gamegrammar.dynamindresearch.com/) (Claude Sonnet 4) | Traditional “designer + developer” pair in physical board game design. Turns discussed changes into structured snapshots of the current game state. Produces **Markdown, PDF, or JSON**; its JSON is the primary machine-readable feed for card generators and simulators. Keeping specs and GameGrammar snapshots aligned avoids drift between docs and tooling. |
| **Design collaborator (research & models)** | Perplexity Pro | Second designer. Leverages **multi-model access** for research, precedent, and drafts: comparable games, production considerations, citation-backed alternatives. Strong for "what else exists?" and evidence-based suggestions. Outputs are drafts; not source of truth. |
| **Design collaborator (multimodal)** | Gemini Pro | Third designer. Leverages **multimodal in/out** (text + images) for generative iteration and review: card mockups, layout feedback, visual variants, or parsing sketches/reference art. Fits visual iteration for playable prototypes and asset direction. |
| **Integrator / executor** | Cursor | Lives in the repo and design docs. Merges other agents’ outputs into the canonical specs, maintains folder structure and **design-support tooling**. Implements and maintains **card generators** (physical print-ready and digital assets) and a **rough simulator** to model the physical game; keeps specs and JSON conventions (e.g. `resonance_spec.md` §9) in a form those tools can consume. Does not replace design judgment. |

## Source of Truth

- **Canonical design:** The Markdown specs in `design/` (`core_rules.md`, `campaign_progression.md`, `resonance_spec.md`, etc.) are the source of truth for rules and systems.
- **Snapshots:** GameGrammar outputs in `design/generated/` (JSON, and any Markdown/PDF placed there) are **snapshots** of the game state at a point in time. They are generated from discussed changes and can be used by tooling; spec updates should be reflected there (or vice versa, by agreement).
- **Working drafts:** Outputs from Perplexity or Gemini that are not yet folded into the specs live in `design/agent_output/` and are **not** versioned (folder is in `.gitignore`). They are processed (e.g. by Cursor) into the canonical specs when the team agrees.

## Folder Conventions

- **`design/`** – Source-of-truth Markdown specs. Update these first; then reflect in generated snapshots and tooling.
- **`design/generated/`** – GameGrammar snapshots (JSON, Markdown, PDF). Tracked in git. Represents “current state” output from the paired developer.
- **`design/agent_output/`** – Working outputs from Perplexity Pro, Gemini Pro, or similar agents. Ignored by git. Use for drafts that will be merged into specs or discarded after discussion.

## Pipeline (Current Understanding)

1. **Discussion** – Lead and/or design collaborators (Perplexity, Gemini) explore ideas; GameGrammar may participate as the paired developer.
2. **Drafts** – Perplexity/Gemini outputs may be saved under `design/agent_output/` for review.
3. **Decisions** – Lead decides what to adopt; Cursor (or lead) merges chosen content into the relevant `design/*.md` specs.
4. **Snapshots** – GameGrammar produces snapshots (e.g. JSON) into `design/generated/` based on the current or agreed state.
5. **Tooling** – Specs and generated JSON feed the supporting tools below (see `design/resonance_spec.md` §9 for JSON conventions).

Refinement of this pipeline and of the role descriptions above is expected as the team workflow evolves.

## Supporting Tools (Planned)

Tools to support creation of **playable prototypes** and to model the physical game:

- **Card generators**
  - **Physical:** Produce print-ready card assets (e.g. from structured data or GameGrammar JSON) for physical prototyping and playtesting.
  - **Digital:** Produce assets in formats suitable for use in a digital simulator or tabletop sim (same source data where possible).
- **Rough simulator**
  - A lightweight digital model of the physical game (e.g. Delve flow, Resonance tableau, tier outcomes) to playtest and iterate without always requiring physical components. Consumes specs and/or `design/generated/` JSON.

These tools are implemented and maintained in-repo (e.g. under `engine/` or a dedicated `tools/`); they consume canonical specs and `design/generated/` snapshots so that design changes flow through to prototype and simulation in one pipeline.
