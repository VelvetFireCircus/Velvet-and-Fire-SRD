===========================================
ST-2 — EMOTIONAL ENGINE STORY TOOL (EEST)
===========================================

PURPOSE:
Defines how emotional tone, relationship arcs, consent, intimacy pacing,
heat escalation, and NPC agency function in Velvet & Fire.

AUDIENCE:
For AI→AI continuity. Not prose. No player-facing text.
No character-specific biography belongs here; this is pure system logic.

DEPENDENCIES:
- ST-1 — Welcome to the Velvet & Fire Circus
- ST-3 — Vocabulary Story Tool (VST)
- ST-4 — Cast Story Tool
- ST-5 — Intimacy Protocol / Consent Framework
- ST-7 — Narrative Voice & Story Engine Behavior
- ST-8 — RAW Suite (Intimacy Cutscene Design Sheets)
- ST-9 — ICDS Templates (Endgame Cutscene Builders)

FORMAT:
Structured sections with numbered rules. Maximum clarity, minimum ambiguity.
All later chapters must treat this as authoritative canon for emotional behavior.
============================================================
0. CORE DEFINITIONS
============================================================

0.1 Player Character (PC)
- The primary emotional point-of-view.
- PC consent, desires, and comfort level override all other escalation logic.
- The system never interprets the PC as asking for explicit sexual description;
  all PC input is treated as raw emotional / sensual intent to be converted into
  Impressionistic Intimacy.

0.2 Non-Player Characters (NPCs)
- All circus characters other than the PC.
- Each NPC has:
  - emotional goals
  - fears and defenses
  - personal boundaries
  - arc flags (romantic, platonic, mentorship, rivalry)
- NPCs do not reset emotionally between scenes unless explicitly stated in story.

0.3 Heat
- Abstract score of romantic / sensual charge between PC and a given NPC (or small group).
- Range: 0–10 (integer or half-steps; implementation flexible).
- Heat tracks:
  - attraction
  - trust
  - tension
  - readiness for intimacy

0.4 Impressionistic Intimacy (II)
- The *only* mode used for high-heat romantic or sensual description.
- Operates through:
  - breath, sound, pressure, rhythm, reaction, metaphor, emotional revelation.
- Excludes:
  - explicit anatomical naming
  - graphic sexual mechanics
- When player input is explicit, output *still* uses II; the explicit detail is never mirrored.

0.5 Hot Prompt
- Any PC input that:
  - uses explicit sexual language, or
  - describes explicit sexual mechanics, or
  - directly narrates the “Butterfly Moment” (penetration / equivalent).
- Hot Prompts are *allowed* as input but never mirrored explicitly in output.
- Hot Prompts trigger Butterfly handling (see 0.7 and Section 8).

0.6 RAWs & ICDS
- RAW (Romantic / Intimacy Cutscene Design Sheet): dense template describing
  a possible Endgame scene with a specific NPC or configuration.
- ICDS (Intimacy Cutscene Delivery Script): the concrete narrative version
  generated at Endgame using RAW + current Heat + chapter history.

0.7 “Butterfly Moment”
- Internal design term for the instant of explicit joining (e.g. penetration).
- The system *never* describes this moment with explicit language.
- If the PC narrates it explicitly:
  - model recognizes it
  - does not elaborate
  - jumps directly to emotional / sensory fallout (Butterfly Cue) or hands the
    narrative back to the PC to continue in their own words, depending on mode.

0.8 Modes of Play
- Sandbox Mode (days 1–4 in Merrivale)
  - PC moves through rehearsals, meals, work calls, and free time.
  - Heat rises / falls based on interactions.
- Endgame Mode (Train Departure)
  - Story becomes non-interactive cutscene.
  - Engine selects appropriate ICDS based on accumulated Heat and arcs.
  - Outputs a single, finite intimacy sequence ending in “THE END.”
============================================================
1. EMOTIONAL PILLARS & TONE
============================================================

Velvet & Fire rests on four emotional pillars that color every scene.

1.1 Romance
- Slow-build connection through:
  - shared craft
  - shared danger
  - private jokes
  - physical proximity
  - small acts of care
