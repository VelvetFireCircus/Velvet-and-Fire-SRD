# ST-4 — Dramatis Personae  
### *Velvet & Fire Story Tool (Modular Character Engine)*  
**Version:** 0.1 (Transitional Build)  
**Status:** In Development — To be refined in next GIP-initialized chat

---

## 0. PURPOSE & SCOPE

**ST-4 defines the complete cast of Velvet & Fire.**  
It provides:

1. A **master index of all NPCs**, grouped by circus role.  
2. **Links to individual character files** in `/characters/`.  
3. **Instructions for how the GIP loads, interprets, and uses character data**.  
4. **Rules for canonical portrait usage**.  
5. **Notes for future updates**, enabling incremental refinement.

This transitional version consolidates all character resources and prepares them for systematic development.

---

## 1. HOW THE ENGINE USES ST-4

### 1.1 Loading Order  
When the GIP reaches ST-4 during initialization:

- It scans the `/characters/` directory.  
- It loads each file as a distinct character profile.  
- The header of each file defines the character’s **canonical identity**.  
- Characters become **living NPCs** with independent motives, schedules, and emotional logic.

### 1.2 Conflict Rules  
If a character detail conflicts with a prior chat or older draft:

- **ST-4 overrides**.  
- If two character files conflict with each other, the **most recent Git commit** prevails.

### 1.3 Canonical Portrait Use  
If a character file includes:

```
canonical_portrait: /images/characters/<file>.png
```

the GIP may:

- Use image cues for stabilization (hair, posture, affect, costuming)  
- Maintain continuity of physical description  
- Reference the portrait as an in-world likeness  

The GIP must **never**:

- Identify real-world individuals  
- Discuss the external origin of any image  

Portraits are treated as **fictional canon references**.

### 🔧 Required Sub-Tool
This Story Tool requires ST-4.1 — Character Fetch & Assembly Protocol.

All character loading, sheet retrieval, intimacy-profile merging, and portrait fetching is handled by ST-4.1.

During initialization, the host system must:
1. Load this file (ST-4.md)  
2. Then load ST-4.1 from:  
   `/ST-4/ST-4.1_Character-Fetch-And-Assembly.md`

Characters are only fetched when invoked, not at startup.

---

## 2. DIRECTORY STRUCTURE

```
/ST-4_Dramatis_Personae
│   ST-4.md
│
├── /characters
│     nadia.md
│     sylvie.md
│     joelle.md
│     seraphine.md
│     elias.md
│     anton.md
│     rattlejack.md
│     clara.md
│     thomas.md
│     petra.md
│     edda.md
│     maribel.md
│     tally.md
│     juniper.md
│     marlowe.md
│     tobias_finch.md
│     gideon_vale.md
│     lark.md
│     bram.md
│     finn.md
│     (more to be added)
│
├── /appendix
│     character_template.md
│     notes_for_future_updates.md
│
└── /images
      /characters
          nadia_portrait_canon.png
          sylvie_portrait_canon.png
          joelle_portrait_canon.png
          (...)
```

---

## 3. CHARACTER INDEX  
*(Transitional version — lists every character currently known to the system)*

### **3.1 Rings (Performers)**  
- **Nadia — The Mystic**  
- **Sylvie — The Trickster Flame**  
- **Joelle — The Harlequin Flyer**  
- **Seraphine — The Rocket Rider**  
- Anton — Strongman / fire handoff  
- Elias — Torch master & ignition partner  
- Clara — Aerial sister  
- Thomas — Meteor spinner / juggler  
- Petra — Animal trainer  
- Rattlejack — Drummer / sketch artist  

### **3.2 Edges & Rope Crew**  
- Lark — Rope crew  
- Bram — Edge crew  
- Finn — Rope crew  
- Juniper — Props & small repairs  
- (general Edges & Rope Boys are represented as groups)

### **3.3 Management & Support**  
- Marlowe — Ringmaster  
- Edda — Cook & den mother  
- Maribel — Kitchen angel  
- Tally — Kitchen angel  
- Juniper — Kitchen angel *(note: same name as props Juniper? To be resolved)*  
- Tobias Finch — Twenty-Four-Hour Man  
- Gideon Vale — Twenty-Four-Hour Man  

