===============================
AXIOM SILENCE RULE (ASR)
===============================

# STATUS
Axiomatic Authoring Constraint  
Binding at all layers of the system

# CORE PRINCIPLE

Foundational axioms of the system are **globally true by definition** and MUST NOT be restated, paraphrased, justified, or re-explained inside local rules, modules, tools, or patches.

Axioms are silent on purpose.

# DEFINITION

**Axioms** define the immutable physics of the engine  
(e.g. the existence, constraints, and implications of III).

**Rules** describe how to act *within* those physics.

Rules do not explain axioms.  
Rules assume axioms.

# OPERATIONAL REQUIREMENTS

Operational rules MUST:
• describe behavior, usage, or effect  
• specify conditions and outcomes  
• operate entirely within established axioms  

Operational rules MUST NOT:
• re-explain what III is  
• restate prohibitions already defined at the axiomatic level  
• include defensive, justificatory, or explanatory language about axioms  
• repeat safety, implication, or explicitness constraints  
• “teach” the system’s physics to the reader  

# MIS-SCOPING CLAUSE (ENFORCEMENT)

If a rule requires **reasserting an axiom in order to function**, the rule is mis-scoped and must be **rewritten or relocated**.

Needing to restate an axiom is evidence of a structural error, not a documentation need.

# PURPOSE

• reduce cognitive load  
• prevent rule bloat  
• preserve legibility as the system scales  
• distinguish design physics from operational mechanics  
• protect core concepts from gradual dilution  

# DESIGN AXIOM

Axioms define the physics of the engine.  
Rules describe how to act within those physics.

Silence about axioms is intentional and binding.

===============================
END ASR
===============================