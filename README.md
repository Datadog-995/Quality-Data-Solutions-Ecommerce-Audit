# Quality Data Solutions: E-commerce Data Audit & Cleaning Pipeline

This repository contains an end-to-end data integrity and text standardization pipeline for e-commerce datasets, showcasing production-ready workflows for data auditing, text parsing, and anomaly flagging.

## 📊 Repository Structure & Components

### 1. [1-raw_ecommerce_dataset.tsv](1-raw_ecommerce_dataset.tsv)
* **Status:** Untouched / Raw Input Data
* **Format:** Tab-Separated Values (`.tsv`) displayed in a clean spreadsheet grid.
* **Description:** Contains the initial unverified e-commerce order logs, including text formatting inconsistencies, trailing spaces, missing fields, and unflagged negative financial transactions.

### 2. [CLEANED -Data__Ecommerce..csv](CLEANED%20-Data__Ecommerce..csv)
* **Status:** Pristine / Production-Ready Output
* **Format:** Comma-Separated Values (`.csv`)
* **Description:** The final polished output dataset generated after executing data cleaning and column audits. All categories are standardized to Title Case, whitespace is stripped, and valid transaction keys are restored.

### 3. [CLEAN - ECOMMERCE- STEPS copy.CSV](CLEAN%20-%20ECOMMERCE-%20STEPS%20copy.CSV)
* **Status:** Programmatic Audit Footprint
* **Format:** OpenRefine JSON Operation History
* **Description:** Contains the exact, reproducible JSON data profiling steps and multi-column facet edits utilized during the data scrubbing phase.

---

## 🛠️ Data Cleaning Footprint (OpenRefine History)

The core text standardization and data restructuring steps applied via OpenRefine include:
* **Order ID Restoration:** Programmatically filled blank order IDs by parsing and reformatting the user account prefix from customer emails: `grel:if(isBlank(value), "ORD-" + (10000 + cells["Customer Email"].value.split("@")[0].replace("customer","").toNumber()), value)`
* **Text Standardization:** Applied global `.trim()` configurations to isolate and remove trailing or double spaces across all `SKU` and `Category` blocks.
* **Facet Consolidation:** Executed mass edits on category groupings to merge duplicate terms (e.g., standardizing `Sports`, `SportsAndOutdoors`, and `Sports&outdoors` into a uniform **Sports & Outdoors** category).
* **Audit Anomaly Flagging:** Created automated multi-column flags (`Price_Audit_Flag` and `Quantity_Audit_Flag`) to target and isolate negative transactional values (`value < 0`).
