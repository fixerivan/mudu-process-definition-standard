# MUDU Process Definition Format v1

## Purpose

This format defines one durable Markdown contract for one official MUDU
catalogue process. It must remain readable by ministry experts and analysts and
deterministically parseable for graph publication,Netgrif realization,test
generation,impact analysis and version comparison.

The document is a source-backed business definition. It is not a process-family
report,free-form analyst essay,current-code description,or evidence of business
acceptance/runtime conformance.

## File identity

Canonical path:

```text
process-definitions/MUDU-NNN/definition.md
```

There is exactly one current definition per official catalogue ID. Historical
versions remain in Git. Related catalogue processes are referenced by ID and
never embedded as additional lifecycles.

The source-clean files under `examples/` in this public repository are review
copies. A governed portfolio may keep its current definitions under the
canonical path above.

## Required front matter

The file begins with YAML front matter containing these keys in this order:

```yaml
---
schema: mudu-process-definition/v1
process_id: MUDU-NNN
catalogue_id: "NNN"
catalogue_name: "Official catalogue name"
canonical_name: "Current legally precise name"
definition_version: 0.1.0
definition_status: DRAFT
authority_status: UNCONFIRMED
source_selection: UNKNOWN
implementation_conformance: NOT_VERIFIED
formal_verification: NOT_RUN
language: sk
source_baseline_date: YYYY-MM-DD
supersedes: null
related_processes: []
---
```

`catalogue_id` is a quoted three-digit string. Never write an unquoted value
such as `063`: YAML 1.1 readers can interpret it as octal and display `51`.

Enums:

- `definition_status`: `DRAFT`, `REVIEW`, `ACCEPTED`, `FROZEN`, `SUPERSEDED`.
- `authority_status`: `UNCONFIRMED`, `ANALYST_CONFIRMED`,
  `MINISTRY_CONFIRMED`.
- `source_selection`: `SELECTED`, `PARTIAL`, `CONFLICT`, `UNKNOWN`.
- `implementation_conformance`: `NOT_VERIFIED`, `MISSING`, `PARTIAL`,
  `CONFORMANT`, `NONCONFORMANT`.
- `formal_verification`: `NOT_RUN`, `PARTIAL`, `PASS`, `FAIL`.

Only authorized human acceptance may set `ACCEPTED`, `FROZEN`,
`ANALYST_CONFIRMED` or `MINISTRY_CONFIRMED`.

Use `NONCONFORMANT` only when at least one exact implementation mismatch is
recorded in sections 16 or 17. Use `PARTIAL` when only part of the implementation
was evaluated,and `NOT_VERIFIED` when no exact conformance evaluation exists.

## Claim semantics

Every substantive table row identifies both a layer and a status.

Layers:

- `LAW`: binding EU/national provision or directly controlling legal act.
- `OFFICIAL_PROCEDURE`: current authority procedure,form,methodology or
  published operational instruction.
- `ACCEPTED_INTENT`: explicit authorized analyst/ministry decision.
- `CURRENT_IMPLEMENTATION`: observed EA,Petriflow,code,configuration,template or
  runtime behavior.
- `OBSERVATION`: source-backed contextual fact that is not itself normative.
- `PROPOSAL`: unaccepted design suggestion.

Statuses:

- `CONFIRMED`: directly supported by the cited source at the stated layer.
- `PROPOSED`: awaiting an authority decision.
- `CONFLICT`: applicable sources disagree or implementation contradicts intent.
- `UNKNOWN`: evidence is insufficient.
- `NOT_APPLICABLE`: section/record does not apply,with a reason.

Modalities are `MUST`, `MUST_NOT`, `SHOULD`, `MAY`, and `DESCRIPTIVE`.
`MUST`/`MUST_NOT` may be `CONFIRMED` only with a cited `LAW`,
`OFFICIAL_PROCEDURE`, or `ACCEPTED_INTENT` source.

## Stable identifiers

Use three-digit catalogue IDs and monotonically increasing three-digit record
numbers:

