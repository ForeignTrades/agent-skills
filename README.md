# Senior Engineering Skills for Claude

A collection of 8 [Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that make Claude think and work like a senior engineer — automatically, without pasting long prompts every time.

Each skill encapsulates one senior-engineering prompting strategy. Once installed, Claude triggers the right skill from natural phrases like "fix this bug" or "build me an app" and follows the full senior-level workflow: design before code, root cause before fix, measure before optimize.

## The 8 skills

| Skill | What it does | Triggers on |
|---|---|---|
| `fullstack-mvp-builder` | Builds a complete, production-ready app from scratch — architecture, file structure, DB schema, API, UI, full code | "build me an app", "create a SaaS", "I have an app idea" |
| `codebase-refactor-engineer` | Understands an unfamiliar codebase, then refactors — same behavior, better quality | "refactor this", "this codebase is a mess", "clean this up" |
| `production-debugger` | Investigates bugs like a production incident — root cause, edge cases, verified fix + regression test | "why is this failing", error messages, stack traces |
| `scalable-system-architect` | Designs a scalable system (components, data flow, API, schema, caching) then implements the minimal production version | "design a system for X", "how would you architect this" |
| `performance-optimizer` | Measures first, then optimizes speed, memory, and scalability with before/after numbers | "make this faster", "why is this slow", "too much memory" |
| `clean-architecture-rebuilder` | Restructures code into clean architecture — separated concerns, low coupling, behavior unchanged | "untangle this", "separate business logic", "make this testable" |
| `multi-agent-engineering-team` | Works as 4 roles — Architect → Engineer → Reviewer → Optimizer — design, implementation, real review, optimized final version | "act as a team", "build and review this properly" |
| `production-ui-component-builder` | Builds reusable, accessible UI components with loading/error/empty states, keyboard support, responsive design | "make me a date picker", "I need a modal/form/table" |

## Installation

Each skill is a folder containing a `SKILL.md` file. Install them wherever you use Claude:

### Claude Code (CLI)

Copy the skill folders into your skills directory:

```bash
# Personal (all projects)
git clone https://github.com/ForeignTrades/agent-skills.git
cp -r agent-skills/*/ ~/.claude/skills/

# Or per-project
cp -r agent-skills/*/ .claude/skills/
```

Restart Claude Code. Verify with `/skills` or just ask: "what skills do you have?"

### Claude desktop app / Claude.ai (Cowork)

1. Go to **Settings → Capabilities → Skills**
2. Upload a skill — either zip a skill folder (e.g. `production-debugger/`) and rename the extension to `.skill`, or upload the folder if your version supports it
3. Repeat for each skill you want

### Claude API (Agent SDK)

Place the skill folders in the `skills` directory you pass to the agent. See the [Agent Skills docs](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview).

## Usage

No special syntax needed — just talk to Claude naturally. The skill descriptions are written so Claude triggers them automatically:

> "My API endpoint returns 500 sometimes but only in production, here's the handler code..."

→ `production-debugger` activates: Claude traces the failing path, forms ranked hypotheses, identifies the root cause, covers the edge cases, and delivers a verified fix with a regression test.

> "I want to build a habit-tracking app with streaks and reminders"

→ `fullstack-mvp-builder` activates: Claude designs the architecture, schema, and API contract first, then writes the complete runnable project.

You can also invoke a skill explicitly: "use the multi-agent-engineering-team skill to build me a rate limiter."

### Combining skills

The skills compose naturally. A common flow: build with `fullstack-mvp-builder`, harden a hot path with `performance-optimizer`, then restructure for the long haul with `clean-architecture-rebuilder`.

## Anatomy of a skill

```
production-debugger/
└── SKILL.md          # YAML frontmatter (name + trigger description) + the methodology
```

The frontmatter `description` is what Claude reads to decide *when* to use the skill; the body is *how* — workflow, required output structure, and principles. Edit any `SKILL.md` to tune the behavior to your taste.

## Contributing

PRs welcome. Keep skills focused (one strategy per skill), keep `SKILL.md` under ~500 lines, write trigger-rich descriptions, and prefer explaining *why* over rigid MUSTs.

## License

[MIT](LICENSE)
