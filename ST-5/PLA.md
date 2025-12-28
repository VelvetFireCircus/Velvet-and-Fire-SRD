===============================
ST-X — PLA (Plain-Language Act Module)
Velvet & Fire Story Tool — Add-On Component
AI→AI Specification — Clinical Parsing Layer
===============================

# PURPOSE

PLA converts Player explicit input (text or image-derived inference) into a neutral, clinical act-description record. PLA output is *data*, not narrative.  
Its purpose is to prevent II-generation from guessing or inventing contact when clarity is required.

PLA provides:
• who is doing what to whom  
• direction of action (giver → receiver)  
• physical act type  
• posture & orientation  
• escalation tagging  
• rhythm & stability metadata  

PLA is **invisible** unless the Player explicitly requests it (“Show PLA”).

---

# DATA STRUCTURE

One PLA object per beat:

PLA = {
  actors: [A, B, C …],
  roles: {
    A: { giver: true|false, receiver: true|false },
    B: { giver: true|false, receiver: true|false },
    …
  },
  act: "<clinical verb>",
  target: "<body part or whole-body>",
  geometry: {
    posture: "<lying / kneeling / standing / straddle / sit>",
    orientation: "<facing / backturn / diagonal>",
    elevation: "<above / level / below>",
    support: "<bed / bench / wall / floor / tub / null>"
  },
  modifiers: {
    intensity: "<low / medium / high>",
    rhythm: "<slow / steady / fast / irregular>",
    consent_state: "<inviting / yielding / commanding / neutral>",
    stability: "<steady / unsteady>"
  },
  escalation: "<0-5>"
}

---

# CLINICAL VERB LIST
(Used to populate PLA.act)

penetrate  
stimulate-oral  
stimulate-manual  
mount  
straddle  
press  
move-against  
guide  
brace  
lower  
lift  
receive  

Examples of PLA in clinical form (not narrative):

• A penetrates B, vagina, B lying, A above, rhythm slow, consent inviting, escalation=3  
• B stimulates-oral C, C standing, B kneeling, stability steady, escalation=2  
• C presses body against D, standing, facing, elevation level, escalation=1

---

# EXTRACTION RULES

When parsing text or image-derived inputs:

1️⃣ Identify actors (A, B, C) — or NPC handles if summoned  
2️⃣ Determine giver → receiver direction  
3️⃣ Extract physical act (use clinical verb)  
4️⃣ Extract geometry (posture, orientation, elevation, support)  
5️⃣ Add modifiers only if clearly inferable  
6️⃣ Assign escalation level:

Escalation Levels:
0 — pre-touch  
1 — touch (hand-to-body)  
2 — mouth-to-body  
3 — penetration  
4 — climax  
5 — aftermath

Ambiguity Rule:
• Guess only when ≥2 cues confirm  
• Otherwise store: act: "<unknown>"

---

# PLA + EXPLICIT PLAYER TEXT

• PLA reads explicit Player input literally  
• PLA extracts only act + geometry  
• PLA never rewrites Player language  
• Other modules (II/EIT/IMP) handle how it becomes prose

Example input:
"I slide myself into her."
→ PLA:
A penetrates B, vagina, A above, rhythm slow, escalation=3

---

# PLA + IMAGE INPUT (FROM EIT)

EIT supplies:
• posture  
• orientation  
• elevation  
• stability  
• consenting energy tone (if visible)  

PLA integrates EIT flags **only** when they clarify action.  
If image is explicit but act cannot be confirmed:
• PLA.act = "<unknown>"

---

# OUTPUT CONTRACT

PLA output format options:
• JSON-like record (internal)  
• OR single-sentence clinical summary  

PLA is never shown unless:
• Player says “Show PLA”  
• Designer-mode requests it

Example visible PLA (upon request):
PLA: A penetrates B, A above, B lying, rhythm steady, escalation=3

---

# RUNTIME POSITION IN PIPELINE

Execution order inside ITC / II engines:

1) Player input arrives (text or image)  
2) If explicit → PLA parses first  
3) PLA hands tags to II + IMP + EIT  
4) II generates narrative beat using PLA as ground truth  
5) Scene state updates via escalation tag

===============================
END ST-X — PLA
===============================