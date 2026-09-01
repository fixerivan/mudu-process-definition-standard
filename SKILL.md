---
name: mudu-process-definition
description: Create, review, or update one strict human-and-machine-readable MUDU process definition per official catalogue process. Use for MUDU process Markdown, analyst/ministry scope definitions, source-to-process formalization, or validation before graph and Netgrif ingestion.
---

# MUDU process definition

Create or review exactly one `definition.md` for one official catalogue
process. Never combine a process family, neighbouring lifecycle stages,
technical helper nets, or several catalogue IDs into one definition.

Read all of [`STANDARD.md`](STANDARD.md) before starting. A new definition must
contain its metadata, human-readable quick overview, and complete structured
reference records.

## Language boundary

- Write all business and legal meaning in Slovak: names, purpose, actors,
  requirements, steps, outputs, gaps, questions, and diagram labels.
- Keep system syntax in English: YAML keys, stable IDs, enum values, and this
  instruction file.
- Preserve exact code, file, field, transition, and configured-value names and
  format them as code, for example `vehicle.xml` or `reason_delete`.
- Do not mix English engineering jargon into Slovak process sentences when a
  clear Slovak expression exists.
- Language never establishes authority. The explicit layer, status, and cited
  source do.

## Non-negotiable rules

- Preserve the official catalogue ID and name. Put a clearer working name in
  `canonical_name` without presenting it as an approved official renaming.
- Give every scope statement, requirement, actor, field, document, timing rule,
  invariant, step, output, integration, scenario, dependency, mapping, gap, and
  question a stable process-scoped ID. Never reuse an ID for another meaning.
- Keep `LAW`, `OFFICIAL_PROCEDURE`, `ACCEPTED_INTENT`,
  `CURRENT_IMPLEMENTATION`, `OBSERVATION`, and `PROPOSAL` separate. Code or EA
  can prove implementation facts, never business authority.
- A confirmed normative statement needs an exact source edition, locator,
  clause or range, and effective or observation date.
- Use `UNKNOWN`, `CONFLICT`, or `NOT_APPLICABLE` explicitly. Never fill a gap
  from inference, similarity, model confidence, or a neighbouring process.
- Keep proposals and open questions out of the confirmed contract. Only an
  authorized human may set `ACCEPTED_INTENT`, `ACCEPTED`, or `FROZEN`.
- Sections 2 through 15 describe business meaning. Put current EA, Petriflow,
  code, configuration, templates, and runtime findings in section 16 and never
  silently promote them into requirements.
- Preserve process boundaries with exact `MUDU-NNN` references. A change,
  renewal, cancellation, registration, appeal, or downstream process remains
  separate when it has its own catalogue ID.
- The LLM authoring the definition must directly read the cited sources and
  author every semantic record. Another model, similarity result, or generated
  text may suggest a candidate but cannot select identity, authority, or
  business meaning. Deterministic extraction and validation are allowed.
- Use a graph only as a dependency and conflict index. Review every material
  relationship against its sources; an edge is never authority by itself.
- A process diagram contains only a real trigger, activity, decision, state,
  outcome, or genuine handoff. List sources, shared entities, possible impacts,
  gaps, and questions separately below it with `DEP-*`, `GAP-*`, or `Q-*` IDs.
- A human must understand the process from the quick overview and diagram.
  Detailed tables provide precision and machine processing; they must not hide
  the basic meaning.

## Workflow

1. Identify the exact `MUDU-NNN`, official catalogue name, and boundaries with
   neighbouring processes.
2. Find and read all applicable law, official procedures and forms, accepted
   decisions, and current implementation evidence.
3. Reconcile law, official procedure, accepted intent, and implementation.
   Record conflicts instead of choosing silently.
4. Write the quick overview in plain Slovak, then fill every required section.
   Use an explicit `NOT_APPLICABLE` row with a reason where a section does not
   apply.
5. Check section order, table headers, enums, stable IDs, and every source
   reference against `STANDARD.md`.
6. Review the meaning of every claim, source completeness, direct dependencies,
   possible impacts, and already-authored connected definitions.
7. Create a small human-readable diagram of the real process flow. Keep issues
   and impacts outside the flow and reference their exact definition records.
8. Fix every error and save the result as `DRAFT / UNCONFIRMED`. Structural
   correctness does not confer business acceptance or prove implementation.

On revision, preserve stable record IDs, increment `definition_version`, append
section 18, and state the exact accepted change. Never rewrite accepted history
silently.