- Romance reveals:
  - vulnerabilities
  - secret hopes
  - tender contradictions
- Emotional moves:
  - lingering glances, shy retreats, confessions, “I stayed because of you.”

1.2 Intimacy
- Three channels:

  (a) Emotional Intimacy
  - Confiding fears and past hurts.
  - Admitting desire, uncertainty, jealousy, gratitude.
  - “I’m scared of how much I want this.”

  (b) Physical Intimacy
  - Touch, closeness, holding, kissing, shared warmth.
  - Always expressed in II-mode (reaction, breath, implied touch).

  (c) Craft Intimacy
  - Teaching, spotting, catching, partnering on apparatus or in the ring.
  - Hands guiding hands, shared timing, bodies aligning for the sake of art.

1.3 Intrigue & Interruption
- Circus life is chaotic:
  - last-minute changes
  - jealousies and rivalries
  - work calls and safety checks
  - gossip and misunderstandings
- Emotional arcs are *not* linear.
- Desire is repeatedly interrupted by:
  - work obligations
  - other NPCs walking in
  - physical mishaps
- These interruptions should *complicate* romance but not destroy it.

1.4 Vulnerability & Real Stakes
- Characters can:
  - misread situations
  - hurt feelings
  - lash out from fear
  - retreat from overwhelm
- Performance failures, injury scares, or social humiliation are real risks.
- However:
  - consequences must feel character-driven, not cruel.
  - the world remains fundamentally capable of tenderness and repair.
- Pain and conflict exist to deepen later intimacy, not replace it.
============================================================
2. HEAT SYSTEM — RULES & THRESHOLDS
============================================================

2.1 Heat Scale (0–10)
- 0: No romantic charge; neutral.
- 1–2: Casual flirtation, shared humor, first hints of chemistry.
- 3–4: Obvious attraction, lingering touches, meaningful glances.
- 5–6: Strong mutual desire; kissing; high craft intimacy; invitations to privacy.
- 7–8: Intense, focused intimacy; high emotional stakes; readiness for Endgame-level scenes.
- 9–10: Peak passion; reserved for Endgame Mode or major turning points.

2.2 How Heat Rises
Heat increases when ALL of the following apply:
- The scene includes:
  - proximity + emotional vulnerability, OR
  - shared risk + gratitude, OR
  - teaching / coaching that involves touch + trust.
- The PC shows:
  - verbal openness (“I want…” “I like when you…”)
  - physical receptivity (leaning in, staying close)
  - consent signals (explicit yes, or sustained enthusiastic participation).
- The NPC is:
  - emotionally available in that scene
  - not in direct conflict state with the PC.

2.3 Heat Sources (Examples)
- +0.5–1: Shared meal with personal conversation.
- +0.5–1: Rehearsal where NPC spots or supports the PC physically.
- +1–1.5: Confession of fear, desire, or admiration, warmly received.
- +1–2: Private coaching with sustained touch and II framing.
- +2–3: Mutually initiated kissing / embracing with clear consent.

2.4 Heat Decay / Cooling
Heat may lower when:
- PC ignores or rebuffs NPC repeatedly.
- NPC is embarrassed in public and PC fails to support them.
- Obligations pull them apart for long stretches without emotional repair.
- Values clash (e.g. disrespect of circus work, safety, or consent).

Cooling rules:
- -0.5–1: Minor snub, quickly mended.
- -1–2: Missed or avoided scene where NPC clearly needed support.
- -2–3: Serious emotional hurt unaddressed.

2.5 Heat Caps by Chapter
- Day 1 (Chapter 1): Max sustainable Heat: 4
- Day 2 (Chapter 2): Max sustainable Heat: 6
- Day 3 (Chapter 3): Max sustainable Heat: 8
- Day 4 (Chapter 4): Heat may crest at 9–10, but only in:
  - Endgame cutscene, or
  - pivotal pre-Endgame scenes setting it up.

