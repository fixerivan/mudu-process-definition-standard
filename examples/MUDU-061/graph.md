# MUDU-061 graph — aircraft registration

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
flowchart LR
    A[Owner submits<br/>registration request] --> B[Check eligibility,data,<br/>documents and fee]
    B --> C[SIS check:<br/>aircraft + every engine]
    C -->|clear| D[Decision]
    C -->|unambiguous hit| X[No registration<br/>notify Police]
    D -->|final| E[Create current registration<br/>and Slovak nationality]
    E --> F[Issue certificate<br/>and public projection]
    F --> G[MUDU-062<br/>change]
    F --> H[MUDU-063<br/>deregistration]

    M[Aircraft,owner,operator,lien,<br/>mark,engine,propeller] --- E
    G1[Open: SIS dispatch<br/>implementation] -.-> C
    G2[Open: mark uniqueness<br/>and concurrency] -.-> E
    G3[Open: output and<br/>finality state] -.-> F
```
