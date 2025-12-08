===============================
ST-4.2_Character-Index
Velvet & Fire Story Tool (Cast Audit & Index)
AI→AI Structural Specification
===============================

# ST-4.2 — CHARACTER INDEX  
### *Velvet & Fire Story Tool (Cast Audit & Index)*

**Version:** 0.1  
**Status:** Transitional — To be expanded as new characters are added

---

## 0. PURPOSE & SCOPE

ST-4.2 provides a **single, machine-readable index** of all Velvet & Fire
characters currently recognized by the engine.

It is used to:

1. List all character folders under `/ST-4/characters/`.  
2. Track each character’s **compliance state** (full / provisional / ambient).  
3. Expose the presence or absence of:
   - CS.md (Character Sheet)
   - DIP.md (Emotional Engine profile)
   - RAWs/ (Intimacy RAW modules)
   - canonical portrait path
4. Support **Architect Mode audits** and **Story Mode readiness checks**.

This tool does **not** define canon; it **points to** canon resources defined in
ST-4, ST-4.1, and the Character Sheets themselves.

---

## 1. CONVENTIONS

- One row = one character.  
- `handle` must match the folder name under `/ST-4/characters/<handle>/`.  
- Paths are **repository-relative**, not full URLs.  
- `status` indicates engine readiness:

  - `full`        → CS + DIP + portrait, template-compliant  
  - `provisional` → CS present but incomplete and/or missing modules  
  - `ambient`     → minimal presence; cannot carry full emotional/narrative load  

- This file is **authoritative for audit purposes**, not for lore.
- Any missing or unknown field may be left as `-` or `todo`.

---

## 2. CHARACTER INDEX TABLE

> NOTE: This table is intentionally small to start.  
> Add or update rows as characters are created, rebuilt, or promoted.

| id  | handle        | display_name | role_epithet                  | status      | CS_path                                   | DIP_path                                  | RAWs_path                                 | portrait_path                                   | notes                                  |
|-----|---------------|-------------|-------------------------------|-------------|-------------------------------------------|-------------------------------------------|-------------------------------------------|-----------------------------------------------|----------------------------------------|
| C01 | sylvie        | Sylvie      | The Trickster Flame           | full        | /ST-4/characters/sylvie/CS.md            | /ST-4/characters/sylvie/DIP.md            | /ST-4/characters/sylvie/RAWs/            | /images/characters/sylvie_canon.png          | Canon portrait locked.                 |
| C02 | joelle        | Joelle      | The Harlequin Flyer           | full        | /ST-4/characters/joelle/CS.md            | /ST-4/characters/joelle/DIP.md            | /ST-4/characters/joelle/RAWs/            | /images/characters/joelle_canon.png          | Uses canonical flyer portrait.         |
| C03 | nadia         | Nadia       | The Mystic (Madame Astraea)   | full        | /ST-4/characters/nadia/CS.md             | /ST-4/characters/nadia/DIP.md             | /ST-4/characters/nadia/RAWs/             | /images/characters/nadia_canon.png           | Tattoos + DIP integrated.              |
| C04 | anton         | Anton       | [fill epithet]                | provisional | /ST-4/characters/anton/CS.md             | /ST-4/characters/anton/DIP.md             | /ST-4/characters/anton/RAWs/             | /images/characters/anton_canon.png           | Recently rebuilt; verify DIP/RAWs.     |
| C05 | elias         | Elias       | Torch Master & Ignition Partner | provisional | /ST-4/characters/elias/CS.md           | /ST-4/characters/elias/DIP.md             | /ST-4/characters/elias/RAWs/             | /images/characters/elias_canon.png           | Check meteor-ritual hooks.             |
| C06 | marlowe       | Marlowe     | Ringmaster                    | provisional | /ST-4/characters/marlowe/CS.md           | /ST-4/characters/marlowe/DIP.md           | /ST-4/characters/marlowe/RAWs/           | /images/characters/marlowe_canon.png         | Needs DIP/RAW audit.                   |
| C07 | edda          | Edda        | Cook & Den Mother             | full        | /ST-4/characters/edda/CS.md              | /ST-4/characters/edda/DIP.md              | /ST-4/characters/edda/RAWs/              | /images/characters/edda_canon.png            | Includes Breathing Train hooks.        |
| C08 | tobias_finch  | Tobias Finch| Twenty-Four-Hour Man          | provisional | /ST-4/characters/tobias_finch/CS.md      | /ST-4/characters/tobias_finch/DIP.md      | /ST-4/characters/tobias_finch/RAWs/      | /images/characters/tobias_finch_canon.png    | Scout / advance.                       |
| C09 | gideon_vale   | Gideon Vale | Twenty-Four-Hour Man          | provisional | /ST-4/characters/gideon_vale/CS.md       | /ST-4/characters/gideon_vale/DIP.md       | /ST-4/characters/gideon_vale/RAWs/       | /images/characters/gideon_vale_canon.png     | Scout / advance.                       |
| C10 | clara         | Clara       | Aerial Sister                 | provisional | /ST-4/characters/clara/CS.md             | /ST-4/characters/clara/DIP.md             | /ST-4/characters/clara/RAWs/             | /images/characters/clara_canon.png           | Joelle’s partner in flight.           |
| C11 | rattlejack    | Rattlejack  | Drummer & Sketch Artist       | provisional | /ST-4/characters/rattlejack/CS.md        | /ST-4/characters/rattlejack/DIP.md        | /ST-4/characters/rattlejack/RAWs/        | /images/characters/rattlejack_canon.png      | Includes meteor sketch artifact.       |
| C12 | juniper       | Juniper     | Props & Repairs               | ambient     | /ST-4/characters/juniper/CS.md           | -                                         | -                                         | /images/characters/juniper_canon.png         | To be expanded beyond ambient.         |
| C13 | junia         | Junia       | Kitchen Angel                 | ambient     | /ST-4/characters/junia/CS.md             | -                                         | -                                         | /images/characters/junia_canon.png           | Renamed from duplicate Juniper.        |
| C14 | petra         | Petra       | Animal Trainer                | ambient     | /ST-4/characters/petra/CS.md             | -                                         | -                                         | /images/characters/petra_canon.png           | Animal acts WIP.                       |
| C15 | lark          | Lark        | Rope Crew                     | ambient     | /ST-4/characters/lark/CS.md              | -                                         | -                                         | /images/characters/lark_canon.png            | Edge / rope presence only (for now).   |
| C16 | bram          | Bram        | Edge Crew                     | ambient     | /ST-4/characters/bram/CS.md              | -                                         | -                                         | /images/characters/bram_canon.png            | Edge crew.                             |
| C17 | finn          | Finn        | Rope Crew                     | ambient     | /ST-4/characters/finn/CS.md              | -                                         | -                                         | /images/characters/finn_canon.png            | Rope crew.                             |

