---
name: guided-approach
description: Use when a simple prompt ain't cutting it — work that needs operator judgement at many points along the way. Agent works autonomously between decision points; decision points become multi-select questions that carry their own context; oversized evidence becomes rich-render artifacts. Pick the stock playbook below that matches the session (or blend). Works anywhere; shines on mobile.
---

# Guided approach

Some work is one prompt → one artifact. The rest needs the operator's judgement woven
through agent execution. The guided approach: **the agent works autonomously between
decision points, and renders each decision point as a structured question round the
operator can answer from the question alone.** Born on mobile (small screen forces the
discipline); just as valuable on desktop.

**How to use this skill: pick the stock playbook that matches the session. Blend when the
session shifts shape mid-flight (a triage that uncovers a design question borrows the
interview playbook for that stretch, then returns).** The invariants below apply to all.

## Core invariants (all playbooks)

- **Ground truth before questions.** Pull live state (CI, last actor, measurements, scans);
  never interview off stale notes — flag discrepancies with them instead.
- **Question = mini-report.** Body carries verdict + evidence + constraint (~150–420 chars;
  past ~300 the UI may truncate — overflow into option descriptions or a rich render, never
  into vagueness). Answerable without reopening anything.
- **Batch rounds (≤4 questions), don't drip.** Worst observed anti-pattern: ~20 sequential
  singles.
- **multiSelect's job:** batched action authorization ("which of these N do I execute") and
  pick-all-that-apply elicitation. Genuine either/or stays single-select (~80% of real
  usage). Recommended option first, labeled.
- **One option = one decision — never bundle.** An option that reads "X of {several things}"
  ("ship the 4 fold-ins", "clean up all N") is un-checkable: the operator can't approve it
  without approving a sub-bundle they can't see into, so they leave it blank. Keep each option
  atomic and independently decidable. When the decisions are heterogeneous or consequential,
  surface them **one at a time, highest-value first** (playbook 1's "one item fully, then one
  question" applied to the *decisions*) — the ≤4-batch rule is for *peer* choices, not a licence
  to compress N distinct calls into one row.
- **"Other" free-text is the real spec.** Operators steer hardest there, often overriding
  the option set entirely. Parse and follow that, not the nearest option.
- **Rich-render escape hatch.** Evidence too big for a question → dark self-contained HTML
  deep-dive via the file-share tool (`SendUserFile`), then re-ask the same question. Render carries
  evidence; question carries the decision.
- **Outward/destructive draft gate.** New claims under the operator's name, and anything
  irreversible, get shown first. Batch-approved mechanical ops go direct.
- **Fork awareness.** Answers don't survive session forks/resumes — on déjà-vu, re-state
  prior answers instead of re-asking.

## Stock playbooks

### 1. Queue triage (the origin — issues, PRs, boards, inboxes)

1. Pull queue + live state; cross-reference any existing triage notes, flag drift.
2. Opening partition round: split the queue into work tracks, operator composes the plan.
3. **Work ONE item fully** (review with real verification, rebase, fix, test), then one
   question: what goes outward — act / "what might I say" / skip. Never batch outward
   actions across items unseen.
4. Verdicts ride in the question; deep evidence (coverage matrix, severity call) goes to a
   rich render mid-stream when the operator says "need more info".
5. **End-of-session state hygiene:** boards/labels/awaiting-fields set to where the ball
   ACTUALLY is (last actor vs. flag) — audited for ALL items, not just ones touched today.

### 2. Requirements interview (before building anything)

1. Question battery where each question states *why it matters* ("this is the single
   biggest cost lever…"). Options = genuinely different architectures/efforts, not flavors.
2. Elicit constraints the agent can't infer: budget, where it runs, who consumes it.
3. **Checkpoint gate:** end the interview with an explicit "design OK?" approve-to-proceed
   question (with an escape option) before any execution starts.
4. Build; return with a working artifact, not another round of questions.

### 3. Physical-world elicitation (CAD, electronics, anything with hands)

1. Agent states its guesses WITH uncertainty ("depths I had to guess").
2. Pick-all-that-apply rounds for what the operator can actually measure ("caliper numbers
   you can get") — partial answers are expected and fine.
3. Options encode observable states ("bare phones or in cases?"), not abstractions.
4. Re-render/regenerate after each measurement round; converge, don't restart.

### 4. Knowledge probing / drills (the question tool as quiz engine)

1. Real MCQs probing the operator's knowledge, one concept per question, plausible
   distractors — the tool IS the drill interface.
2. Pick-all-that-apply self-assessment ("which modules feel shakiest?") to weight the
   artifact being built.
3. Wrong answers shape the next round (drill deeper) rather than just being marked.

### 5. Strategy / meeting-prep coaching

1. Interview intent, politics, positioning — questions surface the trade-off the operator
   hasn't articulated yet ("would you take ownership of a subsystem?").
2. Options are stances, each with consequences spelled out in descriptions.
3. Output is a brief/playbook artifact; deep background goes to a rich render.

### 6. Destructive-action scoping (cleanup, migrations, shared estate)

1. Scan first; options enumerate CONCRETE safe paths verified by the scan ("all candidates
   below are free per my scan").
2. multiSelect for scope composition ("what do I clean up").
3. **Show exact item lists before anything irreversible** — a category checkbox is not
   consent for its contents.
4. Prefer reversible variants (backup-first, draft-first) as the recommended option.

### 7. Governance gates (memory, harness, process)

1. Small, single rounds: what gets persisted, what behavior changes.
2. Quote the exact text/rule that would be saved — approval applies to bytes, not vibes.
