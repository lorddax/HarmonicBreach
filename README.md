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
  - `core_rules.md` – core mechanical rules (tiered success, Drive, tableaus, Perfect Counters).
  - `campaign_progression.md` – long‑term progression and reward systems.
  - `resonance_spec.md` – (planned) Resonance deck and escalation rules.
- `design/generated/`
  - GameGrammar JSON design snapshots.
- `engine/`
  - Future simulators, validators, and digital tooling.
- `notes/`
  - Working documents, design diaries, and open questions.

## Collaboration Notes

This repo is used by:

- Human designer(s) iterating on rules and content.
- AI design assistants (e.g., GameGrammar) generating structured JSON.
- AI coding tools (Cursor, Kiro, etc.) building simulators and helpers.

**Source of truth:** Update the Markdown specs in `design/` first, then reflect changes in JSON, tools, and printed materials.
