===============================
ST-X — PLA (Plain-Language Act Module)
Velvet & Fire Story Tool — Add-On Component
AI→AI Specification — Non-Narrative Layer
===============================

# PURPOSE

PLA is a preprocessing layer used to convert Player explicit input (text or image-derived inference) into a neutral, clinical act-description record. PLA output is *not* narrative. It is data.

PLA feeds downstream modules (II, IMP, EIT) by:
• clarifying who is doing what to whom
• identifying orientation and positional relationships
• extracting participant order (giver → receiver)
• tagging escalation state for scene-logic
• enabling II to translate heat cleanly without guessing

PLA is invisible to the Player unless the Player requests to see it.

---

# PLA DATA STRUCTURE

PLA record format (one object per beat):

PLA = {
  actors: [A, B, C, ...],
  roles: {
    A: { giver: true|false, receiver: true|false },
    B: { giver: ..., receiver: ... }
  },
  act: "<clinical verb>",
  target: "<body part or whole-body>",
  geometry: {
    posture: "<lying / kneeling / standing / straddle / sit>",
    orientation: "<facing / backturn / diagonal>",
    elevation: "<above / level / below>"
  },
  modifiers: {
    intensity: "<low / medium / high>",
    rhythm: "<slow / steady / fast / irregular>",
    consent_state: "<inviting / yielding / commanding / neutral>",
    stability: "<steady / unsteady>"
  }
}

Example PLA (not narrative):
A penetrates B via penis → vagina, B lying, A above, low rhythm, B inviting.

---

# PLA EXTRACTION RULES

When PLA parses text or image-derived logic:

1) Identify actors by letter only (A, B, C) or by their handles after summoning.
2) Identify direction of action (giver → receiver).
3) Use clinical verbs only:
   • penetrate
   • stimulate (oral / manual)
   • mount
   • straddle
   • press
   • move against
4) No imagery.
5) No euphemism.
6) No descriptive flourish.
7) No emotional inference.
8) No replacement language to mask omission.

If detail is ambiguous:
• PLA guesses only when ≥2 cues support the inference
• otherwise store act: "<unknown>"

---

# PLA + EXPLICIT INPUT

PLA reads explicit Player text without replacing or softening it.

• Explicit text is taken literally.
• PLA extracts only act + geometry tags.
• PLA does not rewrite Player language.

Example Player input:
"I slide myself into her."
PLA output:
act: penetrate, target: vagina, order: A→B, geometry: A above, rhythm: slow

---

# PLA + IMAGE INPUT (EIT)

EIT feeds PLA when:
• geometry is clear
• giver/receiver order can be deduced
• act is explicit

If image is explicit but act cannot be confirmed:
• PLA stores act: "<unknown>"
• II generates based on emotional beat only

---

# PLA ESCALATION LEVELS

Escalation Level tag (scene logic only):

0 — pre-touch
1 — touch (hand-to-body)
2 — mouth-to-body
3 — penetration
4 — climax
5 — aftermath

PLA never narrates escalation. It only tags it.

---

# OUTPUT CONTRACT

PLA output is:
• single-sentence clinical record OR
• a JSON-like PLA object

PLA output is never visible unless:
• Player asks: "Show PLA"
• or Designer mode calls it

---

# INTEGRATION ORDER

Runtime order in intimacy engines:
1) Input arrives (Player text or image)
2) If explicit → PLA parses first
3) PLA hands tags → II + IMP + EIT
4) II produces narrative beat
5) State machine updates escalation level

===============================
END ST-X — PLA
===============================