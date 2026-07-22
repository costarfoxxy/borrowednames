# The Weight of Borrowed Names — Technical Design Document

*Living reference for Castlemarne. Current as of ch1 (patched), ch2, ch3 (unversioned filenames, GitHub is source of truth). Last updated: added full narrative arc §1B (all beats, chapter count, structure); resolved §9.4 (Vothren offstage, Farren introduced); confirmed Pell as minimal NPC with schema entry; seeded playerName for Ch5+; patched Ch1 §14 inconsistencies (flags location, localStorage key, chapter field); updated §15 with confirmed Ch4 structure.*

This document exists so that a chapter built in a fresh context — whether by Rowan by hand, or generated dynamically later — stays mechanically and canonically consistent with everything before it. Read this before writing scene code. When in doubt, this document is the source of truth over any individual chapter file, since chapter files are where drift actually happens.

---

## 1. Core Design Intent

The reading sense is not a puzzle mechanic. It is the game's central metaphor: **the protagonist is a person who reads what things carry, wearing the name of someone whose own things she is reading.** Every mechanic below should serve that idea — the tension between accumulating true knowledge and losing your own shape while you do it.

Two axes are in constant tension throughout the game:
- **Cover Integrity** — can you keep performing Tessaly convincingly?
- **Rootedness** — how much of *you* is dissolving into *her*?

These are designed to sometimes trade off against each other (a choice that protects your cover often costs you rootedness, and vice versa) but not always — that inconsistency is intentional. Real disguise isn't a clean tradeoff.

---

## 1A. Narrative Arc — Chapter by Chapter

*This section exists because the mechanics document what each chapter does, but not what it's* for. *A fresh session reading only scene code has to reverse-engineer the emotional throughline from prose. This is that throughline, stated directly.*

**Prologue — the coercion.** The player signs a name that isn't theirs under duress dressed as opportunity. The solicitor's line — *an offer you cannot safely refuse* — is the whole premise in one sentence. This is where `senseType` and `sealOrigin` get chosen, and where the reading sense first gets framed as something that has, until now, been professionally useful and personally isolating.

**Chapter One — the house becomes real.** Tessaly stops being a name on paper and becomes a felt person: her morning room, her drawers, her handwriting. The critical beat is the discovery that the reading sense — which has only ever been *tolerated* elsewhere — is *welcomed* here. The house reaches for the player. This is the first taste of the real seduction the game is built on: not "you might get caught," but "you might not want to leave."

**Chapter Two — the stakes become real.** What looked like paperwork develops teeth. Idris's intercepted letter and Voss's letter in the study both point at the same thing from different angles: someone else already knows this arrangement is dangerous, and said so in writing, before the player arrived. Maren's audit is the chapter's structural core — the first real test of whether the performance holds under someone else's trained attention, and (as of the revision pass) the first place accumulated stats get a mechanical payoff via skill checks rather than just narrative acknowledgment.

**Chapter Three — the threat becomes real.** Vothren gets a name and a shape: not a vague menace but a specific, historied danger — a collector of people with the reading sense, owed a debt Idris's family already tried to pay with Tessaly. Alliances resolve here: Maren picks a side, Idris admits what he's known. The dream sequence is the chapter's emotional center — it's where accumulated Rootedness and Reading Exposure stop being background numbers and start dictating what the player's own subconscious hands them.

**Chapter Four (in progress) — the climax.** Pell arrives to complete the transfer. This is where every accumulated thread has to actually matter: Cover Integrity should gate what's possible, Reading Exposure should change Vothren's leverage even offstage, Rootedness should color what "winning" even means by the chapter's end, and `letter_opened` — read all the way back in Chapter Two — should pay off a third time. The chapter's central question isn't "does the player get caught," it's **"does the player still want to leave, and if not, is that a loss."**

---

## 1B. Full Narrative Arc — All Beats

*This section was written before Ch4 scene code began, to establish the shape of the whole story. It should be updated as chapters diverge from the plan, but divergence should be a decision, not a drift. Beat count and chapter count are confirmed here; use this as the structural north star.*

**The central dramatic question:** Can a borrowed name become your own — and what does it cost if it does?

**Secondary engines:**
- *Mystery engine:* What happened to the real Tessaly?
- *Threat engine:* What does Vothren actually want?
- *Want engine:* What did the protagonist come here wanting — and is that still true?
- *Place engine:* What does the morning room remember, and what does it hold by the end?

### The Ten Beats

**Beat One — Threshold** *(Prologue — done)*
Coercion dressed as opportunity. The protagonist signs *Tessaly Aldane* under duress. `senseType`, `sealOrigin`, and `playerWant` are chosen here. The reading sense is framed as professionally useful and personally isolating — something tolerated, not welcomed.

**Beat Two — First Night** *(Ch1 — done)*
The house before anyone wakes. Geography of the lie. Maren guarded, Idris lost, Efa kind. The reading sense almost catches what the morning room remembers. First test: can the name be held overnight?