> You may add, remove, or reclassify rows as your GitHub `characters/` directory evolves.

---

## 3. USAGE IN ARCHITECT MODE

In Architect Mode, ST-4.2 is primarily for:

- **Visual audits** — spotting missing DIPs, RAWs, portraits.  
- **Planning** — choosing which character to upgrade next.  
- **Cross-checking** — making sure ST-4, ST-4.1, and the repo agree on who exists.  

Typical Architect queries powered by ST-4.2:

- “Which characters are still `ambient`?”  
- “List all `provisional` characters missing DIPs.”  
- “Show me all `full` NPCs with complete portraits.”  

Because the table is human-editable, you can also keep quick notes in the `notes` column for future passes.

---

## 4. USAGE IN STORY MODE

In Story Mode, ST-4.2:

- Provides a quick **eligibility filter** for ST-7 (Narrative Engine).  
- Ensures only `full` or appropriate `provisional` NPCs are considered for:
  - spotlight scenes  
  - emotional pivots  
  - intimacy-enabled encounters  

ST-4.1 still performs the detailed fetch & validation, but ST-4.2 gives it a **shortlist** of likely candidates when needed.

---

## 5. MAINTENANCE RULES

- Whenever a new character folder is created under `/ST-4/characters/`, add a row.  
- When a character’s CS becomes template-compliant and fully resourced:
  - Update `status` → `full`.  
- When a character is deprecated or moved to “Elsewhere”/legacy use:
  - Keep the row, add a note (e.g., “Elsewhere only”).  

This file should be treated as **lightweight but authoritative** for cast inventory.

---

## 6. INTEGRITY MARKERS

- **ST-4.2-ID:** DP-INDEX-v0.1  
- **Validated With:** ST-4, ST-4.1  
- **Maintainer:** VelvetFireCircus Project  

===============================
END ST-4.2
===============================