```text
SCP-060-001  scope/boundary
REQ-060-001  normative requirement
ACT-060-001  actor/role
PRE-060-001  precondition/input
FLD-060-001  data field
DOC-060-001  document/attachment
TIM-060-001  deadline/time rule
FEE-060-001  fee rule
RULE-060-001 invariant/decision rule
STEP-060-001 process step
OUT-060-001  output/effect/end state
INT-060-001  integration
NOT-060-001  notification
ALT-060-001  alternative/error/remedy
DEP-060-001  dependency/impact edge
AC-060-001   acceptance scenario
MAP-060-001  EA/Petriflow/code mapping
GAP-060-001  implementation/evidence gap
Q-060-001    unresolved question
DEC-060-001  pending/accepted decision
SRC-060-001  source revision
```

IDs are permanent. A changed meaning receives a new ID;removed accepted records
remain in Git history and the definition change log.

## Required sections and tables

All sections appear exactly once and in this order. Do not omit empty sections;
use one explicit `NOT_APPLICABLE` row.

### 1. Identita a stav

```text
| Pole | Hodnota |
```

Required fields: `Katalógové ID`, `Katalógový názov`, `Kanonický názov`,
`Vecný gestor`, `Typ procesu`, `Definičný stav`, `Autorita`, `Jazyk`.

Process types include `APPLICATION_DECISION`, `NOTIFICATION`,
`REGISTRY_MUTATION`, `EXAMINATION`, `CERTIFICATION`, `APPROVAL`, `STATEMENT`,
`SUPERVISION`, `INTERNAL`, `INTER_AUTHORITY`, and `OTHER`.

### 2. Účel, spúšťač a hranice

```text
| ID | Typ | Tvrdenie | Vrstva | Stav | Zdroje |
```

Use `PURPOSE`, `TRIGGER`, `IN_SCOPE`, or `OUT_OF_SCOPE`. Explicitly separate
adjacent catalogue processes.

### 3. Autorita a právny základ

```text
| ID | Modalita | Normatívne pravidlo | Vrstva | Stav | Zdroje |
```

Every legal statement cites exact provisions. Do not use a bibliography-only
claim.

### 4. Aktéri a oprávnenia

```text
| ID | Aktér | Typ | Oprávnenie a zodpovednosť | Vrstva | Stav | Zdroje |
```

Distinguish applicant,data subject,representative,processor,approver,other
authority and system actor.

### 5. Vstupy a predpoklady

```text
| ID | Podmienka alebo vstup | Povinnosť | Vrstva | Stav | Zdroje |
```

Use `REQUIRED`, `CONDITIONAL`, `OPTIONAL`, or `NOT_APPLICABLE`.

### 6. Údaje formulára

```text
| ID | Údaj | Typ | Kardinalita | Zdroj/hodnota | Validácia | Vrstva | Stav | Zdroje |
```

Cardinality is explicit (`1`, `0..1`, `1..*`, `0..*`). Conditionality references
a stable rule ID. A group field may be used when the controlling source defines
a structured identity group.

### 7. Dokumenty a prílohy

```text
| ID | Dokument/príloha | Povinnosť | Forma | Vrstva | Stav | Zdroje |
```

Do not copy attachments from a related process. Distinguish legal requirements,
official forms and current implementation configuration.

### 8. Poplatky, lehoty a časové pravidlá

```text
| ID | Typ pravidla | Hodnota | Spúšťač/začiatok | Vrstva | Stav | Zdroje |
```

Separate statutory deadlines,operational targets,validity,pauses,renewals and
fees. Never omit the start event.

### 9. Rozhodovacie pravidlá a invarianty

```text
| ID | Modalita | Pravidlo/invariant | Vrstva | Stav | Zdroje |
```

Include uniqueness,mutual exclusion,predecessor,finality,side-effect and
concurrency invariants required for formalization.

### 10. Procesný tok

```text
| ID | Poradie | Stav pred | Činnosť | Aktér | Podmienka | Stav po | Vrstva | Stav | Zdroje |
```

Steps describe the authoritative business flow. Implementation-only steps are
labelled accordingly. Branches reference `RULE-*`;ordinary ordering must not be
invented from code layout.

### 11. Výstupy, právne účinky a koncové stavy

```text
| ID | Typ | Výstup/účinok | Právoplatnosť/platnosť | Vrstva | Stav | Zdroje |
```

