# Random Number Generator — The Art of the Possible

*The first working n8n workflow in this project — and a small, honest metaphor for a much bigger pattern.*

## Why this workflow, of all things

On its face, this is about as simple as automation gets: click a button, and a text file fills up with a fresh random two-digit number every five seconds, for up to fifteen minutes, then it stops on its own. There's no machine learning here, no real data, no real stakes.

But the *shape* of the workflow is the point, not the random number. Strip away what each step literally does, and what's left is a pattern that shows up everywhere serious automation and AI systems get built: something produces a signal, something processes or evaluates that signal, and something decides what happens next — with a hard limit on how long any of it runs unsupervised. Swap "random number" for a live sensor reading, a model's prediction, or a market signal; swap the five-second wait for however long it takes a model to run inference; and the workflow's skeleton doesn't change at all.

That's the art of the possible here: not what it computes, but what it's *shaped like*.

## Mapping the metaphor

| In this workflow | Stands in for |
|---|---|
| Manual Trigger | An event or request that kicks off a process |
| Generate Random (00–99) | A signal being produced — in a real system, a live measurement, a model's output, or an inference result |
| Wait (5 seconds) | The processing step itself — where a real system might be running a model, doing analysis, or computing a forecast |
| If (elapsed < 15 min?) | A decision point — a guardrail, a policy, a human-defined threshold deciding whether the loop continues |
| Loop-back on "true" | Continuous monitoring — the system keeps checking, not just running once |
| Auto-stop on "false" | Discipline — nothing runs unsupervised forever by design, not because someone remembered to turn it off |

That If node earns more attention than its one line of logic suggests. It's a symbolic, human-authored rule sitting downstream of something probabilistic — which is, in miniature, the core idea behind pairing a learned or statistical component with an explicit, legible rule: let the system produce and process a signal on its own, but keep a hard, human-defined boundary on what it's allowed to do without a check. Human-centered AI design leans hard on exactly this shape — not "the system does everything," but "the system does the middle part, and an explicit rule decides the edges."

## What it actually builds

![Random Number Generator workflow running in the n8n editor — Manual Trigger through Init, Generate Random, Convert to File, Write File to Disk, Wait, and If, with a loop-back connection from If's true output to Generate Random](../docs/images/random-number-generator-workflow.png)

Manual Trigger → capture a start time → generate a random two-digit number → convert it to a text file → write it to disk, overwriting the same file each cycle → wait five seconds → check whether fifteen minutes have passed since the start. If not, loop back and do it again. If so, stop — on its own, no one needing to remember to.

The full node-by-node build — every setting, every expression, and the one real gotcha hit along the way (an n8n 2.x file-access default) — is documented in [`n8n_how.md`](../n8n_how.md).

## What's next

This is the first of what should be a small family of workflows following the same shape with real substance behind each step: real data instead of a random number, a real model instead of a five-second wait, a real decision policy instead of a fixed 15-minute cap. The next one — a finance/stock forecasting workflow — is exactly that evolution.
