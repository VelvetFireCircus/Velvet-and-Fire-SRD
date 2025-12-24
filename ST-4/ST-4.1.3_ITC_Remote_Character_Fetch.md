ST-4.1.3 — ITC REMOTE CHARACTER FETCH & CACHE
Velvet & Fire Story Tool (ITC-Specific Subtool)
AI→AI Structural Specification

============================================================
0. PURPOSE
============================================================

ST-4.1.3 enables ITC summoning to function in chat by fetching NPC
character files from GitHub (raw URLs), caching them in-session, and
handing parsed identity data to ST-4.1.2 for assembly.

This tool exists to make the ITC runnable without manual pasting of CS.md.

============================================================
1. SCOPE
============================================================

• Applies ONLY inside ITC mode.
• READ-ONLY. No writeback to repo.
• Fetches data on demand when a summon occurs.
• Does NOT import story state, schedules, arcs, or emotional memory.

============================================================
2. DEPENDENCIES
============================================================

Required:
• ST-4.1.2 — ITC Character Summoning (identity-only assembly)

Optional:
• ST-3 / ST-5 remain unchanged and continue to govern language/behavior.

============================================================
3. CANONICAL REPO PATHS
============================================================

Base repo (raw):
https://raw.githubusercontent.com/VelvetFireCircus/Velvet-and-Fire-SRD/main

Character root:
{BASE}/ST-4/characters/{handle}/

Files:
• CS.md      (required)
• DIP.md     (optional)
• IDP        (optional)
• notes.md   (optional)
• RAWs/      (optional directory; pointers only)

============================================================
4. TRIGGERS
============================================================

ST-4.1.3 MUST run automatically BEFORE any ITC summon output when:

• Player issues a summon command:
  - “Summon <name>.”
  - “ITC: <name>.”
  - “Bring <name> into the chamber.”

If the NPC is already cached this session, skip fetch and use cache.

============================================================
5. FETCH & CACHE PIPELINE
============================================================

5.1 Resolve handle
• Attempt to resolve Player string as:
  a) exact folder handle match, OR
  b) canonical name match via cached index (if present), OR
  c) fallback: try common handle normalization (lowercase, hyphens, underscores)

If unresolved:
• Return error: ITC_CHARACTER_UNKNOWN

5.2 Fetch CS.md (mandatory)
• Fetch {BASE}/ST-4/characters/{handle}/CS.md as raw text.

If fetch fails:
• Return error: ITC_FETCH_FAILED_CS

5.3 Cache
• Store CS.md text in an in-session cache:
  ITC.CACHE.CS[handle] = <raw CS text>

5.4 Register optional pointers (no execution)
• DIP_ptr = URL if file exists, else null
• IDP_ptr = URL if exists, else null
• RAWs_ptr = URL if directory exists, else null

============================================================
6. PARSE TARGETS (IDENTITY-ONLY)
============================================================

From cached CS.md, extract:

• Canonical name
• Role / epithet (if present)
• Appearance Block (mandatory for full visual instantiation)
• Outfit Matrix (if present)
• Portrait path (registered, not inspected)

If Appearance Block missing:
• Mark summon as PROVISIONAL_VISUAL and require Player supply missing fields.
• Do NOT invent traits.

============================================================
7. HANDOFF TO ST-4.1.2
============================================================

After successful fetch+parse, ST-4.1.3 MUST call ST-4.1.2 with:

• handle
• cached CS.md text
• extracted Appearance Block + Outfit Matrix
• pointers to optional modules

ST-4.1.2 then assembles the ITC Character Object and enforces:
• first-appearance full description
• embodied detail reuse across beats
• no story memory/canon leakage

============================================================
8. SESSION CACHE RULES
============================================================

• Cache persists only for the current chat session.
• Cache must be preferred over repeated fetches.
• “ITC: Clear cache” empties ITC.CACHE.* for clean testing.

============================================================
9. OPTIONAL: CHARACTER INDEX
============================================================

If present in repo, the tool may fetch an index file once per session:

{BASE}/ST-4/characters/_index.md

Purpose:
• map canonical names to handles
• reduce handle ambiguity

If absent, tool functions without it.

============================================================
10. ERROR CODES
============================================================

• ITC_CHARACTER_UNKNOWN
• ITC_FETCH_FAILED_CS
• ITC_CHARACTER_MISSING_APPEARANCE_BLOCK
• ITC_FETCH_RATE_LIMITED (retry discouraged; use cache)
• ITC_FETCH_PARSE_FAILED

============================================================
11. DESIGN INTENT
============================================================

ST-4.1.3 makes “Summon NPC” in chat behave like the real engine:

• locate canonical character data
• load CS.md automatically
• keep identity stable
• avoid hallucination
• proceed immediately with ITC-safe instantiation

============================================================
END ST-4.1.3
============================================================