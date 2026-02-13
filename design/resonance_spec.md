# Harmonic Breach: Resonance System

This document defines the updated Resonance mechanics for Harmonic Breach. It replaces older numeric “+1/+2/+3 to thresholds” escalation with a single, unified system based on a **Resonance Deck** and a visible **Resonance Tableau**. The tableau itself functions as the “Resonance track” and as the early‑boss trigger.[file:14]

## 1. Design Intent (Context for Future Work)

Resonance should:
- Feel like corrupted game logic accumulating in the Delve, not just a difficulty number.[file:14]
- Be **visible** on the table so players can read how close they are to disaster.
- Interact with the existing **tag‑based, 4‑tier outcome system** instead of raw numeric thresholds.[file:14]
- Give players **meaningful levers** to delay, accelerate, or shape escalation at a cost.
- Avoid death spirals where a few bad failures make the game mathematically unwinnable.[file:14]

The system below is designed around those goals and around an earlier, well‑received prototype where players could see a “big bad” moving through a deck and decide when to push or pull; here, that feeling is captured via the tableau instead of physically cycling a 100‑card stack.

## 2. Core Concepts

- **Resonance Deck**: A small deck of scenario‑specific escalation cards.
- **Resonance Tableau**: A shared row of slots where Resonance cards are placed; its state (how many cards, and which are face‑up) *is* the current Resonance.
- **Boss Card**: For each Delve, the boss defines how the Resonance Tableau behaves and when the boss appears.[file:14]

There is no separate numeric Resonance marker. Players read stability directly from the tableau.

## 3. Resonance Deck

### 3.1 Composition

The Resonance Deck is built per Delve from:[file:14]

- **Base Resonance cards** (generic to all Delves).
- **Theme Resonance cards** (e.g., Horror, Cyberpunk, Platformer).
- Optional **POI Resonance cards** (location‑specific).

Typical size: **8–12 cards**, tuned per difficulty.

Each Resonance card includes:

- Tags (e.g., Horror, Technology, Threat, Boon).
- Whether it enters the tableau **face‑up** or **face‑down** by default.
- Whether it counts toward **boss trigger conditions** (Threat) or is primarily a beneficial/neutral effect (Boon/Neutral).

### 3.2 When Resonance Cards Are Drawn

During each **Resonance Phase**, before revealing the next Challenge:[file:14]

1. Draw the **top card** of the Resonance Deck.
2. Resolve any **on‑reveal** effects.
3. Unless the card says otherwise, place it into the **Resonance Tableau** following the normal placement rules (see below).

Some cards may skip the tableau and resolve purely as Instants, but in general, resonance‑related effects should flow through the tableau to keep all escalation visible.

## 4. Resonance Tableau

The Resonance Tableau is a shared row of slots that shows the current corruption state.

### 4.1 Structure

The **Boss card** defines the tableau profile for that Delve:[file:14]

- `max_slots` (e.g., 3–5).
- Which tags or card types matter for boss triggers (e.g., Threat, Horror, Technology).
- Any special rules for face‑down cards (e.g., “face‑down cards do not count for triggers”).

Example: A boss might specify `max_slots = 4` and “Boss spawns when 3 or more face‑up Threat cards are present in the tableau.”

### 4.2 Card States

Each slot in the tableau may hold at most one Resonance card.

Cards have two states:

- **Face‑up**  
  - Ongoing rules text is active.  
  - Tags are visible and count for boss triggers.

- **Face‑down** (latent corruption)  
  - Does **not** apply its ongoing effect by default.  
  - Occupies a slot.  
  - Does **not** contribute tags to boss triggers, unless a card or boss text says otherwise.

### 4.3 Card Entry

- By default, Resonance cards enter **face‑up** into the leftmost empty slot.
- Cards with “enter face‑down” explicitly override this.
- If all slots are full when a card would enter:
  - Apply any **on‑overflow** rule from the boss (e.g., immediate boss spawn; discard oldest card; force flips).

### 4.4 Reading Resonance

Players assess current Resonance by:

- How many **slots are occupied**.
- How many cards are **face‑up**.
- Which **tags** are showing on face‑up cards.

Different bosses care about different patterns, but the rules for reading the tableau are always the same.

This is intentionally replacing the previous “Resonance levels modify thresholds” system; difficulty is now expressed via visible cards and tags, not hidden math.[file:14]

## 5. Boss Triggers and Effects

### 5.1 Boss Triggers

Each boss defines one or more conditions that cause it to appear as the next Challenge. Examples:[file:14]

- **Full Tableau Trigger**  
  “When all slots are occupied, spawn the boss.”

- **Tag Threshold Trigger**  
  “When there are 3 or more Threat‑tagged cards face‑up, spawn the boss.”

- **Hybrid Trigger**  
  “When there are at least 2 Horror cards and the tableau is at least half full, spawn the boss.”

Triggers are checked at the **end of the Resolution Phase**, after tier outcomes and any flips/purges for that round.

### 5.2 Early and Late Boss

- Spawning the boss **early** (few cards / low Threat density) should generally provide a small tactical advantage (e.g., fewer stacked Resonance effects, weaker boss state).
- Spawning the boss **late** (full tableau, many Threat tags) can grant the boss additional powers or harsher failure tiers.

These modifications are written directly on the boss card (e.g., “If the tableau was full when I spawned, all my failures increase Resonance or discard extra cards”), keeping the logic local.[file:14]

This preserves the earlier “visible boss approaching” idea from the 100‑card deck prototype, but via a small, manageable structure.

