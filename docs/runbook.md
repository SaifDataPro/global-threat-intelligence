# Runbook — Global Threat & Vulnerability Intelligence System

## Platform Overview
End-to-end threat intelligence platform built on Microsoft Fabric.
Two data sources → Bronze → Silver → Gold → Power BI SOC Dashboard.

## Scheduled Jobs
| Pipeline | Schedule | Notebook | 
|---|---|---|
| pl_bronze_otx_ingestion | Daily 06:00 IST | nb_bronze_otx_ingestion |
| pl_bronze_bigquery_ingestion | Daily 06:30 IST | nb_bronze_bigquery_ingestion |

## First Steps When Something Looks Wrong
1. Go to **Fabric Monitoring Hub**
2. Check status of last pipeline runs
3. If FAILED — click the run to see error details
4. Check `pipeline_log` table for last successful run
5. Check `data_quality_log` table for failed checks

## Common Failure Scenarios

### Pipeline Failed — OTX API
**Symptom:** `pl_bronze_otx_ingestion` shows Failed in Monitoring Hub
**Likely cause:** OTX API key expired or rate limit hit
**Fix:** 
- Verify OTX API key is still valid at otx.alienvault.com
- Check API rate limits — free tier allows limited calls per day
- Re-run notebook manually once fixed

### Pipeline Failed — BigQuery
**Symptom:** `pl_bronze_bigquery_ingestion` shows Failed in Monitoring Hub
**Likely cause:** GCP service account key expired or permissions changed
**Fix:**
- Verify service account key file is still present in Lakehouse Files
- Check GCP IAM permissions for the service account
- Re-run notebook manually once fixed

### Dashboard Showing Stale Data
**Symptom:** SOC Manager reports data hasn't updated
**Check:**
- Monitoring Hub — did pipelines run successfully today?
- pipeline_log table — what was the last successful run timestamp?
- Semantic model — trigger manual refresh if pipelines succeeded

### Data Quality Check Failed
**Symptom:** data_quality_log shows FAIL status
**Check:**
- Which table and which check failed?
- Row count drop — did source data stop arriving?
- Null check failure — did schema change at source?

## Manual Re-run Steps
1. Go to workspace `global-threat-intelligence-dev`
2. Open the failed notebook
3. Run all cells in order
4. Verify pipeline_log shows SUCCESS
5. Trigger semantic model refresh manually

## Key Tables for Diagnosis
| Table | Purpose |
|---|---|
| pipeline_log | Every pipeline run — status, rows loaded, timestamp |
| data_quality_log | Every quality check run — pass/fail per check |
| bronze_otx_pulses | Last ingested OTX data |
| silver_firewall_logs | Last transformed firewall data |
| fact_threat_events | Correlated threat events — Gold layer |
