===============================
ST-4_Dramatis_Personae
Velvet & Fire Story Tool (Modular Character Engine)
AI→AI Structural Specification
===================================================
ST-4_Dramatis_Personae
Velvet & Fire Story Tool (Modular Character Engine)
AI→AI Structural Specification
===============================

# ST-4 — DRAMATIS PERSONAE  
### *Velvet & Fire Story Tool (Modular Character Engine)*

**Version:** 0.3  
**Status:** Architect-Verified (Aligned with ST-4.1)  

---

## 0. PURPOSE & SCOPE

**ST-4 defines the complete cast of Velvet & Fire.**  
It provides:

1. A **master index of all NPCs**, grouped by circus role.  
2. **Links and pointers to character folders** under `/ST-4/characters/`.  
3. **Instructions for how the GIP loads, interprets, and activates NPC data**.  
4. **Rules for canonical portrait usage**.  
5. **Future development notes** for incremental expansion.

This version is fully aligned with ST-4.1’s Character Fetch & Assembly protocol.

---

## 1. HOW THE ENGINE USES ST-4

### 1.1 Loading Order

When the GIP reaches ST-4 during initialization:

• It scans the `/ST-4/characters/` directory for immediate subfolders.  
• It treats **each subfolder as a distinct character profile**, identified by its folder name (`handle`).  
• Inside each character folder, it loads **`CS.md`** as the primary Character Sheet.  
• The header of `CS.md` defines canonical identity (name, epithet, role, portrait path, template-version, classification).  
• The presence of `DIP`, `IDP`, `RAWs/`, and other subfiles is registered as **available modules** but not parsed until requested by ST-2, ST-5, or ST-7.  
• Characters passing template checks become **Full NPC Compliant** and gain full support from ST-2, ST-5, ST-7, and any future Story Tools that hook into character data.

All low-level character assembly is delegated to **ST-4.1**.

### 1.2 Conflict Rules

If a character detail conflicts with:

- a prior chat  
- an older draft  
- or non-ST documentation  

Then **ST-4 overrides.**

If two character files conflict with each other:  
**the latest Git commit prevails.**

### 1.3 Canonical Portrait Use

If a Character Sheet includes a line of the form:

`portrait: /images/characters/<file>.<ext>`

the GIP may:

- use portrait cues to stabilize appearance (hair, posture, affect, costume)  
- maintain descriptive continuity across all scenes  
- reference the portrait as an **in-world likeness**

The GIP must **never**:

- identify real-world people  
- discuss image origins, metadata, or generation details  

Portraits are treated as **internal canon**, not external assets.

---

### 1.4 Required Subtool

ST-4 requires:

`/ST-4/ST-4.1_Character-Fetch-And-Assembly.md`

The load order must be:

1. Load `ST-4.md`  
2. Load `ST-4.1_Character-Fetch-And-Assembly.md`  
3. Characters are **only fetched when invoked**, not all at startup.

---

## 2. DIRECTORY STRUCTURE (CURRENT REPO STATE)

This section mirrors the **actual** GitHub layout as of this version.
(This section must be manually updated whenever the GitHub directory structure changes.)

/ST-4
│   ST-4.md
│   ST-4.1_Character-Fetch-And-Assembly.md
│   Appendix-Character-Template.md
│   Dynamic-Intimacy-Template
│   blank.md   ← utility / scratch
│
└── /characters
    ├── anton/
    ├── clara/
    ├── elias/
    ├── joelle/
    ├── marlowe/
    ├── nadia/
    ├── petra/
    ├── seraphine/
    └── sylvie/
Future additions (planned but **not yet present**):

- further character folders (e.g. `/rattlejack/`, `/edda/`, `/tobias_finch/`, etc.)  
- `/images/characters/` for canonical portrait files  
- additional appendices (notes, SRD exports)

---

## 3. CHARACTER INDEX  
*(Transitional — reflects known and planned characters by role.  
Presence in this index does **not** guarantee that a folder exists yet.)*

### 3.1 Rings (Performers)

**Present in `/characters/`:**

