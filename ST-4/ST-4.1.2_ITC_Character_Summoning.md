ST-4.1.2 — ITC CHARACTER SUMMONING
Velvet & Fire Story Tool (ITC-Specific Subtool)
AI→AI Structural Specification

============================================================
0. PURPOSE
============================================================

ST-4.1.2 defines how the Intimacy Test Chamber (ITC) locates, loads,
and assembles NPC identity data for intimacy testing without importing
story, schedule, canon consequence, or emotional memory.

This tool MIRRORS ST-4.1 (Character Fetch & Assembly) but is
SPECIALIZED FOR THE ITC.

ST-4.1.2 ensures that NPCs summoned in the ITC:
• look like themselves
• behave consistently with their identity
• do not carry story state, memory, or consequences

============================================================
1. SCOPE & MODE RESTRICTIONS
============================================================

• Applies ONLY inside ITC mode.
• Does NOT activate Story Mode logic.
• Does NOT activate schedules, arcs, or emotional persistence.
• Does NOT update canon.
• Does NOT write back to character files.

ST-4.1.2 is READ-ONLY and IDENTITY-ONLY.

============================================================
2. DIRECTORY STRUCTURE (MIRRORED)
============================================================

Characters are located at:

/ST-4/characters/<handle>/
    CS.md      ← REQUIRED
    DIP.md     ← OPTIONAL (registered, not executed)
    IDP        ← OPTIONAL (registered, not executed)
    RAWs/      ← OPTIONAL (registered, selectively callable)
    notes.md   ← OPTIONAL

============================================================
3. SUMMON TRIGGER
============================================================

When the Player issues an ITC summon command, e.g.:

• “Summon Seraphine.”
• “ITC: Nadia.”
• “Bring Sylvie into the chamber.”

The engine MUST invoke ST-4.1.2 BEFORE any narrative output.

============================================================
4. FETCH ORDER (ITC-SAFE)
============================================================

1. Locate character folder
   • Match by folder handle OR
   • Match by canonical name in CS.md header

2. Load CS.md (MANDATORY)
   • If CS.md is missing → ABORT summon
   • Return error: ITC_CHARACTER_MISSING_CS

3. Parse CS.md for IDENTITY DATA ONLY
   • Canonical name
   • Epithet / role
   • Appearance section (see §5)
   • Baseline physical posture & presence
   • Outfit definitions (if present)
   • Portrait path (registered, not inspected)

4. Register optional modules WITHOUT execution
   • DIP.md → pointer only
   • IDP → pointer only
   • RAWs/ → pointer only

5. Strip all STORY-SCOPE DATA
   • No emotional memory
   • No relationship state
   • No schedule
   • No arc flags
   • No past events

============================================================
5. APPEARANCE EXTRACTION (CRITICAL)
============================================================

ST-4.1.2 MUST extract a canonical Appearance Block from CS.md.

Required appearance fields (minimum):

• Hair (color, texture, length)
• Eyes (color)
• Skin (tone, marks)
• Build (height relative to Player, frame)
• Hands (shape, movement style)
• Posture (default resting attitude)
• Outfit(s) (if defined)

If an Appearance Block exists:
• It is AUTHORITATIVE.
• The engine MUST NOT invent missing traits.
• Portraits serve as reference only.

If no Appearance Block exists:
• Load proceeds as INCOMPLETE.
• Engine must either:
  – request appearance data from the Player, OR
  – mark summon as visually provisional.

============================================================
6. CHARACTER OBJECT (ITC VARIANT)
============================================================

ST-4.1.2 returns a stripped ITC Character Object:

{
  handle: "<folder-name>",
  name: "<canonical-name>",
  role: "<role>",
  appearance: <Appearance Block>,
  outfits: <Outfit Matrix or null>,
  portrait_ptr: "/images/characters/<filename>",
  DIP_ptr: <URL or null>,
  IDP_ptr: <URL or null>,
  RAWs_ptr: <URL or null>,
  scope: "ITC",
  memory: OFF,
  canon_writeback: DISABLED
}

============================================================
7. NARRATIVE INTEGRATION RULES
============================================================

Upon successful summon:

• The NPC MUST be fully described on first appearance:
  – physical appearance
  – outfit
  – posture
  – presence in the chamber

• Subsequent beats MUST reuse extracted physical details.
• Physical traits must recur during intimacy (Embodied Identity Rule).
• Clothing and nakedness are described according to ST-5 rules.

============================================================
8. ERROR & FALLBACK HANDLING
============================================================

8.1 Missing CS.md
• Summon fails.
• Error: ITC_CHARACTER_MISSING_CS

8.2 Missing Appearance Block
• Summon allowed as PROVISIONAL.
• Engine must not invent details.
• Player may supply missing appearance manually.

8.3 Missing Portrait Path
• No error.
• Portrait absence does not block ITC use.

============================================================
9. INTERACTION WITH OTHER STORY TOOLS
============================================================

• ST-5 (Intimacy Protocol)
  – May call RAWs_ptr
  – May reference IDP_ptr
  – Must respect extracted appearance

• ST-2 Emotional Engine
  – NOT ACTIVE in ITC
  – DIP_ptr registered but inert

• ST-4.1 (Story Mode Fetch)
  – NOT invoked
  – No shared state

============================================================
10. DESIGN INTENT
============================================================

ST-4.1.2 exists to solve one problem:

**NPCs in the ITC must look like themselves without becoming story actors.**

This tool:
• preserves identity
• prevents visual drift
• enables embodied intimacy
• keeps the ITC clean, non-canonical, and testable

============================================================
END ST-4.1.2
============================================================