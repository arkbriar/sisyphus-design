# sisyphus-design

A skill that produces high-quality design documents through iterative refinement. Supports both Claude Code and Codex.

## Philosophy

The boulder rolls back. That's the point.

Sisyphus wasn't punished for failing — he was punished for trying. Camus said imagine him happy. We say imagine him useful: each push leaves the boulder a little higher than before.

This plugin drafts a design and hands it to a reviewer who has never seen it and never will again. The reviewer finds what the author couldn't. The author fixes it. A new reviewer — equally blind, equally merciless — checks the fix. The boulder rolls back. It goes up again.

Your time enters where machines can't substitute. Everything else is the hill.

## What it does

`/sisyphus-design <requirement>` runs a multi-phase process:

1. **Research & Diverge** — investigates the codebase and domain, thinks from first principles, generates 2-3 fundamentally different approaches
2. **Interrogate** — presents the critical path, approaches, and questions that reveal which approach fits your constraints
3. **Decisions** — presents key decisions for approval with trade-offs and a concrete example trace
4. **Draft & Refine** — drafts the design, then runs independent evaluators until the design stabilizes
5. **Review** — you read and comment on the design file
6. **Refine & Deliver** — addresses your comments through the same process, delivers the final design

Three human touchpoints. Everything else is automated.

## Install

### Claude Code

```
/plugin marketplace add arkbriar/sisyphus-design
/plugin install sisyphus-design
```

### Codex

Copy the skill into your Codex skills directory:

```bash
cp -r skills/codex-design ~/.codex/skills/sisyphus-design
```

Enable the `request_user_input` tool so the skill can pause for your input during human phases:

```bash
codex features enable default_mode_request_user_input
```

## Usage

```
/sisyphus-design Distributed task queue with at-least-once delivery, backed by PostgreSQL, implemented in Rust
```

In Codex, invoke with `$sisyphus-design` or let it trigger automatically from the description.

The design is written to `design/` in your project (e.g., `design/distributed-task-queue.md`).

## Example

- [DistributedTaskQueue](https://github.com/arkbriar/DistributedTaskQueue) — designed and implemented end-to-end with this skill

## Reuse

The methodology here is a harness at the meta level — the iterative loop of draft, evaluate, fix is not specific to software design. The checklist (`skills/design/checklist.md`) can be extracted and applied to any structured document where consistency, coverage, and minimality matter.

## License

MIT
