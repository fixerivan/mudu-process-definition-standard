---
name: mudu-process-review
description: Generate or revise a short Slovak MUDU process proposal for analyst or ministry review from available sources. Use before detailed Petriflow formalization or implementation.
---

# MUDU process review proposal

Generate one human-reviewable `definition.md` for one exact `MUDU-NNN` process.
Read all of [`STANDARD.md`](STANDARD.md) first.

## Goal

Research broadly but communicate narrowly. The reviewer must understand what
the process does, its boundaries, proposed flow, important rules, contradictions,
and the exact decisions requested from them.

Do not expose the internal evidence model, implementation inventory, graph
schema, or test architecture in the review proposal.

## Language boundary

- Write all process meaning, questions, and diagram labels in Slovak.
- Keep metadata keys, statuses, and stable IDs in English.
- Preserve an exact technical identifier only when the reviewer needs it to
  answer a question; format it as code.

## Method

1. Identify the exact catalogue process and read every relevant available
   source, including the current Petriflow and implementation evidence.
2. Separate supported facts, implementation observations, conflicts, and
   unanswered business questions.
3. Write the shortest complete explanation of the process purpose, trigger,
   boundary, and successful result.
4. Create a small top-level visual flow containing only business actions,
   decisions, states, and outcomes.
5. Include only rules that the reviewer needs to confirm.
6. Convert every unresolved contradiction into a concrete question. Never
   choose silently or use model confidence as authority.
7. End with an explicit checklist of what the reviewer must confirm or correct.
8. Keep the document `DRAFT / UNCONFIRMED` until an authorized human accepts it.

## Review quality gate

Before returning the proposal, verify that a reviewer can determine without
technical project knowledge:

- what starts the process;
- what the successful result is;
- what belongs and does not belong to it;
- who performs the important actions and decisions;
- what is disputed or unknown;
- exactly what response is requested.

If any answer requires reading the internal evidence dossier, rewrite the
proposal before returning it.
