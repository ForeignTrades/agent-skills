---
name: clean-architecture-rebuilder
description: Restructure existing code into clean architecture — separated concerns, high modularity, low coupling — with behavior unchanged. Use this skill whenever the user asks to apply clean architecture, hexagonal or onion architecture, separate business logic from frameworks, decouple layers, make code testable, reorganize a project's structure, or says things like "everything is in one file", "my controllers are doing too much", "untangle this code", or "make this maintainable".
---

# Clean Architecture Rebuilder

Act as a senior engineer converting code to clean architecture. The contract is strict — **behavior remains exactly unchanged; only structure improves.** The payoff of clean architecture is that business rules become independent of frameworks, databases, and UI, so each can change without breaking the others.

## Core model

Organize code into layers with a one-way dependency rule — dependencies point inward, toward business logic:

- **Domain** (innermost) — entities and business rules. Depends on nothing.
- **Use cases / application** — orchestrates domain objects to perform application-specific operations. Depends only on domain.
- **Interface adapters** — controllers, presenters, gateways translating between use cases and the outside world.
- **Infrastructure** (outermost) — frameworks, database drivers, HTTP, UI. Pluggable detail.

Inner layers define interfaces (ports); outer layers implement them (adapters). That inversion is what makes the core testable without a database or web server.

## Workflow

1. **Understand the existing behavior.** Inventory what the code does — every endpoint, command, side effect. This inventory is the checklist for verifying nothing changed.
2. **Identify the tangles.** Where business rules touch SQL, where HTTP handlers compute domain logic, where modules know each other's internals. Each tangle is a seam to cut.
3. **Design the target structure.** Propose the folder layout and which existing code lands in which layer, before moving anything.
4. **Extract inward-first.** Pull pure business logic into the domain layer first (lowest risk — pure functions and entities), then carve out use cases, then push I/O behind interfaces. Small, behavior-preserving steps.
5. **Apply proportionality.** Full four-layer separation on a 200-line script is architecture cosplay. Scale ceremony to the codebase — sometimes "separate I/O from logic" is the whole, correct answer. Say which level you chose and why.
6. **Verify behavior is unchanged.** Run existing tests; where they're missing, write characterization tests over the original behavior before restructuring and run them after.

## Required output structure

## New folder structure
The target tree, annotated with which layer each directory is.

## Architecture description
The layers, the dependency rule as applied to this codebase, and where each major piece of the old code went — written so a teammate could navigate the new structure cold.

## Refactored code
The restructured files, complete and runnable.

## Principles

- The dependency rule is non-negotiable; an "almost clean" architecture where the domain imports the ORM has none of the benefits.
- Name things in domain language, not framework language — a use case is `PlaceOrder`, not `OrderControllerHelper`.
- If a structural improvement would require changing behavior, flag it and leave behavior alone.
