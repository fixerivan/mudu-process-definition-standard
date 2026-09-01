# MUDU-062 graph — change of aircraft-register data

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Existing MUDU-061 registration"] --> B["Identify exact old and new values"]
    B --> C["Check applicant, documents and fee"]
    C --> D["Check aircraft and every engine in SIS"]
    D -->|Hit| X["Do not change register and notify Police"]
    D -->|Clear| E["Decide"]
    E -->|Approved| F["Apply change at its accepted effective event"]
    E -->|Rejected or stopped| Y["No register change"]
    F -->|Certificate changed| G["Replace certificate and return old one"]
    F -->|Certificate unchanged| H["Keep existing certificate"]
    G --> I["Update register views"]
    H --> I
```

This diagram shows the external request route. The separate ex-officio
correction route remains unresolved in `GAP-062-012`.

Predecessor:`MUDU-061` registration. Separate downstream process:`MUDU-063`
deregistration. Portfolio impact only:`MUDU-091` Mode S/ELT.

## Open issues — not part of the process flow

- `GAP-062-004`:replace the seven loose UI choices with one complete typed old-to-new change.
- `GAP-062-006`:calculate the fee from the document actually changed.
- `GAP-062-005`:complete the real SIS integration.
- `GAP-062-013` and `Q-062-001`:define stale-data detection,effective dates and concurrent-change handling.
- `GAP-062-012`:define the separate internal ex-officio correction route.
