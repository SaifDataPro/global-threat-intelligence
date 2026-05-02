# Decision Log

| # | Date | Decision | Reasoning | Alternatives Considered |
|---|------|----------|-----------|------------------------|
| 1 | [26 April 2026] | AlienVault OTX as threat intel source | Free API, rich IOC data, real-world SOC relevance | VirusTotal (limited free tier), MISP (self-hosted complexity) |
| 2 | [26 April 2026] | BigQuery as simulated internal log store | Already on trial, mirrors real enterprise pattern | Static CSV (less realistic), Azure SQL (additional cost) |
| 3 | [26 April 2026] | Medallion architecture (Bronze/Silver/Gold) | Industry standard for Fabric/Lakehouse, clear separation of concerns | Data Vault (overkill for this scale) |
| 4 | [2 May 2026] | Excluded is_malicious_seed from bronze_firewall_logs | Column is synthetic helper only, not representative of real source data. Bronze mirrors real-world source schema. | N/A |
| 5 | [2 May 2026] | Bronze arrays stored as strings | tags, malware_families, targeted_countries from OTX are JSON arrays stored as raw strings in Bronze. Parsing happens in Silver only. | Parse in Bronze (rejected — violates raw landing principle) |
| 6 | [2 May 2026] | Separate Bronze tables per source | bronze_otx_pulses, bronze_otx_indicators, bronze_firewall_logs kept separate. Combining happens in Silver. | Single combined table (rejected — loses source lineage) |
