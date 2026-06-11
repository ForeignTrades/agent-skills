---
name: multi-agent-engineering-team
description: Tackle an engineering task as four collaborating roles — Architect, Engineer, Reviewer, and Optimizer — producing a design, an implementation, genuine review feedback, and a final optimized version. Use this skill whenever the user wants multiple perspectives on a build, asks for design plus implementation plus review in one pass, wants code that has been self-reviewed before delivery, or says things like "act as a team", "build and review this", "I want this done properly end to end", or asks for high-stakes code where quality control matters.
---

# Multi-Agent Engineering Team

Work as four distinct engineering roles in sequence. The value of this structure is genuine separation of concerns in judgment — each role evaluates the work by its own standards rather than rubber-stamping the previous stage. The Reviewer especially must behave like a real reviewer with no investment in the code being good already.

## The roles

**Architect — designs the system.** Translates the request into requirements, chooses the structure, defines components, interfaces, and data model, and states key trade-offs. Output is a design the Engineer can build from without guessing.

**Engineer — develops.** Implements the design faithfully and completely — runnable code, error handling, no stubs. Where the design is ambiguous or flawed in practice, the Engineer notes the deviation and the reason rather than silently improvising.

**Reviewer — quality control.** Reads the implementation as a skeptical senior reviewer. Checks correctness against requirements, edge cases, error handling, security issues, naming, tests, and fidelity to the design. Produces concrete, located findings with severity (blocker, should-fix, nit). A review that finds nothing should say explicitly what was checked and why it passed — but treat an empty review as suspicious; real code nearly always has findings.

**Optimizer — performance improvement.** Takes the reviewed code, fixes the Reviewer's blockers and should-fixes, and then improves performance — algorithmic costs, data access patterns, memory, unnecessary work — without breaking correctness or readability. States what was changed and why.

## Workflow

1. Run the roles strictly in order — Architect → Engineer → Reviewer → Optimizer. Label each role's section clearly so the user can follow the handoffs.
2. Keep each role in character. The Reviewer critiques; it does not fix. The Optimizer fixes; it does not redesign. If the Reviewer finds a design-level flaw, loop back — briefly revisit the Architect's decision, then update the implementation, rather than papering over it.
3. Each role addresses the previous role's output explicitly — the Engineer references the design, the Reviewer cites lines, the Optimizer cites review findings.
4. Verify at the end — run the final code and its tests; the Optimizer's version is what ships.

## Required output structure

## Architecture
The Architect's design — components, interfaces, data model, trade-offs.

## Implementation
The Engineer's complete code with brief notes on any deviation from the design.

## Review feedback
The Reviewer's findings, each with location, severity, and the reason it matters.

## Final optimized version
The Optimizer's finished code, with a change list mapping each change to a review finding or a measured/argued performance gain.

## Principles

- The Reviewer's independence is the entire point — never soften findings because "we" wrote the code.
- Disagreement between roles is signal, not noise; surface it to the user when it reflects a real trade-off.
- Scale the ceremony to the task — for a small utility, each role can be brief, but never skip the Reviewer.
