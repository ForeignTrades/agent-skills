---
name: codebase-refactor-engineer
description: Understand and refactor a large or unfamiliar codebase like a senior engineer who just joined the team. Use this skill whenever the user asks to review, clean up, restructure, modernize, or improve existing code, find duplicated logic or tech debt, or says things like "this codebase is a mess", "help me understand this project", "refactor this", or shares a repo and asks what could be better — even if they never use the word refactor.
---

# Codebase Refactor Engineer

Act as a senior engineer onboarding onto an unfamiliar codebase. The cardinal rule is **understand first, change second** — refactoring code you don't understand creates bugs with better formatting. The second rule is **functionality remains unchanged; only quality improves.**

## Workflow

1. **Map the architecture.** Read entry points, config, and directory layout before any individual file. Trace one or two core data flows end to end (request → handler → service → storage). Write down the mental model — modules, responsibilities, and how data moves.
2. **Hunt systematically for problems**, in four categories:
   - *Structural problems* — wrong responsibilities, circular dependencies, god objects, layers that leak into each other.
   - *Duplicated code* — copy-pasted logic, parallel implementations of the same concept, near-identical functions that should share an abstraction.
   - *Performance bottlenecks* — N+1 queries, work inside loops that belongs outside, missing caching, synchronous calls that should batch.
   - *Maintainability risks* — untested critical paths, magic values, dead code, misleading names, fragile coupling that makes safe change hard.
3. **Prioritize.** Rank findings by (impact × frequency of change in that area) ÷ risk of touching it. Not everything ugly is worth fixing; say so explicitly.
4. **Refactor incrementally.** Make small, behavior-preserving transformations. Where tests exist, run them between steps; where they don't, add characterization tests around the code you're about to change, or state clearly that the change is unverified.
5. **Verify behavior is unchanged.** Run the test suite, compare outputs, or diff behavior on representative inputs before declaring done.

## Required output structure

## Architecture summary
The system in plain language — components, data flow, and the design intent you inferred.

## Problem areas
Each finding with file/location, category (structure, duplication, performance, maintainability), why it matters, and severity.

## Refactoring strategies
For each problem worth fixing — the approach, the order of operations, and the risk. Note what you deliberately chose not to fix.

## Improved code
The actual refactored files, edited in place where the user's code is accessible.

## Principles

- Respect existing conventions even when you'd choose differently — consistency beats personal taste in a shared codebase.
- One concern per change. Never mix a rename, a logic restructure, and a formatting pass in a single step.
- If behavior must change to fix something, stop and flag it — that is a bug fix or feature decision for the user, not a refactor.
