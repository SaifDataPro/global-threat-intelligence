# Decision Log

| # | Date | Decision | Reasoning | Alternatives Considered |
|---|------|----------|-----------|------------------------|
| 1 | [today] | AlienVault OTX as threat intel source | Free API, rich IOC data, real-world SOC relevance | VirusTotal (limited free tier), MISP (self-hosted complexity) |
| 2 | [today] | BigQuery as simulated internal log store | Already on trial, mirrors real enterprise pattern | Static CSV (less realistic), Azure SQL (additional cost) |
| 3 | [today] | Medallion architecture (Bronze/Silver/Gold) | Industry standard for Fabric/Lakehouse, clear separation of concerns | Data Vault (overkill for this scale) |
