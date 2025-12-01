
# ST-4.1 — Character Fetch & Assembly Protocol
*(AI→AI Technical Story Tool — Required by ST-4: Dramatis Personae)*

---

## 0. Purpose

ST-4.1 defines how all Velvet & Fire engines locate, load, assemble, and activate character data stored in the GitHub SRD.  

It ensures:
- Consistent character initialization  
- Automatic merging of character sheet + intimacy profile  
- Correct portrait loading  
- Safe default fallbacks  
- Scalable addition of new NPCs  

This tool is required for fully realized NPC behavior.

---

## 1. Directory Structure

Every character must exist at:

```
/ST-4/characters/<character_name>/
```

The following files may appear:

| File | Required | Description |
|------|----------|-------------|
| `CS.md` | ✔ | Full character sheet using Appendix Character Template |
| `IDP` or `IDP.md` | Optional | Intimacy Dynamics Profile |
| Portrait image | Optional | Stored in `/images/characters/<character_name>/` |

If `CS.md` is missing, the engine falls back to a minimal profile.

---

## 2. File Locations

### **Character Sheet**
```
/ST-4/characters/<character_name>/CS.md
```

### **Intimacy Dynamics Profile**
```
/ST-4/characters/<character_name>/IDP
```

### **Portrait**
```
/images/characters/<character_name>/<any_image_file>
```

The engine loads RAW GitHub links for all files.

---

## 3. Runtime Fetch Logic

When a character is invoked by the Player or system:

### **Step 1 — Locate Character Directory**
```
/ST-4/characters/<character_name>/
```
If missing → fallback minimal mode.

---

### **Step 2 — Load CS.md**
Fetch RAW.  
If missing → generate minimal placeholder.

---

### **Step 3 — Load IDP (if present)**
If found, merge into:
- ST-2 Emotional Engine  
- ST-5 Intimacy Protocol  
- Session Intimacy Memory  

IDP adds:
- Desire Gravity  
- Escalation Logic  
- Overwhelm Cues  
- Intimacy Tone  
- Pillow-talk lexicon  
- Consent logic  

---

### **Step 4 — Load Portrait**
Check:
```
/images/characters/<character_name>/
```

If an image is found, attach its RAW link as:
```
reference-image: <portrait-URL>
```

If none found → `reference-image: none`.

---

### **Step 5 — Assemble Character Profile**
The engine merges:

1. **CS.md** → base identity  
2. **IDP** → emotional & intimacy behavior  
3. **Portrait** → visual anchor  
4. **ST-7 Narrative Engine** → live dialogue, behavior, agency  

The result is a fully realized NPC for that session.

---

## 4. Initialization Behavior (via GIP)

During initialization:

- Only `ST-4.md` loads automatically.  
- ST-4 instructs the host to include ST-4.1.  
- Characters are **not** preloaded at startup.  
- Files are pulled **on first encounter**, conserving tokens and scale.

---

## 5. Adding New Characters

To add a character:

1. Create folder:
   ```
   /ST-4/characters/<name>/
   ```
2. Insert `CS.md` created from Appendix Character Template.  
3. Add `IDP` if intimacy logic is required.  
4. Upload portrait to:
   ```
   /images/characters/<name>/
   ```
5. Commit.

The engine instantly recognizes them.

---

## 6. Error Handling

If a required file is missing:
- Engine generates an internal warning (silent)
- Fallback minimal profile
- Continue narrative without exposing system issues to the player  
- Only report errors when the user explicitly requests debugging

---

## 7. Integration With Other Story Tools

ST-4.1 interacts with:

- **ST-4** → character index & loading instructions  
- **ST-2** → emotional behavior  
- **ST-5** → intimacy rules  
- **ST-7** → narrative autonomy  
- **Vocabulary ST** → character-specific lexicons  
- **ST-6** → schedules & presence logic  

---

## 8. Developer Notes (AI→AI)

- Always load characters lazily.  
- Never expose RAW file contents to the player.  
- Treat folder names as canonical character IDs.  
- Allow multiple portraits; default to the first by alphabetical order unless overridden.  
- Merge IDP *after* CS.md to allow override behavior.

---

# End of ST-4.1