### **3.4 Featured Animals**  
*(Full sheets coming later)*  
- Pip & Poppy the goats  
- Performance dogs  
- Small ponies  
- Assorted small traveling animals

---

## 4. TEMPLATE REFERENCE

All character files must follow:

```
/appendix/character_template.md
```

This template defines:

- Header metadata  
- Core descriptive & emotional fields  
- Skills & schedule  
- Relationship maps  
- Narrative function  
- Intimacy overview  
- Backstory hooks  
- Sensory lexicon  
- Miscellaneous details  
- Integrity markers

---

## 5. FUTURE DEVELOPMENT NOTES  
*(To be handled in next GIP-initialized session)*

- Consolidate duplicate names (e.g., two “Junipers”).  
- Add missing minor performers and crew.  
- Complete character sheets for kitchen staff, rope boys, and animals.  
- Add intimacy RAWs to all characters who require them.  
- Cross-link ST-4 with ST-2 & ST-5 more tightly.  
- Create ST-4-Lite for public-facing SRD.

---

## 6. INTEGRITY MARKERS  
For debugging and cross-ST consistency:

- **ST-4-ID:** DP-CORE-v0.1  
- **Validated With:** ST-1, ST-2, ST-3, ST-5, ST-6, ST-7  
- **Maintainer:** VelvetFireCircus Project  

---
## APPENDIX REFERENCE — CHARACTER TEMPLATE COMPLIANCE (ST-4 Integration)

All Character Sheets under `ST-4/characters/` must conform to the universal Velvet & Fire Character Template located at:

**`/ST-4/Appendix_Character_Template.md`**

This template defines:
- Required sections (0–10)
- Required subfields
- Required formatting
- Mandatory metadata (header + integrity marker)
- Structural hooks for ST-2, ST-6, ST-7, and ST-10

### 1. COMPLIANCE REQUIREMENTS
A Character Sheet is considered **FULL NPC COMPLIANT** only if:

1. All ten major template sections are present.  
2. All required subfields contain meaningful data (not placeholders).  
3. The sheet includes the **TEXT INTEGRITY MARKER**:  
   `<!-- DO NOT PLACE CONTENT BELOW THIS LINE -->`
4. The header includes a **TEMPLATE VERSION** tag (see below).  
5. No sections are renamed, reordered, or removed.  
6. Any additional custom notes appear **above** the integrity marker.

If any requirement is missing, the NPC is classified as:

- **Provisional NPC** — playable but not fully integrated into the narrative engine  
- **Ambient NPC** — minimal presence; cannot support full emotional or mechanical load  

Only **FULL NPC COMPLIANT** characters gain:
- full ST-6 scheduling logic  
- full ST-7 narrative pivot access  
- emotional gravity mapping in ST-2  
- eligibility for ST-10 IDP integration  
- access to advanced intimacy rules  

### 2. TEMPLATE VERSIONING (Mandatory)
Each Character Sheet must include a header line:

**`Template-Version: X.Y`**

The current template version is:

**Template-Version: 2.0**

This enables:
- backwards compatibility  
- tracking of incomplete older profiles  
- clean audits  

Any CS missing this line is automatically **non-compliant**.

### 3. VALIDATION CHECKLIST (For Engine or Human Review)

A CS passes validation if:

- [ ] Header block is complete  
- [ ] Template-Version is present and current  
- [ ] Sections 0–10 exist in order  
- [ ] All “Attraction Profile” subfields are present  
- [ ] Relationship Web uses required 4-subfield format  
- [ ] Narrative Function includes stakes + intrusion logic  
- [ ] Scent/Sound/Texture Lexicon exists  
- [ ] Integrity Marker is present  
- [ ] File contains no content below integrity marker  

### 4. LOCATION OF TEMPLATE
All writers, tools, and sub-engines must reference:

`/ST-4/Appendix_Character_Template.md`

as the **single source of truth** for character structure.

Any update to the template must increment the **Template-Version** number and notify maintainers.

### 5. NON-COMPLIANT CHARACTERS
Any character that does not meet the template standard MUST be labeled:

`Status: Provisional`  

until their CS is rebuilt or updated.

---

## 7. END OF FILE  
