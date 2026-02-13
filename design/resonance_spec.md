# Harmonic Breach: Resonance System (Revised)

This document defines the updated Resonance mechanics for Harmonic Breach. It replaces older numeric “+1/+2/+3 to thresholds” escalation with a single, unified system based on a **Resonance Deck** and a visible **Resonance Tableau**. The tableau itself functions as the “Resonance track” and as the default early‑boss trigger.

## 1. Design Intent (Context for Future Work)

Resonance should:
- Feel like corrupted game logic accumulating in the Delve, not just a difficulty number.
- Be **visible** on the table so players can read how close they are to disaster.
- Interact with the existing **tag‑based, 4‑tier outcome system** instead of raw numeric thresholds.
- Give players **meaningful levers** to delay, accelerate, or shape escalation at a cost.
- Avoid death spirals where a few bad failures make the game mathematically unwinnable.

The system below is designed around those goals and around an earlier prototype where players could see a “big bad” moving through a deck and decide when to push or pull; here, that feeling is captured via the tableau instead of physically cycling a large stack.

By default, bosses are **session end‑gates**: thematically, they are anchors that must be confronted; mechanically, they mark the switch from "reaching the anchor" to "resolving the anchor," and their tiered outcomes primarily shape post‑session rewards and future Delve builds.

## 2. Core Concepts

- **Resonance Deck**: A small deck of scenario‑specific escalation cards.
- **Resonance Tableau**: A shared row of slots where Resonance cards are placed; its state (how many cards, which are face‑up, which tags are present) *is* the current Resonance.
- **Boss Card**: For each Delve, the boss defines how the Resonance Tableau behaves, when the boss appears, and how the final 4‑tier boss outcome affects rewards and future Delves.

There is no separate numeric Resonance marker. Players read stability directly from the tableau.

By default, each Delve has a **single‑spawn anchor boss** that appears at most once per session. When the boss appears, play shifts from resolving the Delve deck toward resolving the anchor; when the boss Challenge is resolved at any tier, its outcome effects are applied and the session ends.

## 3. Resonance Deck

### 3.1 Composition

The Resonance Deck is built per Delve from:

- **Base Resonance cards** (generic to all Delves).
- **Theme Resonance cards** (e.g., Horror, Cyberpunk, Platformer).
- Optional **POI Resonance cards** (location‑specific).

Typical size: **8–12 cards**, tuned per difficulty.

Each Resonance card includes:

- Tags (e.g., Horror, Technology, Threat, Boon).
- Whether it enters the tableau **face‑up** or **face‑down** by default.
- Whether it counts toward boss trigger conditions (Threat) or is primarily beneficial/neutral (Boon/Neutral).

### 3.2 When Resonance Cards Are Drawn

During each **Resonance Phase**, before revealing the next Challenge:

1. Draw the **top card** of the Resonance Deck.
2. Resolve any **on‑reveal** effects.
3. Unless the card says otherwise, place it into the **Resonance Tableau** following the normal placement rules (see below).

Some cards may skip the tableau and resolve purely as Instants, but in general, resonance‑related effects should flow through the tableau to keep escalation visible.

## 4. Resonance Tableau

The Resonance Tableau is a shared row of slots that shows the current corruption state.

### 4.1 Structure

The **Boss card** defines the tableau profile for that Delve:
- `max_slots` (e.g., 3–5).
- Which tags or card types matter for boss triggers (e.g., Threat, Horror, Technology).
- Any special rules for face‑down cards (e.g., “face‑down cards do not count for triggers”).

Example: A boss might specify `max_slots = 4` and “Boss spawns when 3 or more face‑up Threat cards are present in the tableau.”

Most Delves should use 3–4 slots as a baseline; 5‑slot tableaus are reserved for advanced scenarios or lower player counts to keep cognitive load manageable.

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

Design note: To avoid "locked" tableaus that feel inert, bosses or Resonance cards may define overflow or flip rules that occasionally turn face‑down cards face‑up or clear them, ensuring the tableau continues to evolve rather than stalling.

### 4.3 Card Entry

- By default, Resonance cards enter **face‑up** into the leftmost empty slot.
- Cards with “enter face‑down” explicitly override this.
- If all slots are full when a card would enter:
  - Apply any **on‑overflow** rule from the boss (e.g., immediate boss spawn; discard oldest card; flip one or more face‑down cards face‑up).

Overflow behavior is a primary tool for preventing tableau bloat or stale states; bosses are encouraged to define simple, visible overflow rules such as "spawn the boss immediately" or "flip the oldest face‑down card face‑up, then spawn the boss."

### 4.4 Reading Resonance

Players assess current Resonance by:

- How many **slots are occupied**.
- How many cards are **face‑up**.
- Which **tags** are showing on face‑up cards.

Different bosses care about different patterns, but the rules for reading the tableau are always the same.

This intentionally replaces the previous “Resonance levels modify thresholds” system; difficulty is expressed via visible cards and tags, not hidden math.

## 5. Boss Triggers and Effects

### 5.1 Default Boss Pattern: Single‑Spawn Anchor

By default, each Delve has a **single‑spawn anchor boss** that appears at most once.

- The boss is the moment the session shifts from "travel toward the anchor" to "deal with the anchor before it deals with us."
- When the boss spawns, it becomes the next Challenge.
- When that boss Challenge is resolved (at any tier), apply its boss‑specific outcome effects and end the session.

Normal Delve deck Challenges do not resume after the boss unless the boss card explicitly defines a multi‑phase or return pattern (advanced design space).

### 5.2 Boss Triggers

Each boss defines one or more conditions that cause it to appear as the next Challenge. Examples:

- **Full Tableau Trigger**  
  “When all slots are occupied, spawn the boss.”

