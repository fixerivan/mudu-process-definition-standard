# MUDU-063 graph — aircraft deregistration

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A1["Owner or representative requests deregistration"] --> B["Check identity, reason, documents and fee"]
    A2["Authority starts case without a request"] --> B2["Prove legal ground and hear affected parties"]
    B --> C["Decide"]
    B2 --> C
    C -->|Approved| D["Deregistration reaches its accepted effective event"]
    C -->|Rejected or stopped| X["No deregistration"]
    D --> E["Close current registration and preserve history"]
    D --> F["Issue deregistration certificate"]
    E --> G["Update current and historical register views"]
```

No SIS check applies to deregistration. Predecessor:`MUDU-061` registration.
`MUDU-062` is a separate change process that may occur beforehand but is not a
required step. Portfolio impact only:`MUDU-091` Mode S/ELT.

## Open issues — not part of the process flow

- `GAP-063-001` and `GAP-063-002`:reconcile the form,reason choices and attachment rules with current law.
- `GAP-063-005`:replace the two competing finality paths with one idempotent effect.
- `GAP-063-006` and `Q-063-002`:define how owner,operator,lien,mark and component histories close.
- `Q-063-003`:define the exact ordering of legal effect,register update and certificate issuance.
- `GAP-063-009` to `GAP-063-012`:correct output templates and add process-specific tests.
