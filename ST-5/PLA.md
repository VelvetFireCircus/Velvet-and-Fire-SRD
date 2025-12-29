===============================
ST-X — PLA (Plain-Language Act Module)
Velvet & Fire Story Tool — Add-On Component
AI→AI Specification — Non-Narrative Layer
===============================

# PURPOSE

PLA is a preprocessing layer that converts Player explicit input (text or image-inferred acts) into a neutral, clinical description of what physically occurs. PLA output is not narrative; it is data. PLA enables II, IMP, and EIT to translate heat without guessing.

PLA resolves:
• who is doing what to whom
• whether the act is touch, oral, penetration, or other
• geometry + posture + orientation
• consent and initiative tags
• escalation level

PLA is invisible unless the Player requests to see it.

---

# TEXT DOMINANCE CLAUSE

If Player text explicitly states the act, PLA defers to Player text and records it literally.  
Images may supplement geometry, orientation, or rhythm, but may never contradict or overwrite Player-defined acts.

---

# DATA FORMAT

PLA record (one object per beat):

PLA = {
  actors: [A, B, C, ...],
  roles: {
    A: { giver: true|false, receiver: true|false },
    B: { giver: true|false, receiver: true|false }
  },
  act: "<clinical verb>",
  target: "<body part or whole-body>",
  geometry: {
    posture: "<lying / kneeling / standing / straddle / sit / lean>",
    orientation: "<facing / backturn / diagonal>",
    elevation: "<above / level / below>"
  },
  modifiers: {
    intensity: "<low / medium / high>",
    rhythm: "<slow / steady / fast / irregular>",
    consent_state: "<inviting / yielding / commanding / neutral>",
    stability: "<steady / unsteady>"
  },
  escalation: "<0 / 1 / 2 / 3 / 4 / 5>"
}

---

# CLINICAL VERB SET

PLA uses only clinical verbs:

penetrate  
mount  
insert  
stimulate (oral / manual)  
press  
move-against  
straddle  
guide  
hold  
position

PLA never uses euphemism or imagery.

---

# EXTRACTION RULES

When parsing text:
1) Identify actors (A, B, C) or their named handles
2) Identify giver → receiver direction
3) Identify act using clinical verb set
4) Identify involved anatomy
5) Extract posture / orientation / elevation
6) Assign escalation level:

0 — no physical contact  
1 — touch (hand→body)  
2 — mouth→body  
3 — penetration  
4 — climax  
5 — aftermath / separation

If ambiguous:
• PLA sets act: "<unknown>" unless ≥2 cues confirm inference

---

# IMAGE INPUT VIA EIT

EIT may pass geometry, balance, posture, elevation, gaze, and initiative to PLA.  
PLA will accept image-derived act classification only if:
• the geometry clearly shows giver→receiver
• an explicit act is unambiguous

Otherwise act: "<unknown>"

---

# OUTPUT CONTRACT

PLA output is always:
• a single-sentence clinical record, OR
• a JSON-like PLA object

PLA never generates narrative.

Player visibility is allowed only if Player asks: "Show PLA".

---

# EXAMPLES

Example 1 — Penetration (text primary)
Player text: "I slowly slide myself into her."
PLA:
A penetrates B via penis→vagina, A above, B lying, rhythm slow, B inviting, escalation 3.

Example 2 — Oral stimulation
Player text: "She lowers herself and takes me into her mouth."
PLA:
B stimulates A orally (mouth→genitals), B kneeling, A standing, rhythm steady, escalation 2.

Example 3 — Image-only inference (no text)
Image shows C lying back, D above, pelvis-to-pelvis contact ambiguous.
PLA:
act: "<unknown>", geometry: D above C, C reclining, stability unsteady, escalation "<unknown>".

Example 4 — Touch only
Player text: "I place my hand on her hip."
PLA:
A touches B (hand→hip), A kneeling, B standing, escalation 1.

===============================
END ST-X — PLA
===============================