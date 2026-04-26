# Global Threat & Vulnerability Intelligence System

## Problem Statement
SOC teams face context-free alert fatigue. Thousands of alerts arrive
daily with no correlation to global threat intelligence, forcing manual
lookups across multiple tools with no unified view.

## Solution
A end-to-end data platform built on Microsoft Fabric that ingests global
threat intelligence from AlienVault OTX, correlates it against simulated
internal company logs, and delivers a unified SOC dashboard in Power BI.

## End Users
- SOC Manager — strategic risk oversight
- SOC Analyst — tactical IOC investigation

## Architecture
BigQuery (simulated logs) → Fabric Data Factory → OneLake (Bronze/Silver/Gold) → Power BI

## Tech Stack
- Microsoft Fabric (Lakehouse, Pipelines, Notebooks, Warehouse, Power BI)
- AlienVault OTX API
- Google BigQuery
- GitHub (version control + project management)
- draw.io (architecture diagrams)

## Project Methodology
- Scrum-lite: 2-week sprints
- DataOps: all pipeline and notebook changes version controlled
- Medallion architecture: Bronze → Silver → Gold
- Delivery tracked via GitHub Projects
