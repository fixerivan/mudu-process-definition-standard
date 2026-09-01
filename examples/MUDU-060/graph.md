# MUDU-060 graph — preliminary aircraft registration mark

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Owner requests preliminary mark"] --> B["Check aircraft and mark data"]
    B --> C["Decide"]
    C -->|Approved| D["Reserve mark for one year"]
    D --> E["Owner may submit MUDU-061 registration"]
    C -->|Rejected or stopped| X["No reservation"]
```

Connected processes:`MUDU-061` registration,`MUDU-062` later change,
`MUDU-063` deregistration and `MUDU-091` Mode S/ELT impact.

## Open issues — not part of the process flow

- `GAP-060-005`:define how two simultaneous requests are prevented from reserving the same mark.
- `GAP-060-002`:reconcile the current form and attachment configuration with current law.
