# Harmonic Breach: Core Rules

This document captures the current core mechanical rules for Harmonic Breach, focusing on challenge resolution, card commitment, Drive, and Perfect Counters. Resonance and campaign details are specified in separate documents.

## 1. Play Overview

- Cooperative, card‑driven game for 3–4 Heroes.  
- Players enter a Delve built from Base, POI, and Theme/Imprint cards.  
- Each round:  
  1. **Resonance Phase** – Delve escalates and reveals the next Challenge.  
  2. **Challenge Phase** – Heroes commit cards and spend Drive.  
  3. **Resolution Phase** – Tags are matched to determine a tiered outcome.  
  4. **Refresh Phase** – Drive and hands are refreshed; tableaus are managed.

## 2. Tags and Required Tags

- Hero and Delve cards have one or more **tags** (e.g., Combat, Technology, Logic, Agility, Perception).  
- Each Challenge/Delve card lists **Required Tags** (1–4 tags total) instead of numeric thresholds.  
- Tags represent the "type of answer" the Delve is asking for; matching tags is how players succeed.

## 3. Committing Cards vs Utility Plays

### 3.1 Commitment for Resolution

- During each Challenge, **each Hero may commit exactly 1 card** from hand.  
- Only committed cards count for matching Required Tags and determining the outcome tier.  
- Committed cards are revealed simultaneously in the Resolution Phase.

### 3.2 Utility Plays

- In addition to their 1 committed card, Heroes may **play or activate other cards** by paying Drive costs.  
- Utility effects can:  
  - Draw or filter cards.  
  - Move cards into or out of tableau.  
  - Manipulate tags on cards.  
  - Provide information or set up future Challenges.  
- Unless explicitly stated, utility cards **do not** count as committed cards for outcome tiers.

### 3.3 Exhaustion

- Any card committed to a Challenge is **spent for the rest of the Delve**, unless a card explicitly returns it to hand, deck, or tableau.  
- Cards in tableau remain until replaced or moved; their ongoing abilities only function while they are in tableau.

## 4. Tiered Outcome System

Each Challenge resolves to exactly one of four outcome tiers based on how well the committed cards cover the Required Tags.

Let "Required Tags" be the tags listed on the Challenge card, and "Matched Tags" be the subset of those tags present among all committed Hero cards (after any tag‑manipulation effects).

- **Strong Success**  
  - Condition: All Required Tags are matched, or a valid Perfect Counter is used.  
  - Result:  
    - The Challenge is cleared.  
    - The Challenge card is **kept** as a session reward for post‑session exchange.  
    - Apply the card's **Strong Success** effect (a boon, such as extra rewards or an environmental advantage).

- **Success**  
  - Condition: At least **2 Required Tags** are matched, but not all.  
  - Result:  
    - The Challenge is cleared.  
    - The Challenge card is **kept** as a session reward.  
    - Apply the card's **Success** effect (moderate benefit; no bane).

- **Low Fail**  
  - Condition: Exactly **1 Required Tag** is matched.  
  - Result:  
    - The Challenge is cleared.  
    - The Challenge card is **not kept** (no reward from this card).  
    - Apply the card's **Low Fail** effect (usually minor or neutral).

- **High Fail**  
  - Condition: **0 Required Tags** are matched.  
  - Result:  
    - The Challenge is cleared.  
    - The Challenge card is **not kept**.  
    - Apply the card's **High Fail** effect (a significant penalty; may also interact with Resonance).

Challenge cards express their specific outcomes in four blocks (Strong Success / Success / Low Fail / High Fail) using this shared tier logic.

## 5. Drive Tokens

- There are three Drive types: **Body, Mind, Agility**.  
- Each Avatar generates a specific mix of Drive during the Refresh Phase.  
- **Drive is never used as a numeric success threshold.**  
- Drive is used only to:  
  - Pay costs to play cards from hand.  
  - Activate tableau abilities.  
  - Trigger Avatar powers and utility effects.

Drive therefore controls **how much** a team can do each round, not **whether** a Challenge succeeds; success is determined by tags and tiers.

## 6. Tableaus

- Each Hero has a personal **tableau** with 3–5 slots (depending on progression).  
- Cards in tableau represent that Hero's current "runtime configuration" of tools and abilities.  
- General rules:  
  - Tableau cards have ongoing or repeatable abilities that require Drive to activate.  
  - Replacing a tableau card typically costs Drive, with costs escalating for multiple replacements in a round.  
  - Tableau abilities focus on setup and support (card draw, Drive efficiency, tag manipulation, recursion), not on raw numeric threshold bonuses.

## 7. Perfect Counter

- Some Hero cards show a **Perfect Counter icon** associated with specific Challenge types or tags (e.g., "Perfect Counter: Combat–Environmental").  
- When a Hero commits a card with a Perfect Counter icon against a **matching Challenge**, that card automatically upgrades the outcome to **Strong Success**, regardless of exact tag coverage, as long as basic play conditions are met.  
- Perfect Counter cards are intended to be rare, high‑impact tools and should be limited per deck and/or gated by conditions or costs.

## 8. Kept vs Cleared Challenges

- **Kept** Challenges (Strong Success, Success):  
  - Set aside in a session Reward Pool.  
  - At the end of the session, they are exchanged according to the campaign/progression rules (see `campaign_progression.md`).

- **Cleared but not kept** Challenges (Low Fail, High Fail):  
  - Removed from play for this Delve.  
  - Provide no direct reward, though they may still have on‑tier effects (banes/boons) that were resolved when cleared.

---

This file is intended as the reference for rules‑level work and for tooling (simulators, validators, etc.). Any future edits to core resolution, Drive usage, or Perfect Counter behavior should update this document first.