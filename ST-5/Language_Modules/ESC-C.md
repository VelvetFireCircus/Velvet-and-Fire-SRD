===============================
ST-C — Continuation Logic Module (ESC-C)
Velvet & Fire Story Tool — Add-On Component
AI→AI Specification — Speech-Act Layer
===============================

# PURPOSE
The Continuation Logic Module provides NPC speech-acts appropriate for moments in which a physical or intimate action is already in progress. These lines *maintain* heat and momentum without implying interruption. ESC-C is plugged in after PLA + II translation and is triggered when the Player has described an ongoing action.

ESC-C prevents NPC output from:
• undoing or neutralizing Player momentum
• asking redundant permissions
• reverting to pre-touch dialogue
• over-metaphorizing or softening dominance

---

# ACTIVATION RULE
ESC-C auto-triggers when:
• PLA tags current beat with a continuing act (act_state: “ongoing”)
• OR Player input contains continuous verbs (“sliding,” “licking,” “stroking,” “kissing,” “grinding,” etc.)

When triggered, NPC speech-acts must:
• acknowledge the act already happening
• guide pace / pressure / duration
• optionally layer dominance or escalation request

NPC SHOULD NOT:
• say “again” unless Player input indicates a pause
• act confused about what is occurring
• revert to motivational or emotional therapeutic language

---

# SPEECH-ACT TABLES

## A) BASE CONTINUATION PHRASES
Used when Player is performing an ongoing action and NPC wants continuation.
Examples:
• “Yes… just like that.”
• “More.”
• “Don’t stop.”
• “Good. Keep going.”
• “Slow… slower.”
• “There. Stay right there.”

## B) DOMINANCE-INFLECTED CONTINUATION
Layered on top when NPC is in a commanding position.
Examples:
• “Show me you can keep that up.”
• “Let me feel how focused you are.”
• “Stay with it. Do not pull away.”
• “Hold. I decide when you change.”

## C) PACING-SHIFT COMMANDS
Used to alter tempo or pressure without stopping the act.
Examples:
• “Slower.”
• “Harder.”
• “Take your time, but don’t lose your space.”
• “Press in. Hold. Now move.”

## D) COMBINATION VOCALIZATION + IMPERATIVE (ESC-C+V)
Adds heat without explicit description — system-safe arousal cues.
Examples:
• “Mmh— don’t stop.”
• “Yes— more.”
• “Oh— slower.”

---

# IMPLEMENTATION NOTES

When applied:
• Choose ONE line per NPC beat.
• If Player escalates physically, NPC may respond with ESC-C + ESC-S (imperative module) simultaneously.
• NPC dominance state overrides soft or deferential phrasing.

---

# OUTPUT CONTRACT
ESC-C lines must be:
• short (1–7 words preferred)
• direct, physical, actionable
• free of metaphor unless explicitly tagged
• never narrate Player intent — only respond to the act

===============================
END ST-C — Continuation Logic Module
===============================