## 6. Player Interaction and Agency

Resonance should never feel like pure punishment; players must have levers to manage the tableau at a cost.

### 6.1 Standard Player Options

Across all bosses and Delves, the following standard interactions exist (cards can add exceptions):

- **Purge (Strong Success Option)**  
  After resolving a Challenge with **Strong Success**, instead of some or all of the usual tier bonus, the team may **discard 1 Resonance card from the tableau** (face‑up or face‑down).

- **Flip (Success / Strong Success Option)**  
  After a **Success** or **Strong Success**, the team may **flip 1 face‑up Resonance card face‑down**.

- **Quarantine (Refresh Phase Action)**  
  During Refresh, the team may spend a scenario‑defined amount of Drive (usually mixed Body/Mind/Agility) to **exhaust** a face‑up Resonance card for the next round. An exhausted Resonance card:
  - Remains in the tableau and counts for boss triggers.
  - Ignores its ongoing text until the next Refresh.

Individual Resonance or Avatar cards can add more specific ways to move, swap, corrupt, or sacrifice Resonance cards, but these three patterns form the global baseline.

### 6.2 Costs and Drive Types

To prevent any single Drive type from becoming strictly superior (a noted concern in earlier evaluations), costs are spread deliberately:[file:14]

- Purge usually costs **opportunity** (forgoing some reward) instead of Drive.
- Quarantine typically costs **Body + Agility** (physical stabilization) or mixed resources.
- Some advanced effects may cost **Mind** (debugging the underlying logic).

Campaign progression can unlock stronger Resonance management tools, but costs should remain meaningful to preserve tension.

## 7. Resonance Cards: Behavior

### 7.1 Types

Resonance cards broadly fall into three types, though the implementation remains flexible:

- **Ongoing**  
  Provide continuous rules changes while face‑up in the tableau.

- **Instant**  
  Resolve immediately on reveal, then either enter the tableau (often face‑down) or are discarded.

- **Trigger**  
  Watch for specific tier outcomes or tag patterns and fire when conditions are met.

### 7.2 Example Behaviors

Examples (for design reference, not final text):

- “While this card is face‑up, all Technology Challenges add 1 extra Required Tag.”
- “On reveal: each Hero discards 1 card; then place this card face‑down in the tableau.”
- “Trigger: when the team achieves Strong Success on a Logic Challenge, flip this card face‑down.”

All effects are expressed in terms of **tags, tiers, and card states**, not raw numeric threshold modifiers.[file:14]

## 8. Example Boss and Resonance Cards

These examples are for flavor and patterns; exact numbers will be tuned later.

### 8.1 Example Boss: Quantum Boss Entity (Revised)

- **Tableau Profile**
  - `max_slots = 4`
  - **Boss Trigger**: Spawn this boss when there are **3 or more face‑up Threat cards** in the Resonance tableau at end of Resolution.

- **Early Spawn Bonus**
  - If the tableau had **fewer than 4 cards** when the boss spawned, all Heroes draw 1 card.

- **Late Spawn Penalty**
  - If the tableau was **full** when the boss spawned, all of the boss’s Low Fail and High Fail outcomes also force each Hero to discard 1 card.

This keeps the original “global corruptor” feel but ties it to visible Threat cards instead of hidden numeric thresholds.[file:14]

### 8.2 Example Resonance Cards

**Glitch Feedback Loop (Base, Ongoing)**  
- Enters face‑up.  
- Tags: Threat, Logic.  
- Effect: While this is face‑up, whenever the team gets **High Fail**, add 1 face‑down Resonance card to the rightmost empty slot.  
- Strong Success hook: If the resolved Challenge used Logic, you may discard this card instead of purging any other card.

**Echoing Screams (Horror, Instant → Face‑down)**  
- On reveal: Each Hero discards 1 card. Place this card face‑down in the leftmost empty slot.  
- While face‑down: counts as Horror for bosses that care about “any Horror card” but does not apply any effect.  
- When flipped face‑up: Each Hero loses 1 Drive of any type; then discard this card.

**System Overclock (Cyberpunk, Ongoing Boon/Threat)**  
- Enters face‑up.  
- While face‑up: All Heroes’ first card each Challenge costs **1 less Drive**.  
- Boss Interaction: This card always counts as **Threat** for boss triggers, even if flipped face‑down.  
- Purge Bonus: If this card is purged via Strong Success, the team may treat that Challenge as Strong Success for campaign reward purposes even if it was only Success.

These examples show how beneficial cards can still accelerate the boss, preserving interesting tradeoffs.

## 9. Tooling and JSON Notes

For structured representations (GameGrammar, simulators, etc.), each Resonance card should include at least:[file:14]

- `card_type`: resonance  
- `source`: base | theme | poi  
- `default_state`: face_up | face_down  
- `counts_for_trigger`: true | false  
- `tags`: [list of tags such as Horror, Technology, Threat, Boon]  
- `effects`: broken down by phase (resonance_phase, challenge_phase, resolution_phase, refresh_phase)

Each boss should define:

- `resonance_max_slots`  
- `resonance_trigger_condition`: structured description of when the boss spawns (using counts of tags, face‑up/face‑down state, and/or occupancy)  
- `early_spawn_effects` / `late_spawn_effects` keyed to tableau state

This keeps the Resonance system fully aligned with the existing tag + tier framework in `core_rules.md`, removes old numeric threshold scaling, and keeps all escalation logic in one visible, manipulable subsystem for both players and tools.[file:14]
