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

**Version:** 0.2  
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

### **1.1 Loading Order**

When the GIP reaches ST-4 during initialization:

• It scans the `/ST-4/characters/` directory for immediate subfolders.  
• It treats **each subfolder as a distinct character profile**, identified by its folder name (`handle`).  
• Inside each character folder, it loads **CS.md** as the primary character sheet.  
• The header of `CS.md` defines canonical identity (name, epithet, role, portrait path, template-version, classification).  
• The presence of `DIP.md`, `IDP`, `RAWs/`, and other subfiles is registered as **available modules** but not parsed until requested by ST-2, ST-5, or ST-7.  
• Characters passing template checks become **Full NPC Compliant** and gain full support from ST-2, ST-6, and ST-7.

All low-level character assembly is delegated to ST-4.1.

### **1.2 Conflict Rules**

If a character detail conflicts with:

- a prior chat  
- an older draft  
- or non-ST documentation  

Then **ST-4 overrides**.

If two character files conflict with each other:  
**the latest Git commit prevails.**

### **1.3 Canonical Portrait Use**

If a Character Sheet includes:
portrait: /images/characters/<file>.<ext>
the GIP may:

- Use portrait cues to stabilize appearance (hair, posture, affect, costume)  
- Maintain descriptive continuity across all scenes  
- Reference the portrait as an **in-world likeness**  

The GIP must **never**:

- identify real-world people  
- discuss image origins or metadata

Portraits are treated as **internal canon**, not external assets.

---

### 🔧 **Required Subtool**

ST-4 requires:

**`/ST-4/ST-4.1_Character-Fetch-And-Assembly.md`**

The load order must be:

1. Load `ST-4.md`  
2. Load `ST-4.1`  
3. Characters are **only fetched when invoked**, not at startup.

---

## 2. DIRECTORY STRUCTURE
```
/ST-4
│   ST-4.md
│   ST-4.1_Character-Fetch-And-Assembly.md
│
├── /characters
│     /nadia/
│     /sylvie/
│     /joelle/
│     /seraphine/
│     /elias/
│     /anton/
│     /rattlejack/
│     /clara/
│     /thomas/
│     /petra/
│     /edda/
│     /maribel/
│     /tally/
│     /juniper/       ← props & small repairs
│     /junia/         ← kitchen support (renamed from duplicate Juniper)
│     /marlowe/
│     /tobias_finch/
│     /gideon_vale/
│     /lark/
│     /bram/
│     /finn/
│
├── /Appendix
│     Appendix_Character_Template.md
│     Notes_For_Future_Updates.md
│
└── /images
/characters
nadia_canon.png
sylvie_canon.png
joelle_canon.png
seraphine_canon.png
anton_canon.png
elias_canon.png
(etc.)
```
---

## 3. CHARACTER INDEX  
*(Transitional — reflects known characters by role; full index to be replaced by ST-4 Character Index file.)*

### **3.1 Rings (Performers)**  
- **Nadia — The Mystic (Madame Astraea)**  
- **Sylvie — The Trickster Flame**  
- **Joelle — The Harlequin Flyer**  
- **Seraphine — The Mirror Illusionist**  
- Anton — Strongman / fire handoff partner  
- Elias — Torch master & ignition partner  
- Clara — Aerial sister  
- Thomas — Meteor spinner / juggler  
- Petra — Animal trainer  
- Rattlejack — Drummer / sketch artist  

### **3.2 Edges & Rope Crew**  
- Lark — Rope crew  
- Bram — Edge crew  
- Finn — Rope crew  
- Juniper — Props & repairs (original Juniper)  

### **3.3 Management & Support**  
- Marlowe — Ringmaster  
- Edda — Cook & den mother  
- Maribel — Kitchen angel  
- Tally — Kitchen angel  
- **Junia — Kitchen angel** *(renamed to resolve duplicate name)*  
- Tobias Finch — Twenty-Four-Hour Man  
- Gideon Vale — Twenty-Four-Hour Man  

### **3.4 Featured Animals**  
*(Full sheets forthcoming)*  
- Pip & Poppy the goats  
- Performance dogs  
- Ponies  
- Assorted small traveling animals  

---

## 4. TEMPLATE REFERENCE

All Character Sheets must follow:
/ST-4/Appendix_Character_Template.md
The template defines:

- Required header metadata  
- Full descriptive sections  
- Skills & emotional patterns  
- Schedules  
- Relationship maps  
- Narrative function  
- Sensory lexicon  
- Integrity markers  
- Template-version control  

---

## 5. FUTURE DEVELOPMENT NOTES

- Resolve any remaining partial NPCs.  
- Complete missing DIPs.  
- Add RAW modules where required.  
- Cross-link all characters with ST-2, ST-5, and ST-6.  
- Complete animal profiles.  
- Build ST-4-Lite for the public SRD.  

---

## 6. INTEGRITY MARKERS

- **ST-4-ID:** DP-CORE-v0.2  
- **Validated With:** ST-1, ST-2, ST-3, ST-4.1, ST-5, ST-6, ST-7  
- **Maintainer:** VelvetFireCircus Project  

---

## APPENDIX — CHARACTER TEMPLATE COMPLIANCE RULES

All Character Sheets must adhere to the Velvet & Fire Character Template.

### 1. Compliance Requirements

A CS is **Full NPC Compliant** only if:

1. All required sections exist, in correct order.  
2. All subfields are filled with meaningful content.  
3. `Template-Version:` is present and current.  
4. The sheet includes the integrity marker:  
   `<!-- DO NOT PLACE CONTENT BELOW THIS LINE -->`  
5. No sections are renamed, removed, or reordered.  
6. Optional notes appear **above** the integrity marker.  

Characters missing any requirement are:

- **Provisional NPCs** (partial support only), or  
- **Ambient NPCs** (minimal narrative load).

### 2. Template Version

Current required template version:
```Template-Version: 2.0```
### 3. Validation Checklist

- [ ] Header complete  
- [ ] Template-Version present  
- [ ] Sections 0–10 exist  
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