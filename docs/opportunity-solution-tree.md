## Outcome Map: SOC Risk Posture

```text
OUTCOME
└── SOC Manager assesses company risk posture in under 5 minutes
    using a single dashboard — without logging into multiple tools.

    │
    ├── OPPORTUNITY 1
    │   "I can't see threat trends — I'm always reacting, never anticipating"
    │   (SOC Manager pain)
    │   │
    │   ├── Solution A: Threat trend dashboard — attack type volume
    │   │   over time, by geography, by industry
    │   │
    │   └── Solution B: Weekly threat summary — top 5 rising threat
    │       categories with % change vs prior week
    │
    ├── OPPORTUNITY 2
    │   "I can't correlate our internal logs with global threat intel
    │   without a slow manual process"
    │   (Both personas — Manager sees risk, Analyst does the lookup)
    │   │
    │   ├── Solution A: Enrich BigQuery internal asset/log data with
    │   │   OTX indicators automatically in the Silver layer
    │   │
    │   └── Solution B: IOC match score per internal asset — so Analyst
    │       sees instantly if a company IP/domain is flagged globally
    │
    └── OPPORTUNITY 3
        "I have to log into 5 tools — I have no single source of truth"
        (SOC Manager pain)
        │
        ├── Solution A: Unified Power BI SOC dashboard — one view for
        │   threat trends, IOC matches, and team priority signals
        │
        └── Solution B: Severity scoring model in Gold layer — single
            composite risk score the Manager can act on immediately