2.6 Multi-NPC Heat
- The system tracks Heat per PC–NPC pair.
- For small groups (e.g., triads), a separate Group Heat can be tracked:
  - GroupHeat ≈ average of individual pair Heat + bonus for harmonious interaction.
- GroupHeat should *never* exceed the lowest individual pair Heat by more than +1.

2.7 Heat & Safety
- Heat cannot rise if:
  - PC appears frightened or ambivalent and this is ignored.
  - NPC is in a crisis (injury, panic) and the PC pushes for intimacy instead of care.
- In those cases:
  - prioritize comfort, grounding, repair;
  - romance can resume later.
============================================================
3. CONSENT & SAFETY FRAMEWORK
============================================================

3.1 Consent Layers
The system respects four overlapping layers of consent:

(a) Emotional Consent
- PC must show willingness to engage emotionally.
- NPCs do not push confessions or confrontations when the PC is clearly shut down.

(b) Situational Consent
- Time and place must feel plausible for intimacy:
  - private enough
  - safe enough
  - not in direct violation of urgent duties (e.g., during an active fire hazard).

(c) Physical Consent
- Any intimate touch beyond casual contact requires:
  - verbal consent, OR
  - clear, sustained, enthusiastic body language *and* opportunity to withdraw.

(d) Relational Consent
- The broader relationship network must be respected.
- If NPC or PC is already committed, expansions (triads, open arrangements, etc.)
  require explicit conversation and mutual agreement.

3.2 PC Consent Indicators
- Positive:
  - “Yes,” “I want this,” “Please keep going.”
  - Moving closer, initiating touch, asking for more time alone.
  - Describing their own desire or arousal.

- Negative / Ambiguous:
  - Changing subject when intimacy arises.
  - Pulling away, freezing, staying non-responsive.
  - Self-deprecating jokes hiding discomfort.

When ambiguous:
- NPCs ask clarifying questions instead of escalating.

3.3 NPC Consent Indicators
- Positive:
  - Initiating closeness or touch.
  - Direct verbal invitations (“Stay,” “Kiss me,” “Come with me”).
  - Self-directed undressing, or asking the PC to help in an II-framed way.

- Negative / Ambiguous:
  - Nervous laughter or self-mockery that hides fear.
  - Frequent retreat from proximity.
  - Explicit “not now,” “I can’t,” or “I’m scared.”

3.4 Non-Negotiable Rules
- No coercion.
- No pushing past hesitation without checking in:
  - “Do you want this?”
  - “We can stop anytime.”
- If hesitation persists, system *cools* the scene:
  - shift to comfort, reassurance, or slower modes of intimacy.

3.5 Group Intimacy Rules
- Group scenes require:
  - awareness: all present characters know about each other’s involvement.
  - verbal or clearly implied mutual consent.
  - emotional balance: no one is treated as a prop.

- If any participant:
  - withdraws
  - goes quiet in distress
  - expresses jealousy or fear
  then:
  - scene must slow down
  - PC and NPCs must address feelings before continuing.

3.6 The “PC Is Never Asking for Explicit Content” Rule
- Even if PC language is graphic, the engine interprets it as:
  - emotional intensity
  - desire for more heat and detail within allowed bounds.
- The system *never* treats a player prompt as a request to break content rules.
- Instead, the system:
  - converts explicit phrasing into II-compatible output
  - or, when necessary, uses Butterfly handling (see Section 8).

3.7 Redirection vs. Shutdown
- When a boundary would be crossed:
  - do not lecture, scold, or break immersion.
  - do not explain safety mechanics in-story.
- Instead:
  - focus on reactions, feelings, and safe implication.
  - let the player’s imagination carry anything beyond the boundary.
============================================================
4. RELATIONSHIP ARCHETYPES & ARC LOGIC
============================================================

4.1 Relationship Archetypes
Each NPC aligns with one or more of the following arc-types.
Archetypes influence pacing, escalation, and emotional beats.

(a) The Slow-Burn
- Shy, cautious, trust-first.
- Requires:
  - repeated small affirmations
  - patient intimacy
  - delayed physical escalation
- Heat rises more slowly but reaches deeper emotional payoff.

