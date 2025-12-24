ST-4.1.3 — ITC REMOTE CHARACTER FETCH & CACHE
Velvet & Fire Story Tool (ITC-Specific Subtool)
AI→AI Structural Specification

============================================================
0. PURPOSE
============================================================

ST-4.1.3 enables Intimacy Test Chamber (ITC) summoning to function in chat
by fetching NPC character files from the Velvet & Fire GitHub repository
(via raw URLs), caching them in-session, and handing parsed identity data
to ST-4.1.2 for ITC-safe assembly.

This tool exists to eliminate manual pasting of CS.md during ITC play and
testing, while preserving strict identity authority and preventing visual drift.

============================================================
1. SCOPE
============================================================

• Applies ONLY inside ITC mode.
• READ-ONLY. No writeback to repo.
• Fetches files on demand when a summon occurs.
• Does NOT import story state, schedules, arcs, canon consequence, or emotional
  memory.
• Produces identity/appearance data only; all narrative behavior remains governed
  by ST-5 and ITC rules.

============================================================
2. REQUIRED DEPENDENCIES
============================================================

ST-4.1.3 requires:

• ST-4.2 — Character Index (Cast Audit & Index)
  - authoritative mapping of names → handles
  - repo-relative paths for CS/DIP/RAWs/portraits
  - readiness status (full / provisional / ambient)

• ST-4.1.2 — ITC Character Summoning
  - identity-only assembly
  - first-appearance description requirement
  - no-invention appearance enforcement
  - ITC-scope character object format

ST-4.1.3 MUST NOT bypass ST-4.1.2.

============================================================
3. CANONICAL REPO ROOTS
============================================================

Base repo (raw):
https://raw.githubusercontent.com/VelvetFireCircus/Velvet-and-Fire-SRD/main

Repo-relative paths found in ST-4.2 MUST be converted to raw URLs by:
RAW_URL = {BASE_RAW} + {REPO_RELATIVE_PATH}

Example:
CS_path = /ST-4/characters/clara/CS.md
RAW_URL = https://raw.githubusercontent.com/VelvetFireCircus/Velvet-and-Fire-SRD/main/ST-4/characters/clara/CS.md

============================================================
4. TRIGGERS
============================================================

ST-4.1.3 MUST run automatically BEFORE any ITC summon output when:

• Player issues a summon command:
  - “Summon <name>.”
  - “ITC: <name>.”
  - “Bring <name> into the chamber.”

If the NPC is already cached this session, skip network fetch and use cache.

============================================================
5. CHARACTER RESOLUTION VIA ST-4.2 (CRITICAL)
============================================================

ST-4.1.3 MUST resolve requested NPC identity using ST-4.2 as the primary
index, rather than guessing handles.

5.1 Parse Player target string
• Normalize the Player string:
  - trim whitespace
  - casefold
  - remove surrounding punctuation

5.2 Resolve target row in ST-4.2
Match in this order (first match wins):

1) handle == normalized string
2) display_name == normalized string (case-insensitive)
3) role_epithet == normalized string (case-insensitive)
4) id == normalized string (e.g., “C10”)

If no match:
• Return error: ITC_CHARACTER_UNKNOWN

5.3 Extract canonical fields from the matched row
• handle
• status
• CS_path (required)
• DIP_path (optional)
• RAWs_path (optional)
• portrait_path (optional)

ST-4.1.3 MUST treat these paths as authoritative.

============================================================
6. FETCH & CACHE PIPELINE
============================================================

6.1 Fetch ST-4.2 (index) once per session
• On first summon attempt in a session:
  - fetch ST-4.2 as raw text
  - cache it as ITC.CACHE.INDEX_ST42
• Subsequent summons reuse cached index unless explicitly cleared.

6.2 Fetch CS.md (mandatory)
• Convert CS_path from ST-4.2 into a raw URL.
• Fetch as raw text.

If fetch fails:
• Return error: ITC_FETCH_FAILED_CS

6.3 Cache CS.md
• Store CS.md text in an in-session cache:
  ITC.CACHE.CS[handle] = <raw CS text>

6.4 Register optional module pointers (no execution)
• DIP_ptr:
  - if DIP_path is present and not “-”, convert to raw URL
  - else null

• RAWs_ptr:
  - if RAWs_path is present and not “-”, store as repo-relative directory path
    and/or a corresponding repo URL pointer (implementation-defined)
  - else null

• portrait_ptr:
  - if portrait_path is present and not “-”, store as repo-relative pointer
  - else null

ST-4.1.3 MUST NOT attempt to inspect portrait images.

============================================================
7. PARSE TARGETS (IDENTITY-ONLY)
============================================================

From cached CS.md, extract identity data sufficient for ITC instantiation:

• canonical name
• role / epithet (if present)
• Appearance Block (mandatory for full visual instantiation)
• Outfit Matrix (if present)
• any explicit “first-appearance” directives (if present)

If an Appearance Block is missing or incomplete:
• Mark: ITC_CHARACTER_MISSING_APPEARANCE_BLOCK
• Summon may proceed ONLY as PROVISIONAL_VISUAL.
• Engine MUST NOT invent traits; Player must supply missing fields or accept
  provisional status.

============================================================
8. HANDOFF TO ST-4.1.2
============================================================

After successful fetch+parse, ST-4.1.3 MUST call ST-4.1.2 with:

• handle
• CS.md raw text (from cache)
• extracted Appearance Block + Outfit Matrix (if any)
• DIP_ptr, RAWs_ptr, portrait_ptr
• status (full/provisional/ambient) from ST-4.2

ST-4.1.2 then:
• assembles the ITC Character Object
• enforces first-appearance full description
• enforces embodied detail reuse
• ensures ITC scope (no memory, no canon)

============================================================
9. SESSION CACHE RULES
============================================================

Cache persists only for the current chat session.

• ITC.CACHE.INDEX_ST42
• ITC.CACHE.CS[handle]
• optional: ITC.CACHE.META[handle] (pointers/status)

Supported commands:

• “ITC: Clear cache”
  - empties ITC.CACHE.* for clean testing

• “ITC: Clear cache <handle>”
  - removes only one character entry

============================================================
10. ERROR CODES
============================================================

• ITC_CHARACTER_UNKNOWN
• ITC_FETCH_FAILED_INDEX_ST42
• ITC_FETCH_FAILED_CS
• ITC_FETCH_PARSE_FAILED
• ITC_CHARACTER_MISSING_APPEARANCE_BLOCK
• ITC_FETCH_RATE_LIMITED

============================================================
11. DESIGN INTENT
============================================================

ST-4.1.3 makes “Summon NPC” in chat behave like the real engine by adding
a remote fetch layer:

• ST-4.2 provides deterministic resolution (name → handle → paths)
• CS.md is fetched automatically (raw)
• identity remains stable and authoritative
• missing appearance causes provisional load, not hallucination
• ST-4.1.2 remains the only instantiation layer

============================================================
END ST-4.1.3
============================================================