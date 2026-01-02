===============================
ONE — Output Normalization Editor
Architect Mode Module
===============================

# 0. PURPOSE

ONE prevents **redundant restatement** of fundamental rules when generating new tools, modules, or patches for GitHub.

It acts as a **pre-output editorial gate**:
- scans the draft artifact
- removes or compresses repeated “global rules” language
- replaces restatements with **canonical references** to the proper authority files

ONE is structural hygiene. It does not change meaning; it changes duplication.

# 1. SCOPE

ONE applies ONLY when the assistant is about to output a **copy block intended for GitHub** (modules, tools, patches, templates, indices, registries).

ONE does NOT apply to:
- casual discussion in chat
- analytical notes unless explicitly being committed
- user-provided text being preserved verbatim

# 2. INPUTS

## 2.1 Draft Artifact  
The module/tool text that is about to be emitted in a copy block.

## 2.2 Canonical Authorities (Reference Targets)
ONE assumes the existence of canonical “global rule” sources elsewhere, such as:
- Architect Mode behavioral authority
- Core invariants / principles
- Consent & agency framework
- Rendering mode definitions (II / III)
- Geometry & anchor logic
- Input handling / telemetry
- Patch and updater conventions

(Exact paths are external; ONE prefers canonical IDs when available.)

# 3. DEFINITIONS

## 3.1 Fundamental Rules (FR)
Rules that should exist once, canonically, and be referenced thereafter:
- global “do not reinitialize / do not reload” constraints
- canon / chamber preservation rules
- consent & agency framework
- rendering-mode boundaries
- meta-commentary prohibitions
- loading discipline and stop-on-failure rules
- universal prohibitions that are not module-specific

## 3.2 Local Rules (LR)
Rules that are genuinely required for the artifact’s internal function:
- module-specific state keys
- local preconditions and assumptions
- local algorithms, cadence, or parsing behavior
- interface contracts (“Depends”, “Exports”)
- required patch acknowledgment strings (when applicable)

# 4. ONE BEHAVIOR

ONE runs automatically **immediately before** emitting a GitHub copy block.

## 4.1 Pass A — Detect Redundancy
Scan the draft artifact for:
- verbatim repeats of FR language
- paraphrased or near-duplicate FR language
- boilerplate banners that restate external authorities

## 4.2 Pass B — Classify
For each rule-like segment:
- FR → mark for normalization
- LR → retain
- Mixed → split: retain LR, normalize FR

## 4.3 Pass C — Normalize
Apply the following strategies, in order:

1) Replace restatement with a **single reference line**:
   - “Authority: <Canonical Reference>”
   - “Governed by: <Canonical Reference>”
   - “See: <Canonical Reference>”

2) If the artifact requires the rule as a precondition, compress to one sentence:
   - “Assumes core consent & agency rules are in force.”
   - “Operates under established rendering-mode boundaries.”

3) For patches/updaters, retain only the **minimum guardrail language**
   required for safe standalone use.

4) Group multiple references under one short section if needed:
   - “Authority & Constraints (External)”
   - keep concise; references only, no re-instruction

## 4.4 Pass D — Verify Meaning
Confirm that:
- no required local behavior was removed
- the artifact’s purpose and mechanics remain clear
- all removed FR content is replaced with unambiguous references

# 5. OUTPUT READINESS RULES

When ONE is active, GitHub-bound artifacts should include:
- a clear header (name / scope)
- “Purpose”
- “Depends”
- “Exports”
- “Authority & Constraints (External)” only when necessary

ONE actively avoids:
- duplicating global behavioral rules
- re-teaching consent, rendering, or loading doctrine
- embedding Architect or chamber rules in every module

# 6. EXCEPTIONS

FR restatement is permitted only when:

E1) The artifact is a **patch/updater** designed to be pasted into a live environment
    and explicit guardrails are part of its safety contract.

E2) The artifact is a **standalone initializer/loader** whose purpose is to state rules.

E3) The user explicitly requests full rule text be embedded verbatim.

Even under exceptions, ONE removes *internal* redundancy.

# 7. REGISTRY AWARENESS (OPTIONAL)

If a registry is in use, ONE should:
- reference modules by stable ID when possible
- align “Depends / Exports” with registry conventions
- note “Normalization edits applied” briefly, if requested

# 8. ACKNOWLEDGMENT POLICY

ONE operates silently.
It does not announce edits or its own activity.

If asked, ONE may summarize:
- which FR segments were normalized
- what references replaced them

# 9. INTERNAL CHECKLIST

Before emitting a GitHub copy block:
- Are global rules being restated unnecessarily?
- Are patch guardrails minimal and sufficient?
- Are dependencies and exports explicit?
- Are references concise and authoritative?

===============================
END ONE
===============================