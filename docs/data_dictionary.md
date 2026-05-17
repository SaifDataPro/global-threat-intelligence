# Data Dictionary — Gold Layer

## fact_threat_events
One row per correlated event where an internal firewall log 
destination matched a known malicious OTX indicator.

| Column | Type | Description |
|---|---|---|
| log_id | string | Unique firewall log identifier |
| timestamp | timestamp | When the internal event occurred |
| internal_ip | string | Internal machine IP address |
| destination | string | External destination attempted |
| destination_type | string | domain / IPv4 / URL |
| action | string | allowed / blocked |
| bytes_transferred | integer | Data volume in bytes |
| department | string | Internal department |
| severity | string | low / medium / high |
| severity_score | integer | Numeric severity (1-3) |
| is_blocked | boolean | Whether firewall blocked the event |
| indicator_id | string | Matched OTX indicator ID |
| threat_key | string | FK to dim_threat |
| indicator_type | string | Type of matched IOC |
| indicator_key | string | FK to dim_indicator |
| date_key | integer | FK to dim_date (yyyyMMdd) |
| department_key | string | FK to dim_department |
| composite_risk_score | integer | Weighted risk score (0-10+) |
| risk_level | string | Critical / High / Medium / Low |

## dim_date
| Column | Type | Description |
|---|---|---|
| date | date | Calendar date |
| date_key | integer | Surrogate key (yyyyMMdd) |
| year | integer | Calendar year |
| month | integer | Month number (1-12) |
| month_name | string | Full month name |
| quarter | integer | Quarter (1-4) |
| week_of_year | integer | ISO week number |
| day_of_month | integer | Day of month |
| day_of_week | integer | Day number (1=Sunday) |
| day_name | string | Full day name |
| is_weekend | boolean | True if Saturday or Sunday |

## dim_threat
| Column | Type | Description |
|---|---|---|
| threat_key | string | PK — OTX pulse ID |
| threat_name | string | Name of threat campaign |
| tlp | string | Traffic Light Protocol classification |
| tlp_risk_score | integer | TLP numeric score (WHITE=1 to RED=4) |
| malware_families | string | JSON array of malware families |
| tags | string | JSON array of attack technique tags |
| targeted_countries | string | JSON array of targeted countries |
| author_name | string | OTX pulse author |
| indicator_count | integer | Total IOCs in this pulse |
| threat_first_seen | timestamp | When pulse was created |
| threat_last_modified | timestamp | When pulse was last updated |

## dim_indicator
| Column | Type | Description |
|---|---|---|
| indicator_key | string | PK — OTX indicator ID |
| threat_key | string | FK to dim_threat |
| indicator_value | string | Actual IOC (domain/IP/hash) |
| indicator_type | string | domain/IPv4/URL/FileHash etc |
| indicator_category | string | Network/Web/File/Vulnerability |
| is_active | boolean | Whether IOC is still active |
| is_correlation_target | boolean | Whether used for log matching |
| expiration | timestamp | When IOC expires |
| indicator_first_seen | timestamp | When IOC was first flagged |

## dim_department
| Column | Type | Description |
|---|---|---|
| department | string | Department name |
| department_key | string | PK — lowercase department name |
| risk_tier | string | High / Medium / Standard |
| risk_tier_score | integer | Numeric tier (High=3, Medium=2, Standard=1) |

## SQL Views
| View | Purpose | Answers Question |
|---|---|---|
| vw_threat_trends | Threat type volume over time | Q1 |
| vw_department_exposure | Department risk ranking | Q2 |
| vw_ioc_matches | IOC hits against internal logs | Q3 |
| vw_company_risk | Single company risk score | Q4 |
| vw_malware_families | Active malware families globally | Q5 |
