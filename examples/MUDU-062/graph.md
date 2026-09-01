# MUDU-062 graph — change of aircraft-register data

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Existing MUDU-061 registration"] --> B["Identify exact old and new values"]
    B --> C["Check applicant, documents and fee"]
    C --> D["Check aircraft and every engine in SIS"]
    D -->|Hit| X["Do not change register and notify Police"]
    D -->|Clear| E["Decide"]
    E -->|Approved and final| F["Apply only accepted changes and preserve history"]
    E -->|Rejected or stopped| Y["No register change"]
    F -->|Certificate changed| G["Replace certificate and return old one"]
    F -->|Certificate unchanged| H["Keep existing certificate"]
    G --> I["Update register views"]
    H --> I
```

Related processes:`MUDU-061` registration predecessor,`MUDU-063`
deregistration and `MUDU-091` Mode S/ELT impact.

## Open issues — not part of the process flow

- `GAP-062-004`:replace the seven loose UI choices with one complete typed old-to-new change.
- `GAP-062-006`:calculate the fee from the document actually changed.
- `GAP-062-005`:complete the real SIS integration.
- `GAP-062-013` and `Q-062-001`:define stale-data detection,effective dates and concurrent-change handling.
