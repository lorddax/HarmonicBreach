# Harmonic Breach

**Harmonic Breach: Delve Protocol** is a cooperative, card‑driven tabletop game where Heroes enter corrupted “Delves” – pockets of reality overwritten by video‑game logic – and work together to debug the world.

## Project Goals

- Develop a publishable tabletop game with strong systems design.
- Maintain a clean, agent‑friendly spec for AI design tools and dev tools.
- Support campaign play, tooling, and future digital implementations.

## Core Concepts

- **Tag‑based Challenges:** Delve cards specify Required Tags (Combat, Technology, Logic, Agility, Perception, etc.). Heroes commit cards to cover tags.
- **Tiered Outcomes:** Each Challenge resolves to one of four tiers:
  - Strong Success
  - Success
  - Low Fail
  - High Fail
- **Drive Tokens:** Body, Mind, and Agility Drive pay for cards and abilities; they never directly modify success thresholds.
- **Tableaus:** Each Hero maintains a personal tableau representing their current “runtime configuration” of abilities.
- **Perfect Counters:** Rare cards that, against specific Challenge types, guarantee a Strong Success when committed.

See `design/core_rules.md` for the rules‑level reference.

## Campaign & Progression

Harmonic Breach supports episodic campaigns:

- Multiple Delves linked by a shared story arc.
- Kept Challenges (Strong Success / Success) become post‑session rewards.
- Rewards fuel Avatar upgrades, tableau expansion, and team‑wide unlocks.

See `design/campaign_progression.md` for details.

## Repository Structure

Planned/typical layout:

- `design/`
  - `README.md` – design team roles, pipeline, and folder conventions.
  - `core_rules.md` – core mechanical rules (tiered success, Drive, tableaus, Perfect Counters).
  - `campaign_progression.md` – long‑term progression and reward systems.
  - `resonance_spec.md` – Resonance deck, tableau, and escalation rules.
  - `generated/` – GameGrammar snapshots (JSON, Markdown, PDF).
  - `agent_output/` – working drafts from Perplexity/Gemini (gitignored).
- `engine/` (or `tools/`)
  - Card generators (physical print-ready and digital), rough simulator to model the physical game, validators, and related tooling. Consume `design/` specs and `design/generated/` JSON.
- `notes/`
  - Working documents, design diaries, and open questions.

## Collaboration Notes

Design is run as a multi-agent team led by a human executive producer/designer. The **design team roles and pipeline** (GameGrammar as paired developer, Perplexity/Gemini as design collaborators, Cursor as integrator, plus folder and source-of-truth conventions) are documented in **`design/README.md`**.

**Source of truth:** The Markdown specs in `design/` are canonical; update them first, then reflect changes in generated snapshots (e.g. GameGrammar JSON in `design/generated/`) and tooling.