Separate documents,decisions,certificates,register mutations,publications,
notifications and negative outcomes. Generation time is not automatically the
legal-effective time.

### 12. Integrácie a notifikácie

```text
| ID | Typ | Systém/príjemca | Účel/obsah | Kritickosť | Vrstva | Stav | Zdroje |
```

Use `INTEGRATION` or `NOTIFICATION`. A configured adapter is not proof that an
external call succeeds.

### 13. Alternatívne, chybové a opravné scenáre

```text
| ID | Spúšťač | Očakávané správanie | Koncový stav | Vrstva | Stav | Zdroje |
```

Cover missing evidence,invalid data,negative decision,interruption,stopping,
appeal/review,external failure,retry and concurrency where applicable.

### 14. Väzby na iné procesy a dopad zmien

```text
| ID | Smer | Proces/artefakt | Typ väzby | Dopad | Vrstva | Stav | Zdroje |
```

Use exact process IDs and `PREDECESSOR`, `SUCCESSOR`, `DEPENDS_ON`, `PRODUCES_FOR`,
`SHARED_ENTITY`, `SHARED_INTEGRATION`, `SHARED_OUTPUT`, or `OUT_OF_SCOPE`.

### 15. Akceptačné scenáre

```text
| ID | Given | When | Then | Pokrýva | Stav |
```

Scenarios reference `REQ`, `RULE`, `STEP`, `OUT`, `ALT`, and `INT` IDs. They are
reviewable business examples and later become API/data/Playwright/formal oracles.

### 16. Mapovanie na EA, Petriflow a kód

```text
| ID | Vrstva implementácie | Artefakt | Presná väzba | Stav | Zdroje |
```

Record exact EA GUID/Object ID,Petriflow file/process/transition/field,source
path/commit,configuration row,output template and runtime proof. This section is
descriptive and cannot authorize sections 2-15.

### 17. Medzery, konflikty a otvorené rozhodnutia

```text
| ID | Typ | Otázka/konflikt | Potrebné rozhodnutie | Vlastník | Stav | Zdroje |
```

Use `SOURCE_CONFLICT`, `INTENT_QUESTION`, `IMPLEMENTATION_GAP`, `EVIDENCE_GAP`, or
`PROPOSAL`. No unresolved item is hidden in narrative prose.

### 18. Schválenie a história zmien

```text
| Verzia | Dátum | Zmena | Autorita | Stav |
```

Record every definition version. Acceptance identifies the human authority and
the exact accepted Git/blob identity through the surrounding governed workflow.

### 19. Register zdrojov

```text
| ID | Typ | Názov/verzia | Lokátor | Ustanovenie/rozsah | SHA-256 | Účinnosť/pozorovanie |
```

Source types include `LAW`, `OFFICIAL_PROCEDURE`, `OFFICIAL_FORM`,
`ACCEPTED_DECISION`, `EA`, `SHAREPOINT`, `KNOWLEDGE_TRANSFER`, `PETRIFLOW`,
`SOURCE_CODE`, `CONFIGURATION`, `OUTPUT_TEMPLATE`, `RUNTIME_EVIDENCE`, and
`SOURCE_DRAFT`.

Every source reference used elsewhere must exist here. A missing hash is
`UNKNOWN`,never blank. URLs alone do not identify a source revision.

A source-clean public copy may replace a private locator and hash with
`UNKNOWN`,but it must say that the private evidence was not redistributed. Such
a copy is review material,not independently reproducible implementation evidence.

## Versioning and freeze

- Patch: clarification or evidence correction without changed required behavior.
- Minor: new accepted requirement,branch,field,outcome or mapping.
- Major: incompatible process contract or identity boundary.
- `FROZEN` means the exact accepted version is the baseline. Later change is a
  new version with an explicit delta,impact closure and fresh proof.
- `SUPERSEDED` points to successor definitions but remains readable for history.

## Completeness boundary

Passing structural validation means only that the document follows this
format. It does not prove that sources are current,semantics are correct,the
ministry accepted the definition,Netgrif implements it,or formal/runtime tests
pass. Those states remain explicit in front matter and evidence.
