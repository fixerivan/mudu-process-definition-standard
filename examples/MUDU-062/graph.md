# MUDU-062 graph — change of aircraft-register data

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A["Existing MUDU-061 registration"] --> B["Identify exact old and new values"]
    B --> C["Check applicant, documents and fee"]
    C --> D["Check aircraft and every engine in SIS"]
    D -->|Clear| E["Decide"]
    E -->|Final| F["Apply only accepted changes and preserve history"]
    F -->|Certificate changed| G["Replace certificate and return old one"]
    F --> H["Update public and private register views"]
    F --> I["Deregistration remains MUDU-063"]
    G1["Open gap: incomplete typed change"] -.-> B
    G2["Open gap: fee routing"] -.-> C
    G3["Open gap: SIS implementation"] -.-> D
    G4["Open gap: stale data and effective dates"] -.-> F
```