**Beat Three — The Name Under Pressure** *(Ch2 — done)*
The household begins testing. Maren's audit is the first real fire. Idris's letter is the first mystery. Voss's letter in the study is the first real temptation — a permanent choice about what the player is willing to know.

**Beat Four — The House Responds** *(Ch3 — done)*
Pell's shadow falls through correspondence. Idris decides. Maren picks a side. The dream sequence surfaces accumulated Rootedness and Reading Exposure. The house has started to know the player.

**Beat Five — The Outside Arrives** *(Ch4 — next)*
Aldous Farren arrives in Vothren's place with regrets his employer is unable to attend in person. Pell is present as uneasy co-conspirator — he installed the fake; Farren doesn't know. Farren makes one observation about Tessaly before leaving: *"She has her father's patience."* This sentence is a trap — patience as compliment or warning depends on what the household knows about Voss, and the player doesn't know any of it. Different NPCs react visibly and differently. The deception holds its first external test; a thread comes loose. The player begins to understand what Vothren is actually after.

**Beat Six — What Tessaly Was**
Something arrives — document, object, or person the reading sense can access — that tells the player who the real Tessaly was. Not Pell's version. The actual one. Did she want to disappear? Is she dead? Did she run from this house, or from something Vothren did? This beat ends with a crack: the player has been filling an absence. Now they know the shape of the person they've been filling it with. *Are they replacing her, or becoming something new in the space she left?*

**Beat Seven — The Name Slips**
The player's real self surfaces in a way someone can see. High Rootedness makes it likely — they've grown comfortable. Low Cover Integrity makes it likely — the cracks show. One thing lands in the wrong pair of eyes and doesn't quite make sense. The witness becomes either the most valuable ally or the most dangerous liability, depending on accumulated trust. This beat introduces genuine leverage. See §8 for the `playerName` seed — Ch4 plants the near-slip internally; Ch5 is where someone might actually catch it.

**Beat Eight — The Reckoning Assembles**
Vothren's actual arrival is announced — he's coming himself. Whatever the estate debt is really about becomes clear. The household has to decide what outcome they want; their decisions hinge on what they believe about "Tessaly" and what they know about the real one. The player has to decide which version of themselves walks into the final confrontation.

**Beat Nine — The Confrontation**
Vothren. Pell. Whatever it costs. The reading sense at its highest-stakes use — the player reads something or someone that changes the scene's terms in real time. Every alliance is called in or failed. The player decides, under pressure, whether the borrowed name is the right weapon for what's happening — or whether something else is.

**Beat Ten — What the House Remembers**
Falling action. The morning room again. What it holds now. Each NPC's resolution proportional to their ledger and trust score. The player either carries Tessaly's name forward, releases it, or holds something that is neither — a third thing that grew in the space between. The ledger closes.

### Chapter Count

**Seven chapters plus prologue, with a possible brief epilogue for Beat Ten.**