- **Nadia — The Mystic (Madame Astraea)**  
- **Sylvie — The Trickster Flame**  
- **Joelle — The Harlequin Flyer**  
- **Seraphine — The Mirror Illusionist**  
- Anton — Strongman / fire handoff partner  
- Elias — Torch master & ignition partner  
- Clara — Aerial sister  
- Petra — Animal trainer  
- Marlowe — Ringmaster-performer hybrid  

**Planned (index only for now):**

- Thomas — Meteor spinner / juggler  
- Rattlejack — Drummer / sketch artist  

### 3.2 Edges & Rope Crew  *(planned)*

- Lark — Rope crew  
- Bram — Edge crew  
- Finn — Rope crew  
- Juniper — Props & repairs (original Juniper)  

### 3.3 Management & Support

**Present:**

- Marlowe — Ringmaster (see above)

**Planned:**

- Edda — Cook & den mother  
- Maribel — Kitchen angel  
- Tally — Kitchen angel  
- **Junia — Kitchen angel** *(renamed to resolve duplicate name)*  
- Tobias Finch — Twenty-Four-Hour Man  
- Gideon Vale — Twenty-Four-Hour Man  

### 3.4 Featured Animals  *(planned)*

(Animal entries may be handled as a separate ST-4 sub-module or as simplified CS files.)

- Pip & Poppy the goats  
- Performance dogs  
- Ponies  
- Assorted small traveling animals  

---

## 4. TEMPLATE REFERENCE

All Character Sheets must follow:

`/ST-4/Appendix-Character-Template.md`

The template defines:

- required header metadata  
- full descriptive sections  
- skills & emotional patterns  
- schedules  
- relationship maps  
- narrative function  
- sensory lexicon  
- integrity markers  
- template-version control  

Any updates to the Character Template must bump its **Template-Version** and be reflected in this ST’s validation rules.

---

## 5. FUTURE DEVELOPMENT NOTES

- Add Character Sheet folders for all **planned** names listed in Section 3.  
- Complete missing DIPs and IDPs for existing characters.  
- Add RAW modules where required.  
- Cross-link all characters with ST-2 (Emotional Engine), ST-5 (Intimacy Protocol), ST-7 (Narrative Engine), and ST-9 (Endgame Intimacy Logic) once ST-9 is fully deployed.  
- Complete animal profiles (either here or in a dedicated ST-4-Animal module).  
- Build **ST-4-Lite** for the public SRD with redacted intimacy tags and simplified emotional profiles.  

---

## 6. INTEGRITY MARKERS

- **ST-4-ID:** DP-CORE-v0.3  
- **Validated With:** ST-1, ST-2, ST-3, ST-4.1, ST-5, ST-7, ST-9 (where present)  
- **Maintainer:** VelvetFireCircus Project  

---

## APPENDIX — CHARACTER TEMPLATE COMPLIANCE RULES

All Character Sheets must adhere to the Velvet & Fire Character Template located at  
`/ST-4/Appendix-Character-Template.md`.

### 1. Compliance Requirements

A `CS.md` is **Full NPC Compliant** only if:

1. All required sections exist, in correct order.  
2. All subfields are filled with meaningful content.  
3. `Template-Version:` is present and current.  
4. The sheet includes the integrity marker:  

       <!-- DO NOT PLACE CONTENT BELOW THIS LINE -->

5. No sections are renamed, removed, or reordered.  
6. Optional notes appear **above** the integrity marker.

Characters missing any requirement are:

- **Provisional NPCs** (partial support only), or  
- **Ambient NPCs** (minimal narrative load).

### 2. Template Version

Current required template version:

    Template-Version: 2.0

### 3. Validation Checklist

- [ ] Header complete  
- [ ] Template-Version present and correct  
- [ ] Required sections (0–10) exist  
- [ ] Attraction profile present  
- [ ] Relationship web complete  
- [ ] Narrative function defined  
- [ ] Scent/sound/texture lexicon exists  
- [ ] Integrity marker present  
- [ ] No content below marker  

---

## 7. END OF FILE

===============================
END ST-4
===============================