---
name: mudu-process-definition
description: Generate or revise one complete layered Slovak MUDU process definition in Markdown, combining a human acceptance layer with the detailed structured layer required for Petriflow, impact analysis, tests and verification.
---

# Layered MUDU process definition

Create or revise exactly one `definition.md` for one exact `MUDU-NNN`. Read all
of [`STANDARD.md`](STANDARD.md) before starting.

## Required result

The same Markdown file contains:

- a visible human acceptance layer;
- a collapsed detailed structured layer;
- a prominent visible warning that the complete definition continues below;
- an explicit bold disclosure label beginning with `KLIKNITE SEM`;
- stable IDs shared between both layers;
- no unresolved contradiction hidden as a confirmed rule.

The human layer never replaces or discards detail. The detailed layer never
silently changes the meaning presented for human acceptance.

## Language

- Process meaning, questions and diagram labels are Slovak.
- Metadata keys, statuses and stable IDs are English system syntax.
- Exact technical identifiers are preserved as code only where needed.

## Workflow for an existing process

1. Read all available law, forms, prior analysis, EA, Petriflow, code,
   configuration, outputs and runtime evidence.
2. Build the detailed structured layer and identify source conflicts,
   implementation mismatches and missing decisions.
3. Generate the human layer from that detail: purpose, boundaries, top-level
   flow, important rules, concrete questions and requested confirmation.
4. Add the required visible warning and bold `KLIKNITE SEM` disclosure before
   the collapsed detail; never rely on the browser’s small default arrow alone.
5. Check that every human rule/question references existing stable IDs in the
   detailed layer.
6. Ask the analyst only questions requiring human business authority; update
   both layers after every answer.
7. Keep the file `DRAFT / UNCONFIRMED` until an authorized human accepts the
   exact version.
8. After acceptance, use the complete file to create the actual Petriflow model,
   impact graph, tests and proof artifacts.

## Workflow for a new process or change

Start from the analyst’s intent and ask targeted questions until both layers are
complete. For a change, preserve stable IDs, show the human-readable difference,
recompute affected processes and require renewed acceptance before updating
Petriflow.

## Human layer quality gate

The reviewer must be able to determine without reading the complete detail:

- what starts the process and what successful completion means;
- what belongs and does not belong to it;
- the main actions, decisions and outcomes;
- the important rules;
- what remains disputed;
- exactly what response is requested.

## Detailed layer quality gate

Validate every required section, table, enum, ID and source reference. Current
implementation evidence may prove what exists, but never business authority;
graph edges, similarity and model confidence are never acceptance.
