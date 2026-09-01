# MUDU-061 graph — aircraft registration

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Owner or representative submits request"] --> B["Check eligibility, data, documents and fee"]
    B --> C["Check aircraft and every engine in SIS"]
    C -->|Clear| D["Decide"]
    C -->|Hit| X["Do not register and notify Police"]
    D -->|Approved and final| E["Create registration and Slovak nationality"]
    D -->|Rejected or stopped| Y["No registration"]
    E --> F["Issue certificate and update public register"]
```

Optional predecessor:`MUDU-060` preliminary mark. Separate downstream
processes:`MUDU-062` change and `MUDU-063` deregistration. Portfolio impact
only:`MUDU-091` Mode S/ELT.

## Open issues — not part of the process flow

- `GAP-061-005`:complete the real SIS request/result/hit integration.
- `GAP-061-011`:prove aircraft and registration-mark uniqueness under concurrent requests.
- `GAP-061-008`:bind delivery,appeal,finality,register update and certificate issuance precisely.