- Prologue, Ch1–Ch3: done (Beats 1–4)
- Ch4: Beat Five (Farren)
- Ch5: Beat Six + early Beat Seven (the slip planted, Tessaly's truth emerging)
- Ch6: Beats Seven–Eight (the name slips properly; the reckoning assembles)
- Ch7: Beats Nine–Ten (the confrontation; the morning room)

Beat Ten may be short enough to live at the end of Ch7 rather than as a standalone chapter. If Beats Six and Seven require more room than estimated — the leverage dynamic in Beat Seven has real branching depth — the count may reach eight. Discover in the build; don't predict it now.

---

## 2. Player State Schema

This is the canonical shape of `gs` (game state). Every chapter must read and write this shape exactly. Field names are case-sensitive and must match across all chapters — this is the single most common source of save-string breakage.

```js
gs = {
  playerName: string,        // captured at Prologue creation; NOT currently used in any narrative text — see §8
  sealOrigin: 'found' | 'given' | 'acquired' | 'unknown' | null,
  senseType: 'hot' | 'cold' | null,
  playerWant: 'survive' | 'understand' | 'unnamed' | null,

  stats: {
    coverIntegrity: 0–100,   // starts 60
    rootedness: 0–100,       // starts 20
    readingExposure: 0–100   // starts 0
  },

  npcs: {
    pell:   { suspicion: 0–100, trust: 0–100 },  // starts 20/40; his suspicion register differs — for him it means "is she worth what this cost me?" not "does she belong here?"
    maren:  { suspicion: 0–100, trust: 0–100 },  // starts 60/10
    efa:    { suspicion: 0–100, trust: 0–100 },  // starts 20/30
    idris:  { suspicion: 0–100, trust: 0–100 },  // starts 40/20
    farren: { suspicion: 0–100, trust: 0–100 }   // introduced Ch4; starts 30/0 — arrives neutral-watchful, no prior relationship
  },

  ledger: [ { question, response, sentiment, effects } ],
  choiceHistory: [ { scene, choiceText, effects } ],
  flags: {},                 // chapter-specific booleans/counters — see §7
  currentScene: string | null,
  pendingLedger: object | null
}
```

**Rule:** All stat/trust/suspicion values are clamped 0–100 via `clamp()`. Never write to these fields directly — always route through `applyEffects()`, which owns the clamp and the key-mapping. A chapter that mutates `gs.stats.coverIntegrity` by hand instead of via an effects object will desync from the ledger and stats-overlay display.

### What each stat represents, for writers

| Stat | Represents | Rises when | Falls when |
|---|---|---|---|
| Cover Integrity | How convincing the performance is | Confident, controlled, "correct" answers; successful skill checks | Hesitation, being caught in a slip, emotional leakage |
| Rootedness | How much of the player is becoming Tessaly | Choosing sentiment, permanent reading choices, moments of feeling *at home* | Rarely decreases — currently almost a one-way ratchet; see §9 open question |
| Reading Exposure | How visibly strange the player seems to non-readers | Opening the reading sense, especially involuntarily or in front of witnesses | Almost never decreases (one exception: a `hate`-sentiment ledger choice in Ch2) |

Suspicion and trust are **tracked independently per NPC and are not inverses of each other** — this is stated explicitly in-game (the stats-overlay note) and should stay true. Low suspicion does not imply high trust; an NPC can trust you and still be watchful.

---

## 3. The Ledger System

**Purpose:** a periodic gut-check moment, distinct from ordinary choices, where the player states how they feel about what just happened rather than what they do next.

**Structure of a ledger moment:**
```js
ledger: {
  question: string,
  options: [string, string, string, string],       // exactly 4, always
  sentiments: ['hate','endure','survive','love'],   // this order, always
  effects: [ {effectsObj}, {effectsObj}, {effectsObj}, {effectsObj} ],
  next: sceneId,
  isDream: boolean  // optional, Ch3+ only — see §6
}
```

**Fixed convention — do not vary this:** the four options always map to the same emotional register in the same order:
1. **hate** — rejection / this costs me something I resent
2. **endure** — grudging tolerance / management
3. **survive** — practical acceptance / this is useful
4. **love** — embrace / this is becoming part of me

This ordering is load-bearing for the UI (color-coding, hover states) and for the player's ability to learn the game's emotional grammar over time. A future chapter that reorders these, or uses a 3- or 5-option ledger, will break both the CSS class mapping (`opt-hate`, `opt-endure`, `opt-survive`, `opt-love`) and the read of the pattern.

Ledger entries are permanently recorded in `gs.ledger` and displayed in the Ledger overlay for the rest of the game (including into future chapters, via save string). **Ledger entries are never deletable by the player and never overwritten.** This is the emotional through-line of the whole story — treat it as append-only, always.

---

## 4. Permanent Choices (✦)

A choice marked `permanent: true` renders with an amber ✦ marker and a tooltip ("This choice cannot be undone"). This is a **narrative promise**, not just a UI flag — permanence should track something that changes who the player's character *is*, not just what they know.

Current pattern across chapters: permanent choices are almost always the reading-sense choice — the moment the player opts to open to an object knowing it will leave a mark (`readingExposure` increase) or admit a truth aloud that can't be unsaid (e.g., telling Idris "No, I'm not [her]").

**Guidance for new chapters:** reserve `permanent: true` for choices that meet at least one of:
- Opens the reading sense to something with irreversible consequence (exposure, an NPC witnessing it)
- States a truth aloud to another character that can't be walked back
- Forecloses a relationship path (e.g., burning a bridge, or the reverse — a bridge that can never be un-built)

Do not mark a choice permanent just because it's dramatic. Overuse dilutes the ✦ marker's meaning.

---

## 5. Skill Checks — revived in the Ch2/Ch3 pass

Chapter One introduced a genuine mechanic:

```js
skillCheck: { stat: 'coverIntegrity', against: 'marenSuspicion', threshold: 15, pass: sceneId, cost: sceneId, fail: sceneId }

function performSkillCheck(check) {
  diff = gs.stats[check.stat] - getNPCStat(check.against);
  if (diff >= threshold)   -> pass  ("Cover holds.")
  if (diff >= -threshold)  -> cost  ("Something noticed.")
  else                     -> fail  ("The mask slips.")
}
```

This produced real stakes: the player's accumulated stats *silently* determined which of three branches they got, dressed up as a flash `skillResult` banner. **As of the Ch2/Ch3 revision pass, this system is live again** — Chapter Two's counter-scheduling moment with Maren now runs through it (see `pre_maren_push` and its `_cost`/`_fail` variants). Chapter Three doesn't yet have one of its own; that's a reasonable thing to add if a jeopardy moment surfaces there, but nothing structural is missing.

**Recommendation for Chapter Four and beyond:** any scene with real jeopardy (an audit, an interrogation, a moment where the player might be caught) should route through `performSkillCheck()` rather than a flat three-way choice. This keeps accumulated stats *meaningful* — a player who has spent three chapters carefully building Cover Integrity should get a mechanical payoff for it, not just flavor-text acknowledgment.

If skill checks return, keep the three-tier pass/cost/fail structure — it's already proven and the UI (`.skill-result.pass/.cost/.fail`) already exists in Ch1's stylesheet and should be copied forward, not reinvented.

---

## 5A. Hot/Cold Reading Sense — The Involuntary Open

*Added after the Ch2/Ch3 revision pass. Resolves §9.3 below.*

`senseType` was, until now, a one-time flavor pick — it swapped text in Ch1's desk scene and did nothing mechanically after. This section makes it a running playstyle distinction with real, repeatable stakes, not a single showcase moment.

**The core rule:** a `hot` reader does not get the option to decline an involuntary reading opportunity that a `cold` reader would be offered as a choice. The sense opens on its own. This should read as a genuine loss of agency in the moment — the UI shows no "touch it or don't" choice at all for hot readers at these junctures; the open simply happens, narrated as something that occurs to the player rather than something they do.

**The two-part beat.** An involuntary hot open is never just a flat penalty. It is always followed by a second, real choice about what the player does with what just happened:

1. **The open (automatic, no choice rendered):** Apply a base Reading Exposure cost via `scene.autoEffects` on scene entry (see pattern below). This is non-negotiable for hot readers — it is the cost of the sense type, not a consequence of a decision.
2. **The response (a real three-way choice, always rendered, regardless of sense type when applicable):**
   - **Manage** — cover the tell, breathe through it, give nothing away. Partial exposure refund (roughly half the base cost), small Cover Integrity gain. This is the repeatable lever that answers §9.1: exposure *can* be clawed back, deliberately and at a cost of its own (it costs the player something to suppress what they felt — no accompanying Rootedness gain).
   - **Integrate** — let it land; don't fight what was just learned. Exposure stays at full cost. Rootedness rises. The player is not hiding what they are from themselves, even while hiding it from whoever's watching.
   - **Use** — spend the information immediately and visibly in the scene, in a way that reads to a present witness as insight rather than strangeness. Exposure stays at full cost. Trust rises with whichever NPC is present to see it. **This option is only available in scenes where an NPC is actually present to notice** — an involuntary open while the player is alone (e.g., waking, an empty room) only offers Manage or Integrate.

**Implementation pattern:**
```js
sceneId: {
  autoEffects: { readingExposure: 8 },   // applied once on scene entry, before choices render
  narrative: `...the open happens, unchosen...`,
  choices: [
    { text: '...', effects: { readingExposure: -4, coverIntegrity: 3 }, next: 'sceneId_manage' },
    { text: '...', effects: { rootedness: 5 }, next: 'sceneId_integrate' },
    { text: '...', effects: { <npc>Trust: 6 }, next: 'sceneId_use' }  // omit if no witness present
  ]
}
```
`autoEffects` should only fire once per scene — guard with `gs.flags['autofx_' + sceneId]` so replays and resumes don't double-apply it.

**Cold readers** keep the existing pattern: an explicit choice to open the sense or not, marked `permanent: true` when they choose to. No `autoEffects`, no forced beat.

**Where this is implemented so far:**
- Chapter Three, `morning_three` (Pell's note arrives, Maren present as witness) — hot readers now get the forced open + three-way response; cold readers retain the original choice-based version unchanged.
- **Reserved as the flagship instance:** Chapter Four, the moment Pell crosses the threshold. This is the highest-stakes possible use of the beat and should not be spent early. A hot reader reads him before he's spoken; a cold reader can choose to hold off and read him seated, deliberately, at the cost of whatever the door itself might have told them in that first second.

**Guidance for future chapters:** don't scatter this into every reading opportunity — it dilutes into background noise the same way overusing the ✦ permanent marker would. One or two well-chosen involuntary opens per chapter, at moments with real narrative weight, is the right density.

---

## 6. Dream Sequences (Chapter Three onward)

Introduced in Ch3 as a distinct register: different CSS class (`.dreaming`, `.dream-passage`, `.dream-choice`), slower fade animation (`dreamFade` vs `fadeUp`), branch selection based on accumulated stats rather than player choice:

```js
function dreamBranch() {
  if (gs.stats.rootedness >= 45) return 'dream_high_root';
  if (gs.stats.readingExposure >= 25) return 'dream_high_expose';
  return 'dream_default';
}
```

This is a good pattern — it makes the *accumulation* of earlier choices visible in a way ordinary branching doesn't, and it's worth reusing for other "the house/story reflects your state back at you" moments. Two notes for future use:

- **Threshold check order matters.** Currently rootedness is checked before exposure, so a player high in both only ever sees the rootedness dream. If a chapter wants both to matter, add an explicit combined branch (e.g., `dream_high_both`) rather than relying on check order to surface it.
- Dream ledger moments use the `isDream: true` flag to trigger the purple-tinted overlay styling. If a future chapter adds dream sequences, this flag must be set on both the scene *and* the ledger object nested inside it — they're checked separately in different functions.

---

## 7. Flags

`gs.flags` is the correct place for anything that is: chapter-specific, not a stat, and needs to persist or gate content. Established uses so far:

- `ch1LedgerCount` / `ch3LedgerCount` (note: inconsistently *not* nested under `.flags` in Ch1 — see Known Inconsistencies below) — records how many ledger entries existed *before* this chapter started, so `replayChapter()` can preserve prior-chapter ledger entries while wiping this chapter's.
- `letter_opened` (Ch2) — set when Voss's letter is read. **Currently write-only: no later chapter checks it.** Chapter Four should check this and branch — a player who read the letter in Ch2 has different knowledge than one who deferred it, and Ch3 currently treats both identically.
- `chapter_complete` / `ch3_complete` — set on chapter-end, currently unread. Intended, presumably, as a future guard (e.g., Chapter Four's loader could refuse to accept a save where `ch3_complete` isn't true, or could brief the player differently).

**Rule going forward:** every flag that gets *set* needs a documented consumer, even if that consumer doesn't exist yet. Add it to the table below when you add the flag.

| Flag | Set in | Should be read in | Currently read in |
|---|---|---|---|
| `ch1LedgerCount` | Ch1 (`.flags` — patched) | Ch1 replay | Ch1 replay ✓ |
| `ch1LedgerCount` | Ch2 (`.flags`) | Ch2 replay | Ch2 replay ✓ |
| `ch3LedgerCount` | Ch3 (`.flags`) | Ch3 replay | Ch3 replay ✓ |
| `letter_opened` | Ch2 | Ch3+ narrative branching, Ch4 §15 payoff | Ch3 `morning_three` ✓; Ch4 pending |
| `maren_saw_reading` | Ch2 | Ch4 alliance branching | Ch4 pending |
| `chapter_complete` | Ch2 | Ch3 loader | *nowhere* — low priority |
| `ch3_complete` | Ch3 | Ch4 loader | Ch4 pending |
| `ch4_complete` | Ch4 (TBD) | Ch5 loader | *not yet set* |

---

## 8. Player Name

`playerName` is captured at character creation and stored faithfully through every save string, but **no scene in any chapter interpolates it into narrative text yet.** Every "you say your own name" beat stays deliberately abstract ("You say your own name once, into the quiet room"). This is intentional restraint, not an oversight.

**Confirmed plan (decided before Ch4):**

- **Ch4 plants the seed internally.** At Farren's observation — *"She has her father's patience"* — the player's real self almost surfaces in a way that a present NPC could catch. The text registers the near-slip for the player only; no one in the scene notices. High Rootedness makes this beat more present in the prose; low Cover Integrity makes it feel more dangerous. `playerName` is not interpolated here, but the *shape* of the moment is designed to hold it later.
- **Ch5 is where someone catches it.** Beat Seven (The Name Slips) is the scheduled first interpolation of `playerName` into narrative text — a moment where an NPC hears or reads something that doesn't fit Tessaly, and what they do with it depends on accumulated trust. This is a high-stakes, one-time event; the NPC who witnesses it becomes either the player's most valuable ally or a significant liability.
- **Do not surface `playerName` before Ch5.** The restraint is load-bearing: the name's appearance needs to feel like a breach, not a texture. Using it earlier as flavor dilutes the moment when it actually matters.

---

## 9. Open Design Questions for Rowan

These aren't bugs — they're judgment calls that should be made once and then documented here, so future chapters don't each guess differently:

1. **Should Rootedness or Reading Exposure ever meaningfully decrease?** *Resolved — see §5A.* Manage responses to involuntary hot opens give a real, repeatable exposure refund. Rootedness still has no equivalent lever and remains intentionally closer to one-directional — that asymmetry is a deliberate reading of the theme (you can claw back your composure; you can't as easily claw back how much you've come to feel at home), not an oversight, but worth Rowan confirming.
2. **What do high vs. low Cover Integrity actually gate, going forward?** So far it mostly flavors text and feeds skill checks (revived in the Ch2 revision pass — see §14). Chapter Four is a good place to make it *load-bearing* — e.g., low cover integrity locking the player out of a "clean" path with Pell.
3. **Does `senseType` (hot/cold) deserve a second differentiated moment, or was Ch1's desk scene meant to be the one and only showcase?** *Resolved — see §5A.* It's now a running mechanic (the involuntary open + three-way response), not a one-time flavor pick, with Chapter Four's Pell threshold reserved as the flagship instance.
4. **Is Vothren meant to appear on-page, or stay an offstage pressure?** *Resolved before Ch4.* Vothren stays offstage through at least Ch6. His absence does more work than his presence would at this stage — each chapter his name appears without him should make the eventual arrival (Beat Nine, Ch7) heavier. Ch4 introduces **Aldous Farren**, Vothren's business associate, who arrives with regrets his employer is unable to attend in person. Farren is deliberately unmenacing — polite, calibrated, giving nothing away. He makes one observation about Tessaly (*"She has her father's patience"*) and leaves. The near-miss is the point: the household expected resolution and got deferral instead, which gives everyone — Maren, Idris, Pell, the player — more room to maneuver and more reason to pressure each other. Farren has an NPC schema entry (see §2); his trust/suspicion matter for whether he carries a favorable report back to Vothren.

---

## 10. Scene Object Schema (canonical)

```js
sceneId: {
  label: string,           // chapter label shown in header, e.g. 'Chapter Three'
  title: string,           // scene title shown in header
  narrative: string,       // HTML string; may use <em>, <strong>, .reading-passage, .dream-passage, .formal-note, .creditor-letter
  dynamicNarrative: { hot: string, cold: string },  // optional — overrides `narrative` based on gs.senseType
  isDream: boolean,        // optional — applies dream styling
  isSkillCheck: boolean,   // optional — routes choices through performSkillCheck (Ch1 pattern; revive per §5)
  skillCheck: { stat, against, threshold, pass, cost, fail },  // required if isSkillCheck
  hasLedger: boolean,      // optional — if true, `ledger` is required and choices should be []
  ledger: { ... },         // see §3
  choices: [
    {
      text: string,
      hint: string | null,
      permanent: boolean,       // see §4
      effects: { statKey: number, ... },  // keys must match applyEffects()'s statMap
      skillCheckChoice: boolean,          // optional, Ch1-only pattern — marks a choice as routing to a skill check rather than a direct scene
      next: sceneId | '__end' | function   // function form only used for dream branching (see §6)
    }
  ]
}
```

**Effect keys, exhaustive list (must match exactly):**
`coverIntegrity, rootedness, readingExposure, pellSuspicion, pellTrust, marenSuspicion, marenTrust, efaSuspicion, efaTrust, idrisSuspicion, idrisTrust, farrenSuspicion, farrenTrust`

Any new NPC introduced in a later chapter needs: (1) an entry in `gs.npcs`, (2) two new keys added to `statMap` in `applyEffects()`, (3) two new keys added to the `labels` object in `effectsToString()`, (4) an `npcRow()` call added to `buildStatsHTML()`. Missing any one of these four means the new NPC's trust/suspicion silently fails to display or persist. This is the most error-prone part of extending the cast — a checklist item, not just a note.

---

## 11. What Every Chapter File Must Do (the chapter contract)

For a new chapter — hand-written or dynamically generated — to slot in cleanly:

**On load:**
1. Check for an in-progress autosave for *this* chapter first (`wbn_chN_save` pattern). If found and valid (has `currentScene`), offer Continue.
2. Otherwise, accept a pasted save string from the *previous* chapter. Validate it's actually parseable JSON after base64 decode, and — this is currently missing everywhere — check that the decoded object's `chapter` field is the expected predecessor, not just that `playerName` exists. A save from the wrong chapter should produce a clear error, not a silently malformed game state.
3. Provide a "begin without save" fallback that seeds sensible defaults, since not every playtester will have a prior save.

**During play:**
4. Autosave to localStorage after every scene transition and every ledger resolution, under a consistently-named key (`wbn_chN_save`).
5. Route all stat/trust/suspicion changes through `applyEffects()`. Never hand-edit `gs` fields directly outside of load/replay logic.
6. Any scene with real narrative jeopardy should consider a skill check (§5) over a flat branch, if the mechanic is revived.

**On chapter end:**
7. Set a `chapter_complete`-style flag in `gs.flags`.
8. Serialize the *full* schema from §2 into the save string — not a subset. Ch1's original save string predates the `flags` object; any chapter reading an old save must tolerate a missing `flags` key (default to `{}`), not throw.
9. Version the save string's `v` field meaningfully — bump it when the schema shape changes, not just per-chapter. Right now `v` roughly tracks chapter number, which conflates "which chapter produced this" with "what shape is this data," and those are different questions a loader needs to ask.

**Naming, so save strings and localStorage keys stop drifting:**
- localStorage key: `wbn_ch{N}_save` (Ch1 currently breaks this pattern with `wbn_save_ch1` — worth normalizing next time that file is touched)
- Save-string `chapter` field: `'prologue' | 'chapter_one' | 'chapter_two' | 'chapter_three' | 'chapter_four'` (Ch1 currently just uses `'one'` — normalize)

---

## 12. Guidance Specifically for Dynamic Generation

If later chapters (or chapter branches) are going to be generated rather than hand-authored, the generator's system prompt should be constrained by, at minimum:

- **The full schema in §2 and §10**, non-negotiably — a generated scene that doesn't match the scene object shape will silently fail to render rather than erroring loudly, since `goToScene()` just returns early if `!scene`.
- **The effect-key whitelist in §10** — a generated scene that invents a new effect key (e.g., `idrisAffection` instead of `idrisTrust`) will pass through `applyEffects()` silently doing nothing, with no error. This is the most dangerous failure mode for generated content because it's invisible in testing.
- **The four-option, fixed-order ledger convention (§3)** — a generator given loose instructions will happily produce 3 or 5 options, or reorder the sentiment axis, unless explicitly locked.
- **Current NPC state at generation time** — a generator needs the live `gs.npcs` values as context, not just the immediately preceding scene, or it will write dialogue that contradicts trust/suspicion levels the player has actually earned (e.g., writing Maren as newly skeptical after the player has spent two chapters earning her trust).
- **The ledger as append-only, read-only history** — a generator should receive the full existing `gs.ledger` as context (it's the emotional record of who this player's version of the character has become) but must never be permitted to rewrite or reinterpret past entries.
- **Flags with documented consumers (§7)** — if the generator sets a flag, the same generation pass (or a clearly scheduled next one) needs to consume it. Otherwise flags accumulate the way `letter_opened` and `chapter_complete` already have.

A reasonable implementation: before generating a new chapter or branch, assemble a compact "state packet" — current stats, current NPC trust/suspicion, the full ledger, active flags, and the player's `sealOrigin`/`senseType`/`playerWant` — and feed that as grounding context alongside this document. That's a smaller, cleaner input than replaying entire chapter HTML files, and it's the actual information a human co-writer would want before picking up the thread.

---

## 13. Project Files and File Versioning

**Confirmed behavior (July 2026):** uploading a file to Claude Project Files with the same name as an existing file does **not** overwrite it and does **not** auto-rename it. The two files exist side by side, identical in name, distinguishable only by opening them and comparing content. This is a real risk for a project like this one, where a chat session frequently produces a corrected version of a file that already exists in the project — Chapter One has already gone through one such fix.

**This is a manual-process problem, not a tooling problem** — Claude cannot write back into Project Files directly; any edit produced in a chat is a new download that a person must choose to upload, and the project's file list is a snapshot of whatever was uploaded, not a live sync of anything Claude touches. That division of labor isn't going to change, so the fix has to be procedural.

**Working convention going forward:**
1. **Delete the stale file from Project Files before uploading its replacement**, when the interface allows it. This is the cleanest option — one filename, one file, no ambiguity.
2. **When deletion isn't convenient in the moment, version the filename explicitly** rather than relying on remembering which upload came last: `borrowed-names-ch1.html` → `borrowed-names-ch1-v2.html` → `borrowed-names-ch3-v2.html`, etc. An unversioned filename should be treated as presumptively stale once a `-v2` (or higher) of the same base name exists.
3. **This design doc should note, at the top, which version of each chapter file it was last cross-checked against** — e.g., "current as of ch1-v2, ch2-v1, ch3-v1" — so a future session (or a generator ingesting this doc) doesn't have to guess which file in a possibly-duplicated project folder is authoritative.

**Design suggestion (Sonnet's, not settled — Rowan should weigh in):** consider baking a version marker directly into each chapter file's save-string `chapter` field or a new top-level `schemaVersion`/`fileVersion` constant near the top of the `<script>` block — something like `const FILE_VERSION = 'ch1-v2';` — rather than relying on the filename alone to carry that information. Filenames are easy to lose track of once a file has been downloaded, renamed by a browser, or re-uploaded; a version string embedded in the file itself survives all of that, and it means a loader could theoretically warn if it's reading a save produced by a newer or older chapter than the HTML it's running in. This is a small addition with a real payoff for a project that's already accumulated one duplicate-file incident and is heading toward dynamically generated chapters, where version drift will only get more likely, not less.

---

## 14. Known Inconsistencies Still Open (as of this doc)

Items resolved since the last version of this doc are noted inline below. Remaining open items only:

- ~~Ch1's `ch1LedgerCount` lives at `gs.ch1LedgerCount` (top-level); Ch2/Ch3 use `gs.flags.ch1LedgerCount` / `ch3LedgerCount` (nested).~~ **Resolved in Ch1 patch:** `ch1LedgerCount` now lives under `gs.flags` in Ch1, matching Ch2/Ch3. `gs.flags` also added to Ch1 initial state and restored in `loadState()`.
- ~~localStorage key naming (`wbn_save_ch1` vs. `wbn_ch2_save`/`wbn_ch3_save`) is inconsistent.~~ **Resolved in Ch1 patch:** Ch1 now uses `wbn_ch1_save`, matching the `wbn_ch{N}_save` convention.
- ~~Save-string `chapter` field naming is inconsistent (`'prologue'`, `'one'`, `'chapter_two'`, `'chapter_three'`).~~ **Resolved in Ch1 patch:** Ch1 save string now uses `'chapter_one'`. Canonical values: `'prologue' | 'chapter_one' | 'chapter_two' | 'chapter_three' | 'chapter_four'`.
- No loader validates that a pasted save string actually came from the expected predecessor chapter.
- If a player skips the creditor's letter at `letter_junction` in favor of finding Idris first, there's no return path to read it later — it's simply never resolved on that branch.
- Project Files does not overwrite or auto-rename on same-name upload — no longer a live risk now that GitHub is the source of truth (see §13), but no chapter file currently embeds a version marker, so a similar problem could recur if the repo convention slips.

**Resolved since the last version of this doc:** the skill-check mechanic (§5, revived Ch2/Ch3) · hot/cold differentiation (§5A, now a running mechanic) · `letter_opened` being set but never consumed (now read in Ch3's `morning_three` and its hot-open variant, and required again in Ch4 — see §15) · `chapter_complete`/`ch3_complete` flags are still set but still unread; low priority since nothing currently needs them, but worth a look if Ch4 wants to check "did the player complete Ch3 cleanly."

---

## 15. Chapter Four — Pre-Chapter Contract

*Written before any Ch4 scene code, per the working rhythm established after the Ch2/Ch3 revision pass. This is a contract, not a first draft — it should be revised if the actual writing wants to diverge from it, but divergence should be a decision, not a drift.*

**Emotional arc:** Vothren was expected. Farren arrives instead. Everything the player has built over three chapters — cover, alliances, the reading sense's growing reach, whatever's left of who they were — gets tested in a meeting that was supposed to resolve things and doesn't. The chapter should end with the player understanding, for the first time with real clarity, that this isn't over and that Vothren's patience is not a mercy. The deception holds (or partially holds); the stakes clarify; the near-slip of the player's real self is felt but not yet seen. Ch4 is a pressure chamber, not a climax.

**Who is Aldous Farren:** Vothren's business associate. A man of careful middles — neither threatening nor warm, politeness calibrated to give nothing away. He handles estate valuation and debt assessment (directly relevant to Voss Aldane's situation). He makes one observation about Tessaly before departing: *"She has her father's patience."* He does not elaborate. NPC schema entry: starts suspicion 30 / trust 0. Whether he carries a favorable or unfavorable report back to Vothren should depend on the player's Cover Integrity and the choices made in his presence — but he should never feel like the actual threat; he's the measuring instrument.

**Pell's position in Ch4:** He installed the fake and knows it. Farren doesn't. This makes Pell an uneasy co-conspirator for the duration of the meeting — he needs the cover to hold at least as much as the player does, which is a new dynamic. He is now in the NPC schema with trust/suspicion live. His suspicion register differs from the household's: for him it means *"is she worth what this cost me?"*, not *"does she belong here?"* Trust with Pell in Ch4 should be harder to move in either direction than with household NPCs — he's performing alongside the player, not evaluating from the outside, and that changes what gestures matter.

**Scene list (confirmed before build):**
1. Morning preparation — brief and tense; documents in order, Maren and/or Idris present depending on Ch3 alliance state; the household knows what was expected and registers that something feels wrong before Farren arrives
2. Farren's arrival — **the hot/cold showcase moment** (§5A, reserved for this beat): a hot reader reads him before he's spoken; a cold reader can choose to hold off and read him deliberately once seated, at the cost of whatever the door itself would have told them in the first second
3. The meeting proper — Farren presents Vothren's regrets and terms; **should be a skill check** (§5), Cover Integrity vs. Farren's suspicion; Pell present and managing his own performance
4. *"She has her father's patience"* — the observation lands; different NPCs react differently; the player cannot ask what it means without exposing themselves; this is the chapter's emotional center
5. The `letter_opened` payoff — a player who read Voss's letter in Ch2 has language available here that an unforewarned player doesn't (third use of this flag; see §1A and §7)
6. Farren's departure — a brief, permanent choice (✦) about whether the player says anything as he leaves; low Cover Integrity may foreclose the cleaner options
7. Aftermath — the household reconvenes; alliances shift or solidify depending on how the meeting went; the chapter closes with the player understanding that Vothren is coming himself next time; **the near-slip beat** (internal only — the player feels their real self almost surface at Farren's observation; no one in the scene sees it; high Rootedness makes this more present in the prose; see §8)

**Stat gates (confirmed before build):**
- High Cover Integrity: unlocks a clean negotiation path with Farren; low Cover Integrity forecloses the most favorable version of scene 3
- Reading Exposure ≥ 25: Farren's terms arrive with a different weight — he references something he shouldn't know unless Vothren has been watching more carefully than expected
- Rootedness: no hard gate, but colors the near-slip beat and the aftermath prose — high Rootedness players feel the pull toward naming themselves; low Rootedness players feel the pull toward escape

**Flag contract:**
- Reads: `letter_opened` (§7), `maren_saw_reading` (§7), `ch3_complete` (loader validation), NPC trust/suspicion from Ch3 endings (no explicit alliance flags set in Ch3 — read `gs.npcs` scores directly with documented thresholds)
- Sets: `ch4_complete`; `farren_favorable` or `farren_unfavorable` (determines Vothren's posture in Ch6); at minimum one permanent marker from scene 6 (name TBD when drafted)

**NPC state targets by chapter end:**
- Farren: departed; his trust/suspicion frozen at end-of-chapter values and carried forward (they matter in Ch6 when Vothren references his report)
- Pell: trust/suspicion live for the first time; his final Ch4 position sets his posture for Ch5
- Maren: a clear position confirmed — the chapter should not end with her alliance ambiguous if Ch3 didn't
- Idris: present if his Ch3 alliance held; his presence in scene 1 is meaningful

**Chapter boundary — what the player knows when Ch4 ends:** Vothren was not here. He sent someone instead. Whatever was supposed to be resolved is deferred. The household is more pressured, not less. And somewhere in the middle of the meeting, the player almost said their own name — and caught it. Ch5 begins with that almost still in the room.

---

*This document should be updated whenever a chapter introduces a new mechanic, a new NPC, or a new flag — the update is part of finishing the chapter, not a separate later task.*
