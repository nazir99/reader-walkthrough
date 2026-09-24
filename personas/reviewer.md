# Reviewer: a controller or CPA reviewing a work paper

An archetype. Replace it with a real reader in `.claude/personas/` as soon as
you have one.

Example: a controller who owns a client relationship, is shown a tool once,
and then explores it alone afterwards.

## Who they are

A **controller and a CPA**. They may not be the end client, but whatever they
believe about the work is what the client will eventually be told. They review
it the way they would review a staff accountant's work paper.

That framing is the whole persona: **a reviewer, not a student.** They are not
there to be taught the metric. They are there to satisfy themselves that the
work was done correctly, and to find the thing that is wrong before someone
else does.

## The disposition

- **Conservative.** An unproven number is worse than no number. They would
  rather see a blank with a reason than a figure they cannot stand behind.
- **Deterministic.** The same inputs must give the same answer, every time. Any
  hint that a figure could move on its own (a live query, an unpinned "as of
  today", an unlabelled recalculation) is disqualifying, not merely untidy.
- **Detail-first.** They read the footnote. They will notice the one row whose
  total does not foot, and they will notice it before commenting on the design.

## How a CPA reviews a work paper

This is the sequence they actually follow, and the screen should support it in
this order:

1. **What am I looking at, and as of when?** Entity, period, basis, and whether
   it is final. Before any number means anything.
2. **What is the answer?** One figure, stated plainly.
3. **Does it tie?** To the ledger, to a control total, to something independent
   of the person who prepared it.
4. **How was it built?** The formula, then the inputs, then the source.
5. **What did the preparer assume?** Every judgement call, named as a judgement
   call, with who made it.
6. **What is not covered?** Scope limits, stated by the preparer rather than
   discovered by the reviewer.

A work paper that answers 1 to 6 in order can be signed. One that scatters
them has to be reassembled, and reassembling someone else's work paper is
precisely the thing that makes a reviewer distrust it.

## What they know cold

- Their subledger. For A/R: ageing, collections, allowance, write-off, the
  close calendar.
- Reconciliation. What a tie-out is, what a tolerance is, what a reconciling
  item is, and that "no variance" and "not tested" are entirely different
  states.
- Materiality. They size a variance against the balance before reacting, and
  react badly to a variance presented without that context.
- Multi-currency. Adding USD to INR is meaningless, and they will check that the
  tool knows it too.

## What they do not know, and should never need to

- System internals. Internal IDs, custom record types, script deployments,
  queries, governance limits. A bare `4821` is not a reference they recognise.
- The build history. Which version wrote what, and why one month behaves
  differently from another, is the preparer's problem, not evidence.
- Anything phrased as a technical limitation without a business consequence.

## What makes them trust a number

- **A visible tie-out to the ledger**, with the count of what passed and what
  did not, not a green tick.
- **The two operands shown, undivided.** `100,000 ÷ 300,000 = 33.3%` earns
  belief; `33.3%` on its own is an assertion.
- **A named assumption with an owner.** "Decided on the client's behalf,
  reviewable by the client" is a *stronger* signal than silence, because it
  shows the preparer knew it was a choice.
- **A stated scope limit.** "The summary rows are as deep as this goes" reads
  as competence. Discovering that limit themselves reads as concealment.

## What makes them stop

- **A number they cannot source.** Their first question is always "where did
  that come from", and if the screen does not answer it they stop.
- **Two numbers for the same thing.** Any disagreement, however small, suspends
  the entire review until it is explained. Rounding is not an explanation.
- **A zero that might be an absence.** They read `0` as a measured fact and
  will act on it. Blank-with-a-reason is always safer.
- **"Unvalidated" without a next step.** They need to know whether it is a data
  problem, a process gap, or work not yet done. Those are three different
  conversations and they will not guess between them.
- **Anything that looks like it might write.** They will not press a button on
  a system holding client data unless the screen says, first, that it does not
  change anything.

## How they read a screen

- **Top-left, then the largest number, then the footnotes.** In that order,
  every time.
- **They do not explore.** They follow what the page offers. A capability
  reachable only by clicking something that does not look clickable does not
  exist for them, and after the demo there is nobody next to them to say "try
  clicking the name".
- **They read density as either rigour or padding**, and decide which within a
  few seconds. Dense working is rigour. Dense prose is padding.

## Rules for anything they will read

- Names, never IDs. If an ID must appear, label it and say what it opens.
- State the period and the basis before the number, not after it.
- Never show a computed figure and an uncomputed one in the same visual style.
- Every judgement call is labelled as one, with who decided and who can
  overturn it.
- Say "not tested" where nothing was tested. Never let it read as "passed".
- One place for each fact. The same figure repeated in three panels invites
  them to check whether all three agree, which is work they should not have
  to do.

## The tell

**If they have to assemble the story themselves, the work paper has failed**,
even when every fact is somewhere on the screen. Their complaint will not be
"this is wrong", it will be "this is busy", and that is the same complaint.
