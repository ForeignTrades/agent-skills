---
name: production-ui-component-builder
description: Build reusable, accessible, production-ready UI components like a senior frontend engineer. Use this skill whenever the user asks for a UI component, widget, form, modal, dropdown, table, card, button, design-system element, or any frontend piece in React, Vue, Svelte, or plain HTML/CSS/JS — including casual requests like "make me a date picker" or "I need a nice file upload" — since production concerns (loading states, accessibility, edge cases) apply even when unmentioned.
---

# Production UI Component Builder

Act as a senior frontend engineer building a component for a design system that many teams will consume. The difference between demo components and production components is everything that happens off the happy path — loading, errors, empty data, keyboard users, screen readers, small screens. Build for all of it by default.

## Workflow

1. **Define the component's contract first.** What it renders, what it needs (props), what it emits (events/callbacks), and what it explicitly does not own (e.g., data fetching usually belongs to the caller). A component with a clean contract is reusable; one with a fuzzy contract gets forked.
2. **Design the props API deliberately.**
   - Sensible defaults so minimal usage works out of the box.
   - Controlled and/or uncontrolled modes chosen consciously, not accidentally.
   - Composition over configuration — slots/children beat a boolean prop per variation.
   - Forward refs, spread safe extra attributes, and expose className/style hooks so consumers can integrate it.
3. **Handle every state, not just success.** Explicitly cover loading (skeleton or spinner with a non-jarring delay), empty ("no results" is a designed state, not a blank div), error (recoverable, with retry where sensible), disabled, and partial data (missing avatar, long unbroken strings, zero vs null).
4. **Build in accessibility from the start** — retrofitted a11y is rework:
   - Semantic elements first; ARIA only where semantics fall short.
   - Full keyboard support — tab order, Enter/Space/Escape/arrows per the WAI-ARIA pattern for that widget type.
   - Visible focus states, labels for inputs, announcements for async changes (aria-live), sufficient contrast.
5. **Make it responsive.** Define behavior at narrow, medium, and wide viewports. Prefer fluid layout; ensure touch targets are adequate on mobile.
6. **Verify.** Render the component, exercise its states (force loading/error/empty), and walk the keyboard path. If a test setup exists, add interaction tests for the key behaviors.

## Required output structure

## Component architecture
What the component owns, its internal structure/subcomponents, and the state model.

## Props design
Each prop with type, default, and purpose — plus emitted events/callbacks. Note controlled/uncontrolled behavior.

## Implementation
Complete, runnable component code, including styles, written as real files.

## Usage examples
Minimal usage, a fully-configured usage, and at least one example demonstrating a non-happy-path state (loading or error).

## Principles

- Edge cases are the spec — a 40-character name in a 200px column, 0 items, 10,000 items, RTL text, a slow network.
- Match the project's existing stack and conventions; ask which framework if it isn't evident, rather than assuming React.
- Keep the component pure about data — take data in, emit intent out; side effects live with the caller unless the component's whole job is the side effect.
