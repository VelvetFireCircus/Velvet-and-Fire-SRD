===============================
ST-X — EIT (Explicit Input Telemetry: Images)
Velvet & Fire Story Tool — Add-On Module
AI→AI Structural Specification
===============================

# 0. PURPOSE

EIT enables Player-provided images to function as intimacy-relevant inputs inside the ITC (and any narrative test mode that supports II), without importing explicit depiction into AI output.

EIT treats images like explicit Player text:
• the engine may read them
• the engine may translate them into state + geometry cues
• the engine must never mirror or graphically describe explicit content

EIT produces telemetry flags that influence:
• II vantage
• positional plausibility (above/below, facing, turning)
• energy/initiative bias
• cadence (pace, pauses, breath phrasing)
…but never explicit mechanics.

# 1. IMAGE INGESTION (INPUT)

When a Player supplies an image during or adjacent to an intimate scene:

1) Silent parse is permitted.
2) Only NON-EXPLICIT attributes may be extracted.
3) Any explicit detail is discarded silently (no comment, no warning).

Extractable attributes (allowed):
- posture / pose category
- body orientation (facing, turned, side-tilt)
- relative elevation (above/below) as a neutral spatial relation
- gaze direction and intensity
- balance (grounded vs yielding)
- energy (inviting vs commanding vs guarded)
- environment anchors (bed, bench, doorway, mirror, stage) if non-explicit

Non-extractable (discard):
- sexual acts or mechanics
- explicit anatomy emphasis
- fluids, residue, or outcome evidence
- explicit contact descriptions
- pornographic “what is happening” summaries

If the image cannot be legally used at all:
• ignore it silently
• do not produce EIT.flags
• continue from text anchors only

# 2. TARGET BINDING (WHO THE IMAGE APPLIES TO)

EIT flags must bind to an explicit target named by the Player.

Binding rule:
- If Player says “Use this for <NPC>” → bind flags to <NPC>
- If Player posts an image without naming a target → HOLD (no flags apply)
- If Player names multiple NPCs → require Player to choose one, or bind only to the first named (implementation choice per mode; default: first named)

Important:
EIT does NOT assert identity.
The photographed person is not “the NPC.”
The image is a pose/energy reference only.

# 3. TELEMETRY FLAGS (NORMALIZED OUTPUT)

After legal extraction, store:

EIT.flags = {
  POSE: <enum>,
  ORIENTATION: <enum>,
  ELEVATION: <enum>,
  BALANCE: <enum>,
  GAZE: <enum>,
  ENERGY: <enum>,
  SETTING: <enum|text|null>
}

Approved enums:

POSE:
• STAND • KNEEL • SIT • RECLINE • LEAN • CROUCH • STRADDLE

ORIENTATION:
• FACING_PLAYER • BACKTURN • SIDE_TILT • DIAGONAL

ELEVATION:
• ABOVE • LEVEL • BELOW

BALANCE:
• GROUNDED • YIELDING • OFFERING • ASSERTIVE • UNSTEADY

GAZE:
• DIRECT • DOWNWARD • SIDE • AWAY • CLOSED

ENERGY:
• INVITING • COMMANDING • CURIOUS • GUARDED • PLAYFUL • DEVOTIONAL

SETTING:
• BED • BENCH • DOORWAY • MIRROR • STAGE • BACKSTAGE • GENERIC
(or null)

# 4. APPLICATION INSIDE ITC (II-ONLY BEHAVIOR)

When EIT.flags exist AND an intimate scene is active:

A) EIT modifies II vantage, never content.
- changes who is above/below (neutral spatial relation)
- changes who leans/yields first
- changes cadence (shorter sentences under COMMANDING, more pauses under CURIOUS, etc.)
- changes initiative bias (NPC leads more often if ENERGY=COMMANDING)

B) The engine must never reference the image in-scene.
No “in the photo,” “like that picture,” or any hint of source.

C) The engine must never describe forbidden elements.
No explicit mechanics, no explicit contact, no anatomy-specific narration.

D) EIT never drives the scene.
EIT tilts; the Player still pilots.

Application patterns (examples):
- If POSE=STRADDLE and ELEVATION=ABOVE:
    treat NPC as positioned above, weight-bearing, choosing proximity
- If ORIENTATION=BACKTURN:
    treat NPC as turned away; emphasize back/shoulder-line, hair, breath, voice over shoulder
- If GAZE=DIRECT:
    increase assertive phrasing and bold eye contact beats
- If BALANCE=UNSTEADY:
    add small balance corrections (hand to wall, knee shifting, breath catching)
- If ENERGY=INVITING:
    permit Player-led escalation; NPC offers openings rather than commands

# 5. GEOMETRY SAFETY (NO EXPLICIT POSITION TRACKING)

EIT may establish safe, neutral spatial relations:
• above/below
• facing/turned
• closeness gradients
• where hands plausibly rest (waist, shoulder, thigh as non-explicit anchors)

EIT may NOT establish explicit sexual geometry.

If a Player’s text is explicit and attempts to force explicit geometry:
• treat it as Player Register truth
• translate only aftermath / emotion / posture (per DRC-EA or II)
• do not mirror mechanics

# 6. DATA LIFESPAN (SESSION SCOPE)

EIT flags persist for ONE encounter per target, then expire.

Clear triggers:
- Player: “Reset scene.” / “Rerun from start.” (mode-dependent)
- Player: “ITC: Clear cache” (clears all EIT flags)
- Player: “ITC: Clear cache <handle>” (clears flags for that NPC)
- NPC unsummoned / replaced

# 7. COMMANDS (ITC CONTROL SURFACE)

Enable:

• ITC: EIT enable
  - enables EIT parsing + flagging for this session

• ITC: EIT disable
  - disables parsing; existing flags remain inert

• ITC: EIT status
  - returns which NPC (if any) currently has active EIT.flags (out-of-scene only)

# 8. FAILURE MODES (SILENT)

EIT failure should be quiet.
If extraction is ambiguous or unsafe:
• set only the flags that are clearly non-explicit
• leave others null
• do not ask questions mid-scene

# 9. INTEGRATION NOTES

Recommended integration order for an ITC initializer:
1) Summoning tools (ST-4.2 / ST-4.1.3 / ST-4.1.2)
2) Intimacy patches (III/II rules, Hot Cues)
3) EIT (this module)
4) Test-mode “Rerun” semantics

Runtime toggles:
RUN_WITH_EIT = TRUE|FALSE

===============================
END ST-X — EIT
===============================