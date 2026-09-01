# MUDU-060 graph — preliminary aircraft registration mark

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
flowchart LR
    A[Owner requests<br/>preliminary mark] --> B[Check aircraft and<br/>proposed mark data]
    B --> C[Decide]
    C -->|approved| D[Reserve preliminary mark<br/>for one year]
    D --> E[MUDU-061<br/>registration]
    C -->|rejected / stopped| X[No reservation]

    M[Registration mark<br/>and history] --- D
    G1[Open: atomic reservation<br/>and concurrency] -.-> D
    G2[Open: older form<br/>and attachment rules] -.-> B
```

Connected processes:`MUDU-061` registration,`MUDU-062` later change,
`MUDU-063` deregistration and `MUDU-091` Mode S/ELT impact.