- **Tag Threshold Trigger**  
  “When there are 3 or more Threat‑tagged cards face‑up, spawn the boss.”

- **Hybrid Trigger**  
  “When there are at least 2 Horror cards and the tableau is at least half full, spawn the boss.”

Triggers are checked at the **end of the Resolution Phase**, after tier outcomes and any flips/purges for that round.

### 5.3 Early and Late Boss States

On spawn, the boss reads the current tableau and locks in an **Early** or **Late** state (and optionally a specific mode such as "Threat‑heavy" or "Horror‑loaded").

- Spawning the boss **early** (few cards / low Threat density) should provide a small tactical advantage (e.g., fewer stacked Resonance effects, weaker boss state, mild on‑spawn benefit for heroes).
- Spawning the boss **late** (full tableau, many Threat tags) can grant the boss additional powers or harsher failure tiers (e.g., extra discards on Low/High Fail, extra Resonance added, more severe campaign fallout).

These modifications are written directly on the boss card (e.g., “If the tableau was full when I spawned, all my failures increase Resonance or discard extra cards”), keyed to tableau state at the moment of spawn (for example, "If the tableau was full when I spawned, all my Low Fail and High Fail outcomes also force each Hero to discard 1 card.").

### 5.4 Boss Tier Outcomes as Session End‑Gates

Boss Challenges use the same 4‑tier outcome system as other Challenges, but their outcomes primarily shape **post‑session reward exchange** and future Delve builds rather than short‑term tempo.

For clarity, we can distinguish:

- **Silencing outcomes**: Strong Success, Success.
- **Breach outcomes**: Low Fail, High Fail.

A recommended default pattern:

- **Strong Success (Silence: Optimal)**  
  - The Delve is fully "won."  
  - Grants the best exchange rate for post‑session rewards (e.g., converting Delve gains into notes or other currency).  
  - Additionally allows the team to **cash out the Resonance Tableau**: remaining Resonance (or a function of occupancy/tags) may be converted into extra notes or special rewards.

- **Success (Silence: Costly but Clean)**  
  - The Delve is "won."  
  - Improves the post‑session exchange rate compared to baseline, but the tableau cannot be monetized; remaining Resonance dissipates or leaves a minor mark.

- **Low Fail (Breach: Local Fallout)**  
  - The heroes survive and the session ends, but the anchor's influence bleeds forward.  
  - Exchange rate is baseline or slightly worsened.  
  - The next Delve's build is penalized in a specific way (for example, seeding a particular Resonance card into the next Delve's deck, or imposing a small build constraint like an extra Threat card).

- **High Fail (Breach: Lasting Scar)**  
  - The Delve is lost.  
  - No beneficial exchange; players may lose some accumulated rewards or potential notes.  
  - All **future** Delve builds in this campaign path are affected, usually by adding persistent corruption (e.g., an extra Threat Resonance card to all future decks, global negative tags, or a permanent condition bosses can exploit).

### 5.5 Silence and Breach Tokens (Campaign Hook)

Boss outcomes may also create **Silence** and **Breach** tokens that live in the campaign‑level **HQ deckbox** (defined in the campaign/progression rules):

- **Silence tokens**  
  - Generated by silencing outcomes (Strong Success, Success).  
  - During post‑session, a Silence token is added for free to the HQ deckbox.  
  - HQ can later spend or reference these tokens to unlock upgrades, mitigate future Resonance, or buy reward‑pool cards (details in campaign rules).

- **Breach tokens**  
  - Generated by breach outcomes (Low Fail, High Fail).  
  - During post‑session rewards, a Breach token is among the items drawn from the reward pool.  
  - Players may spend notes to avoid adding that Breach to HQ; if they do not, it is added to the HQ deckbox and becomes a lasting campaign scar that can affect future Delves.

Resonance itself does not track these tokens; they are a consequence layer attached to boss tier outcomes and handled by the HQ/campaign system.

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

To prevent any single Drive type from becoming strictly superior (a noted concern in earlier evaluations), costs are spread deliberately:
- Purge usually costs **opportunity** (forgoing some reward) instead of Drive.
- Quarantine typically costs **Body + Agility** (physical stabilization) or mixed resources.
- Some advanced effects may cost **Mind** (debugging the underlying logic).

During boss fights, these same tools remain available, but the stakes are higher: choosing to spend resources managing Resonance competes directly with spending them to defeat the boss itself. Campaign progression can unlock stronger Resonance management tools, but costs should remain meaningful to preserve tension.

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

All effects are expressed in terms of **tags, tiers, and card states**, not raw numeric threshold modifiers. To reduce cognitive load, each Resonance card should focus on a single clear ongoing effect plus at most one hook (such as a Strong Success or High Fail interaction).

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

This keeps the “global corruptor” feel but ties it to visible Threat cards instead of hidden numeric thresholds; the boss's tier table would then follow the Strong Success / Success / Low Fail / High Fail pattern for end‑of‑session consequences, Silence/Breach token generation, and exchange rates described above.

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

These examples show how beneficial cards can still accelerate the boss, preserving interesting tradeoffs between short‑term advantages and long‑term risk.

## 9. Tooling and JSON Notes

For structured representations (GameGrammar, simulators, etc.), each Resonance card should include at least:
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
- A 4‑tier outcome table whose entries may reference:  
  - Post‑session exchange rates.  
  - Optional conversion of the Resonance Tableau into rewards on Strong Success.  
  - Campaign‑level effects on the next Delve build or all future Delves.  
  - Creation of Silence/Breach tokens and any immediate consequences tied to them.

This keeps the Resonance system fully aligned with the existing tag + tier framework in `core_rules.md`, removes old numeric threshold scaling, and keeps all escalation logic in one visible, manipulable subsystem for both players and tools.