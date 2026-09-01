# MUDU-060 graph — preliminary aircraft registration mark

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Owner requests preliminary mark"] --> B["Check aircraft and mark data"]
    B --> C["Decide"]
    C -->|Approved| D["Decision becomes final"]
    D --> E["Preliminary allocation is valid for one year"]
    E --> F["Owner may submit MUDU-061 registration"]
    C -->|Rejected or stopped| X["No preliminary allocation"]
```

Direct handoff:`MUDU-061` registration. Portfolio impact only:`MUDU-062`,
`MUDU-063` and `MUDU-091` share later aircraft or mark lifecycle data but are
not steps in MUDU-060.

## Open issues — not part of the process flow

- `GAP-060-005`:define how two simultaneous requests are prevented from reserving the same mark.
- `GAP-060-002`:reconcile the current form and attachment configuration with current law.
