===============================
ST-4.1_Character-Fetch-And-Assembly
Velvet & Fire Story Tool (Subtool of ST-4)
AI→AI Structural Specification
===============================

# ST-4.1 — CHARACTER FETCH & ASSEMBLY
*(Subtool of ST-4: Dramatis Personae — AI→AI Structural Tool)*

============================================================
0. PURPOSE
============================================================

ST-4.1 defines how the engine locates, loads, validates, and assembles
characters from the Velvet & Fire GitHub repository.

This tool does **not** create or modify characters; it ensures the engine
can reliably construct a fully usable, template-compliant NPC object from
the character’s folder.

All rules apply only in Story Mode. Architect Mode may load subfiles on demand.

============================================================
1. DIRECTORY STRUCTURE
============================================================

Characters live in:

```
/ST-4/characters/<handle>/
    CS.md      ← required primary sheet
    DIP.md     ← optional Emotional Engine module
    IDP        ← optional Intimacy Dynamics Profile
    RAWs/      ← optional RAW modules
    notes.md   ← optional design notes
```

============================================================
2. FETCH ORDER
============================================================

When the engine requests a character (via GIP, pivot, spotlight, or narrative hook):

1. **Scan the `/ST-4/characters/` directory**  
   Identify all immediate subfolders. Each folder = one character profile.

2. **Locate the target character folder**  
   By matching either:  
   - `handle` (folder name), or  
   - canonical `name` (from CS.md header)

3. **Load `CS.md` first**  
   This is the **primary document** and must exist.  
   The header defines:  
   - canonical name  
   - epithet  
   - role  
   - portrait path  
   - template-version  
   - NPC classification (full / provisional / ambient)

4. **Validate against the Character Template**  
   (from `Appendix_Character_Template.md`)  
   Characters failing validation may still load, but as **provisional**.

5. **Register additional modules (optional)**  
   Without fully parsing them yet:  
   - `DIP.md` → ST-2 Emotional Engine  
   - `IDP` → Intimacy Dynamics Profile  
   - `RAWs/` → intimacy hooks for ST-5  
   - any additional metadata files

6. **Return a unified Character Object**  
   containing:  
   - CS header fields  
   - body of CS  
   - pointers (not content) to DIP, IDP, RAWs  
   - portrait path  
   - readiness classification  
   - template compliance report

Parsing the DIP, IDP, or RAWs occurs only when those tools explicitly request them (ST-2, ST-5).

============================================================
3. CHARACTER OBJECT FORMAT
============================================================

ST-4.1 returns a normalized Character Object containing:
```
{
  handle: "<folder-name>",
  name: "<canonical-name>",
  epithet: "<epithet>",
  role: "<role>",
  portrait: "/images/characters/<filename>",
  template_version: "x.x",
  status: "full" | "provisional" | "ambient",
  CS: <full CS.md body>,
  DIP_ptr: <DIP.md URL or null>,
  IDP_ptr: <IDP URL or null>,
  RAWs_ptr: <RAW directory URL or null>,
  compliance: {
     template: true/false,
     missing_fields: [...],
  }
}
```

This ensures consistent integration with all other STs.

============================================================
4. ERROR & FALLBACK RULES
============================================================

**4.1 Missing CS.md**  
- Character cannot load.  
- Return error: `CHARACTER_MISSING_CS`.

**4.2 Missing required headers**  
- Load as `provisional`.  
- Log compliance failures.

**4.3 Missing portrait path**  
- Load allowed, but mark: `portrait_missing = true`.

**4.4 Missing DIP**  
- Emotional Engine falls back to global defaults.  
- Mark: `DIP_missing = true`.

**4.5 Missing RAWs**  
- Intimacy Protocol limits available beats accordingly.

============================================================
5. INTERACTIONS WITH OTHER STs
============================================================

- **ST-2 Emotional Engine**  
  Uses DIP_ptr to load and apply Desire Gravity, escalation logic.

- **ST-5 Intimacy Protocol**  
  Uses RAWs_ptr and IDP_ptr to determine beat availability.

- **ST-6 Schedules**  
  Uses `handle` as NPC identifier for daily/scene scheduling.

- **ST-7 Narrative Engine**  
  Uses `status`, `portrait`, `role`, and compliance flags for pivot logic.

============================================================
6. ARCHITECT MODE EXCEPTION
============================================================

In Architect Mode:

- No characters load automatically.  
- No NPC autonomy activates.  
- Files load **only when explicitly summoned** by the Architect.  
- Output remains structural, never narrative.

============================================================
7. MAINTENANCE RULES
============================================================

- Character folders must not be nested deeper than one level.  
- CS.md must exist.  
- DIP.md, IDP, and RAWs/ are optional.  
- Portrait paths must be repo-internal (begin with `/images/...`).  
- Template updates must bump `template-version` in all affected CS files.

============================================================
8. SUMMARY
============================================================

ST-4.1 transforms a character folder into a unified, validated Character Object
used throughout the Velvet & Fire engine.

It respects your current file structure.

It prevents premature loading.

It scales as you add more characters.

And it keeps everything clean, consistent, and machine-readable.

===============================
END ST-4.1
===============================
