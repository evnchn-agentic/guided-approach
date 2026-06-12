# guided-approach

**Your agent can do the work. It can't do the judgement. This is the interface between the two.**

A Claude Code skill for the sessions where one prompt was never going to cut it — forty
board items, a fried MOSFET, a cleanup that could eat your toolchain — and where the usual
fallback is a wall of chat questions you answer by scrolling, re-reading, and slowly losing
the will to live.

The guided approach instead: **the agent works autonomously between decision points, and
every decision point arrives as a question that carries its own evidence** — answerable
from the question alone, on a phone, in a queue, without opening a single tab:

> **#6100 verdict:** clean, root-cause fix, mechanics verified against Vue internals
> (emits interception + handler-key lookup + message ordering). No issues found. What
> should I do?
>
> - [ ] **Approve + verification notes (Recommended)**
> - [ ] Approve plain
> - [ ] Comment only, no approval
> - [ ] Skip / hold
> - [ ] *Other: ____* ← where the operator actually steers

And when the evidence outgrows a question — a severity call, a coverage matrix — it
arrives as a self-contained HTML deep-dive instead, and the same question gets re-asked
after you've read it.

## Origin story

Invented 2026-06-12, on a phone, against a 40-item maintainer board. By end of day: four
PRs reviewed (one Request Changes carrying an empirically confirmed footgun a desktop pass
had missed), two stale PRs revived, one counter-proposal PR built-tested-shipped, board
down to **3 items** awaiting the operator. The maintainer on the other side noticed the
output quality unprompted. Every decision in that run fit on a lock screen.

Then we mined **43 past sessions** and found the same technique already load-bearing in
six *other* domains — it just didn't have a name yet.

## What's inside

Thin **core invariants** (question = mini-report, batch don't drip, "Other" is the real
spec, rich-render escape hatch, outward-post draft gate) + **seven stock playbooks** the
agent picks from or blends mid-session:

| # | Playbook | Flavor |
|---|----------|--------|
| 1 | Queue triage | the origin: work one item fully, gate outward actions, leave the board honest |
| 2 | Requirements interview | every question states why it matters; ends with a "design OK?" gate |
| 3 | Physical-world elicitation | "caliper numbers you can get" — the agent can't measure reality |
| 4 | Knowledge probing / drills | the question tool as a quiz engine |
| 5 | Strategy / meeting prep | options are stances, consequences spelled out |
| 6 | Destructive-action scoping | exact file lists before anything irreversible |
| 7 | Governance gates | approval applies to bytes, not vibes |

Plus the failure modes already paid for, so you don't pay twice: question-dripping (worst
observed: ~20 sequential singles), fork-resume re-asking, evidence stuffed past the UI
truncation point.

## Status: brick (拋磚引玉)

Deliberately rough, thrown to attract refinement — see the
[chengyu-throw-brick-attract-jade skill](https://github.com/evnchn-agentic/chengyu-skills/tree/main/chengyu-throw-brick-attract-jade)
for why the roughness is the feature, not an apology.

## Known gaps (bait — refine me)

- Rich-render conventions (dark theme, scroll d-pad for the remote nested-viewport bug) are
  operator-memory pointers, not embedded yet.
- Playbooks 4, 5, 7 are thinner than 1–3 — fewer mined sessions behind them.
- Blending guidance is one sentence; a worked blended example would anchor it.
- references/ with verbatim transcript excerpts per playbook not yet extracted.