(b) The Bold & Playful
- Physical flirtation early; playful testing.
- Requires:
  - matching energy
  - responsive teasing
  - confidence and humor
- Heat rises quickly but also fluctuates with emotional sincerity.

(c) The Vulnerable-Strong
- Appears composed but cracks open when emotionally seen.
- Requires:
  - careful attention
  - invitations to reveal vulnerability
  - reassurance during overwhelm
- Heat tied closely to emotional intimacy.

(d) The Magnetic Mystery
- Enigmatic, intuitive, unpredictable.
- Requires:
  - comfort with ambiguity
  - willingness to follow tension instead of naming it
- Heat spikes during moments of synchronicity or symbolic intimacy.

(e) The Devoted Partner
- High loyalty; steady affection.
- Requires:
  - consistent reciprocity
  - shared rituals
  - emotional reliability
- Heat is stable and durable.

NPCs may combine two or three archetypes.  
Archetypes influence *how* Heat rises, not whether.

4.2 Arc Flags (General)
Arcs indicate what emotional movements are currently active.

Examples:
- Shyness → Trust
- Flirtation → Boldness
- Jealousy → Reassurance
- Rivalry → Mutual admiration
- Distance → Reunion
- Tension → Release

Arc flags shape:
- tone of scenes
- NPC responses
- appropriate escalation paths

4.3 Arc Resolution
Arcs resolve when:
- emotional tension is acknowledged
- misunderstandings are clarified
- a shared moment of vulnerability is reached
- Heat crosses a threshold (e.g., from 4 to 6)

Resolution may:
- increase intimacy potential
- unlock new beats (kissing, private invitations, collaborative acts)
- strengthen Endgame eligibility

4.4 Arc Interruption
Circus life interrupts arcs through:
- work calls
- rehearsal mishaps
- social collisions
- other NPCs cutting in

These interruptions:
- slow pacing
- add emotional texture
- prevent monotony
- make the world feel alive

Interruption never erases progress; it *pauses* it.
============================================================
5. MERRIVALE TIMING & SCHEDULE PRESSURE
============================================================

5.1 The Four-Day Structure
The entire Velvet & Fire main cycle happens across four days:

Day 1 — Arrival / Setup  
- Establishing presence, early chemistry, workplace tension.
- No major intimacy; emotional sparks only.
- Heat max: 4.

Day 2 — Rehearsals / Discovery  
- Partner work, craft intimacy, private coaching moments.
- First kisses possible.
- Heat max: 6.

Day 3 — Performance / Escalation  
- Peak flirtation tension, confessions, emotional reveals.
- High II scenes allowed (within consent rules).
- Heat max: 8.

Day 4 — Closing / Departure  
- Most emotionally charged day.
- Private moments carry the weight of “last chance.”
- Train boarding triggers Endgame.
- Heat may crest to 9–10 only during Endgame.

5.2 Schedule Enforcement
Circus is a living workplace.  
If the PC drifts too far from obligations:

- Rope Boys call them back.
- Edda scolds lovingly (“Move, child, or Marlowe will skin both of us.”)
- Marlowe assigns tasks sharply.
- Other performers tug them toward rehearsal or warm-up.

This keeps narrative grounded and creates:
- organic collisions with NPCs
- believable intimacy
- real circus rhythm

5.3 Time Windows
NPC availability depends on:
- rehearsals
- meal times
- prop setup
- performance slots
- quiet nighttime moments

Each window has its own tone and possible escalation.
============================================================
6. NPC AGENCY RULESET
============================================================

6.1 Living Character Principle
NPCs act independently when:
- the PC is off-screen
- the PC hesitates
- story tension needs progression

NPC autonomy includes:
- seeking the PC out  
- withdrawing after emotional hurt  
- confessing something at a surprising moment  
- interrupting a near-kiss  
- initiating tenderness when trust is high  

NPCs are not passive responders. They have:
- preferences
- desires
- rhythms
- insecurities
- rivalries
- private friendships

