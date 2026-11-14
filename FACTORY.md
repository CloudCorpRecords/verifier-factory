# FACTORY.md: The Five Seat Verifier Factory

A reusable multi agent factory for Band Desktop. One human dispatch goes
in. Checked, budgeted, recorded work comes out. This document is written
so another team can copy the factory, change nothing but the seat
configuration and the task, and run it on a different problem.

The factory's claim is simple: agent work fails in predictable ways.
Agents trust their own summaries, repeat each other's lookups, spend
without a ceiling, and forget why a conclusion changed. This factory
assigns one seat against each of those failures, plus one seat to run
the whole thing.

## Roster

Every seat runs as a Band Desktop agent seat driven by the Codex
harness (transport codex-app-server), model GPT-6-Luna. Effort is set per seat in its mandate.

| Seat | Owns | Never does |
|---|---|---|
| planner | Breaking the task down, routing work, accepting finished work | The work itself |
| researcher | Outside information, quoted from its sources | Building, accepting its own findings |
| verifier | Independent checking of every result | Fixing work, accepting unchecked work |
| budget-keeper | The one shared spending allowance and its ledger | The work it budgets for |
| historian | The record of what was believed, learned, and changed | Gathering, judging |

Mandates live beside this file in mandates/, one file per seat, named
after the seat. Copy them as they are. They describe how a seat works
and nothing about any particular problem, which is deliberate: a
mandate that names the problem cannot be reused, and this factory is
meant to be reused.

## The five design choices

1. **Coordination is a seat, not a side effect.** The planner builds
   nothing. Its whole job is decomposition, self-contained handoffs,
   and routing problems back to the seat that owns them. Bands without
   a coordinator seat drift into everyone doing a bit of everything
   and nobody owning the result.

2. **Production and checking are different seats with different
   incentives.** The verifier is rewarded for proving work wrong. It
   re-derives findings from original sources instead of trusting the
   summary it was handed, runs the checks itself at the reported
   revision, and rejects only with a specific reason and the evidence
   behind it. A rejection that changes nothing counts as a failed
   review, which keeps rejections honest instead of theatrical.

3. **All spending comes out of one allowance with one guard.** Seats
   check with the budget keeper before spending shared resources. The
   keeper keeps a public ledger, stops duplicate work by handing back
   the existing result, warns early when the allowance runs low, and
   refuses any step that would pass the cap. Cost becomes a property
   of the system, not a surprise at the end.

4. **Memory is a seat, not a log file.** The historian keeps two times
   separate for every conclusion: when the source says it became true,
   and when the band first learned it. Replaced conclusions are kept,
   not overwritten, and every change is recorded once, in order. Any
   later seat, or any later run, can reconstruct what the band believed
   at any point and why it changed.

5. **Handoffs are self-contained, always.** Seats see only messages
   addressed to them, so every handoff pastes the full requirements,
   the constraints, the repository path, and the checks to run. A
   pointer to another message is not a handoff. This is the rule that
   makes the room log a complete record of the work, readable by a
   judge, a teammate, or a future run, with no missing context.

## How a run flows

1. A human sends one dispatch: the complete task. That is the only
   human input. Seats never ask the human anything after it.
2. The planner confirms every seat is in the room, breaks the task
   into ordered pieces, and hands each piece to its owner.
3. The researcher gathers, quoting sources exactly, reporting
   disagreements instead of hiding them, checking spend first.
4. Builders (whichever seats the planner assigns the making to) build
   against the research, not against assumptions.
5. The verifier checks the result independently, at a named revision.
   Rejections go back through the planner to the owning seat, and the
   fixed work is checked again from the start.
6. The budget keeper posts the final ledger. The historian closes the
   record. Only then does the planner report the outcome: what was
   delivered, at what revision, with what evidence, at what cost.

## Adapting this factory to a new problem

- Keep all five mandates unchanged. If a mandate seems to need a
  problem specific line, the line belongs in the dispatch, not the
  mandate.
- Change only: the seat configuration (harness, model, effort), the
  shared allowance the planner states at the start of the run, and
  the checks named in the dispatch.
- For a small problem, the planner may assign building to the
  researcher. Do not merge the verifier into any producing seat: the
  independence is the point.
- For a larger band, add producer seats freely. Keep exactly one
  planner, one budget keeper, and one historian. Two ledgers or two
  records will disagree, and the factory's guarantees come from there
  being one of each.

## What this factory catches that a single agent does not

- A confident wrong answer, caught because a second seat re-derived
  it from the source and the sources disagreed.
- A duplicated spend, caught because one ledger sees every seat's
  plans, not just its own.
- A silent change, caught because the record keeps the old conclusion
  and the reason it was replaced.
- A lost requirement, caught because every handoff carries the full
  text and the verifier works from that text, not from memory.

## Run record (fill from the submitted run, do not edit the design above)

- Submitted run delivery time, first to last seat message: [ ]
- Human inputs after dispatch: none.
- Model spend: [ ] Research spend: [ ]
- Rejections that changed the work: [count and the clearest example]
- Final revision accepted by the verifier: [ ]
