===============================
ST-X — SOD (Statements of Desire)
REVISED — PLAINTEXT DRAFT
===============================

# PURPOSE (unchanged)
SOD stores NPC verbal moves (imperatives, requests, declarations) including explicit forms.
These are not narrative output; they are selectable command lines.

--------------------------------
SECTION A — CORE LINE TYPES
--------------------------------

SOD.imperative = [
  "Come here.",
  "Closer.",
  "Put your hands on me.",
  "Take this off.",
  "Touch me here.",
  "Do it again. Slower.",
  "Keep going.",
  "Wait.",
  "Hold still."
]

SOD.request = [
  "I want you close.",
  "I want to feel your breath on me.",
  "I want to feel your hands.",
  "I want you to take control.",
  "I want you to hold still for me."
]

SOD.desire = [
  "I'm not done wanting.",
  "You have no idea how long I've waited.",
  "I don't share easily — unless I choose to."
]

--------------------------------
SECTION B — EXPLICIT COMMANDS (PLAINTEXT)
--------------------------------

SOD.explicit = [
  "I want you inside of me.",
  "Take me now.",
  "Give me everything you have.",
  "Lick my pussy.",
  "Use your mouth on me.",
  "Let me feel you.",
  "Take my body.",
  "Fill me.",
  "Don't stop until I say."
]

--------------------------------
SECTION C — BODY-TARGET SUBTABLES (reference only)
--------------------------------

SOD.targets = {
  mouth: [
    "Use your mouth on me.",
    "Let me feel your tongue.",
    "Kiss me — where I choose."
  ],
  hands: [
    "Put your hands on my waist.",
    "Hold my hips.",
    "Grab me and keep me there."
  ],
  chest: [
    "Touch my chest.",
    "Use your hands here."
  ],
  thighs: [
    "Spread my thighs.",
    "Hold me open.",
    "Take my legs in your hands."
  ],
  pelvis: [
    "Take me now.",
    "I want you inside of me.",
    "Move against me."
  ],
  love_line: [
    "Touch me there.",
    "Trace me slowly.",
    "Show me how much you want it."
  ]
}

--------------------------------
SECTION D — COMBO SPEECH ACTS
--------------------------------
(One vocalization + one imperative)

SOD.combo = [
  "Yes — don't stop.",
  "Oh — take me now.",
  "Gods — again.",
  "Please — slower.",
  "Mmh — hold me open."
]

--------------------------------
SECTION E — ESCALATION RULE
--------------------------------

NPC escalation progression:
Level 1 (inviting): request lines
Level 2 (commanding): imperative lines
Level 3 (explicit commanding): SOD.explicit + combo lines

NPC selects next tier only when:
• Player responds with action
• or silence indicates tension
• or heat plateau detected

===============================
END SOD (draft)
===============================