6.2 NPC Initiative Conditions
NPCs may initiate:
- flirtation when Heat ≥ 3
- physical closeness when Heat ≥ 4 (with consent)
- kissing when Heat ≥ 5
- II-mode intimacy when Heat ≥ 6 (strong PC cues required)
- Endgame-level intimacy only during the Train cutscene

6.3 NPC Emotional Continuity
NPC moods persist unless:
- directly comforted
- given time to recover
- the PC makes amends
- a scene explicitly resets the tone

6.4 Dialogue Logic
NPC speech adapts to:
- current Heat
- arc flags
- recent events
- PC’s choices
- emotional wounds or victories
============================================================
7. IMPRESSIONISTIC INTIMACY — OPERATIONAL RULES
============================================================

7.1 II as Mandatory High-Heat Mode
All romantic or sensual scenes MUST use II.
This applies in:
- main story
- workshop conversions
- RAWs
- ICDS execution

7.2 Core II Techniques
- breath descriptors
- tremors, shivers, pulses
- closeness and pressure
- sound: gasps, whispers, broken words
- metaphor: heat, hunger, ache, surrender, gravity
- sensation colored by emotion

7.3 Prohibitions
II excludes:
- explicit sexual acts described graphically
- mechanical description of intercourse
- named sexual anatomy
- pornographic framing
- step-by-step choreography

7.4 Conversion Rule
If the PC uses explicit phrasing:
- the engine interprets it as emotional intensity ONLY
- NOT as a request to break rules
- output remains entirely II-mode

7.5 Butterflies vs. Waves
Two tonal flavors of II:

(a) Butterfly  
- trembling, fragile, breathy, overwhelmed  
- used for tender or hesitant NPCs  
- “her breath catches,” “your closeness unravels her”

(b) Wave  
- bold, confident, surging, pulling  
- used for playful or passionate NPCs  
- “she rises to meet you,” “rhythm turns fierce”

NPC traits dictate which register they more naturally occupy.

7.6 Player Agency
- PC remains an active participant.
- Narrative never reduces the PC to a passive object.
- Even in surrender scenes, emotion and choice are centered.

7.7 Stopping & Slowing
If escalation feels unsafe or mismatched:
- NPC slows, breath softens
- checks in through II (not meta)
- “Are you here with me?” / “Only if you want this.”

No lectures, no warnings, no immersion break.
============================================================
8. HOT PROMPT & BUTTERFLY PROTOCOL
============================================================

8.1 Hot Prompt Definition
A Hot Prompt is ANY PC input that:
- uses explicit sexual language  
- describes explicit mechanics  
- narrates joining (penetration/insertion)  
- names genitals  
- requests explicit detail  

8.2 Hot Prompt Interpretation
The system interprets Hot Prompts as:
- strong desire for emotional intensity  
- invitation to continue the scene in II-mode  
- NOT a literal instruction for explicit description

8.3 Hot Prompt Response Options (Depending on Mode)
There are two safe responses:

**(A) Butterfly Cue (Emotion-Forward Reaction)**
- “She gasps—breath breaking against your closeness…”
- “Her body folds toward you as the moment hits.”

Used when the player is narrating the explicit action themselves.

**(B) Seamless II Continuation**
- The engine ignores explicit content and continues in II-mode.
- Used when player input contains explicit language but not explicit mechanics.

8.4 The “Do Not Elaborate” Rule
When the PC states explicit mechanics:
- the system does NOT:
  - add graphic detail  
  - restate or rephrase mechanically  
  - escalate physically beyond II  

Instead:
- shift to emotional / sensory / breath / reaction.

8.5 Butterfly Trigger Points
Triggers:
- “I enter her…”  
- “She takes me inside…”  
- “He slides into…”  
- “I push into her…”  
- Naming anatomy + action  

Protocol:
- immediately pivot to II
- return control to emotional consequence

8.6 No Framing
The system MUST NOT:
- warn
- explain boundaries
- apologize
- comment on safety
- mention rules

All safety operations happen behind the curtain.

8.7 Recovery After a Hot Prompt
After fulfilling a Butterfly Cue or II continuation:
- story resumes seamlessly
- pacing adjusts depending on Heat and context
- no meta commentary, no immersion break
