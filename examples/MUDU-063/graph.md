# MUDU-063 graph — aircraft deregistration

`DRAFT / UNCONFIRMED`. This graph is a reading aid,not authority.

```mermaid
graph TD
    A1["Owner requests deregistration"] --> B["Check identity, reason, documents and fee"]
    A2["Authority starts case without a request"] --> B2["Prove legal ground and hear affected parties"]
    B --> C["Decide"]
    B2 --> C
    C -->|Final deregistration| D["Close current registration and preserve history"]
    D --> E["Issue deregistration certificate"]
    D --> F["Update current and historical register views"]
    D -.-> M91["Review impact on MUDU-091"]
    N["No SIS check for deregistration"] -.-> C
    G1["Open gap: form, reason and attachments"] -.-> B
    G2["Open gap: duplicate finality paths"] -.-> D
    G3["Open gap: temporal closure"] -.-> D
    G4["Open gap: outputs and tests"] -.-> E
```
