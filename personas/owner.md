# Owner: the person accountable for the number

An archetype. Replace it with a real reader in `.claude/personas/` as soon as
you have one.

Example: a cost accountant who also runs operations and owns the product cost.

## Who they are

They are accountable for the number being right, and they are the one who has
to defend it to the business. That accountability is the whole persona: they
are not browsing, they are answering for something.

## What they know cold

- Their domain. For a cost owner: overhead pools, absorption, standard vs
  actual, over- and under-absorbed, what a rate is and why it moves.
- Their own operation. Which sites make what, which inputs are stale, what a
  plausible volume looks like.
- Their products. They will spot a wrong-looking figure faster than any
  validation rule will.

## What they do not know, and should never need to

- System internals. Internal IDs, record types, script deployments, queries. A
  bare `142` on screen means nothing to them and they will read it as a
  quantity.
- Why a technical constraint exists. "The field is 300 characters" is not a
  reason they can act on.
- How the thing is built. They judge it entirely on whether the number is right
  and whether they can prove it.

## What they come to a screen for

In order. Almost every visit is one of these:

1. **Is the number right?** And can I see enough of the working to believe it
   without asking anyone.
2. **What is blocking me, and what do I do about it?** Not what went wrong.
   What to do.
3. **Where does it stand?** Has this run been done, is it committed, is it safe
   to look at.
4. **What changed since last time, and why?** A rate moved 30% and they need
   the cause before someone asks them.

## How they read

- **Skims first, top left, then the biggest number.** If the biggest number on
  screen is not the one they came for, the screen is wrong.
- **Stops dead at anything they cannot interpret.** They do not experiment with
  buttons on a system that touches live figures. They stop and ask whoever
  built it, which is exactly the cost this review exists to avoid.
- **Trusts a shown calculation far more than a result.** `$4.6m × 40% ÷ 12,400
  min` earns belief. `$0.3681` alone does not.
- **Distrusts a number they cannot source.** "Where did that come from" is
  their most common question. Answer it on the screen.

## Rules for anything they will read

- Names, never IDs. Period names, account names, site names.
- Every error says what to do, in domain language, not system language.
- Never show a zero for something that has not been computed. They read `$0`
  as a finding and will act on it.
- Say plainly, before they press it, whether a button changes something live.
- Show the inputs behind every aggregate. They are the safeguard on the mapping
  and they know it.

## The tell

If a finding can only be described using a system term, it is a stall for the
owner. Whatever it is, they cannot act on it and will bring it to whoever
built the screen.
