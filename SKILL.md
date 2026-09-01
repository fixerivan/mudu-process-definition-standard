---
name: mudu-process-definition
description: Create, review, or update one strict human-and-machine-readable MUDU process definition per official catalogue process. Use for MUDU process Markdown, analyst/ministry scope definitions, source-to-process formalization, or validating a process definition before graph/Netgrif ingestion.
---

# MUDU process definition

Create exactly one `definition.md` for one official catalogue process. Never
merge a process family, lifecycle neighbours, technical helper nets, or multiple
catalogue IDs into one definition.

Before authoring or reviewing,read [the normative format](STANDARD.md). Start a
new definition from its required front matter and 19 table definitions.

## Non-negotiable rules

- Preserve the official catalogue ID and name; record corrected legal
  terminology separately.
- Give every scope statement, requirement, actor, field, document, timing rule,
  invariant, step, output, integration, scenario, dependency, mapping and gap a
  stable process-scoped ID. Never reuse an ID for different meaning.
- Separate `LAW`, `OFFICIAL_PROCEDURE`, `ACCEPTED_INTENT`,
  `CURRENT_IMPLEMENTATION`, `OBSERVATION` and `PROPOSAL`. Code or EA can prove
  implementation facts, never business authority.
- A confirmed normative statement needs exact source references. Cite the
  edition, locator, clause/page/range, and effective or observation date.
- Use `UNKNOWN`, `CONFLICT` or `NOT_APPLICABLE` explicitly. Never fill a gap by
  inference, similarity, model confidence, or copying an adjacent process.
- Keep proposals and open questions out of the confirmed contract. Ministry or
  analyst approval is required before `ACCEPTED_INTENT`, `ACCEPTED` or `FROZEN`.
- A process definition describes business intent and evidence. Keep current EA,
  Petriflow, code, configuration and runtime findings in section 16 and never
  silently turn them into requirements.
- Preserve cross-process boundaries with exact `MUDU-NNN` references. A change,
  renewal, cancellation, registration, appeal or downstream process remains a
  separate definition when it has its own catalogue ID.
- The LLM performing the task must directly read the sources and author every
  semantic record. Another model,similarity,embeddings or generated text may
  suggest evidence but cannot select identity,authority or business meaning.
  Deterministic extraction,query and validation are allowed.
- Use a graph as a dependency/conflict index,never authority. Account for every
  direct material dependency and manually inspect every shared item that may
  create an indirect impact.
- A human process diagram contains only actual execution semantics:trigger,
  activity,decision,state,outcome and a genuine process handoff. Never draw a
  source,shared entity,impact candidate,gap,conflict or unknown as if it were a
  process step. List those separately below the diagram and reference their
  exact `DEP-*`,`GAP-*` or `Q-*` IDs.

## Workflow

1. Identify the exact `MUDU-NNN`. If the project has a portfolio ledger,record
   it as `IN_RESEARCH`. Inspect its complete typed graph neighbourhood.
2. Identify and manually read the exact authoritative source universe.
3. Reconcile law,official procedure/form,accepted intent and current
   implementation; record conflicts rather than choosing silently.
4. Fill every mandatory section. Use an explicit `NOT_APPLICABLE` row rather
   than omitting a section.
5. Check every required section,table header,record namespace,source reference
   and enum against `STANDARD.md`.

6. Manually perform semantic,source,direct-dependency,potential-impact and
   reciprocal connected-definition review.
7. Fix every structural error before graph or Netgrif ingestion. Structural
   correctness does not confer business acceptance or prove semantic correctness.
8. Register the DRAFT as non-authoritative graph review evidence,update the
   ledger and commit the process-specific increment.

On revision, preserve stable record IDs, increment `definition_version`, append
section 18, and identify the exact authorized delta. Never rewrite accepted
history silently.
