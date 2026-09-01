# MUDU-060 graph — preliminary aircraft registration mark

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Owner requests preliminary mark"] --> B["Check aircraft and mark data"]
    B --> C["Decide"]
    C -->|Approved| D["Reserve mark for one year"]
    D --> E["Continue with MUDU-061 registration"]
    C -->|Rejected or stopped| X["No reservation"]
    M["Registration mark history"] -.-> D
    G1["Open gap: reservation concurrency"] -.-> D
    G2["Open gap: form and attachment rules"] -.-> B
```

Connected processes:`MUDU-061` registration,`MUDU-062` later change,
`MUDU-063` deregistration and `MUDU-091` Mode S/ELT impact.
