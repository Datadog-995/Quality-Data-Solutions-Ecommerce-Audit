## Quality Data Solutions: E-commerce Data Cleaning & Audit

This repository contains a comprehensive data cleaning pipeline for e-commerce order logs. It demonstrates how to transform raw, inconsistent data into a structured format using **OpenRefine**, **Python Pandas**, and **Google Sheets**, with all code and scripts provided to verify the cleaning steps.

### 📊 Repository Structure & Components

### 1. Raw Dataset (1-raw_ecommerce_dataset.tsv)
- **Status:** Untouched / Raw Input Data
- **Description:** The original, uncleaned e-commerce order logs containing missing values, inconsistent formatting, trailing spaces, and unstandardized inventory categories.

### 2. Cleaned Output (Quality_Data_Solutions_Ecommerce_Clean.csv)
- **Status:** Pristine / Production-Ready Output
- **Description:** The final polished dataset. All product names are standardized to Title Case, missing entries are resolved, whitespace is stripped, and formatting anomalies have been fully removed.

### 3. OpenRefine History (openrefine_cleaning_steps.json)
- **Status:** Programmatic Audit Footprint
- **Description:** Contains the exact, reproducible JSON data profiling steps and multi-column facet edits utilized during the text standardization phase.

### 🛠️ Data Cleaning Footprint

The core data integrity steps applied to this dataset include:
- **Text Standardization:** Applied whitespace trimming, merged inconsistent manual category entries into uniform product families, and applied Title Case styling.
- **Deduplication & Restoration:** Programmatically filled missing data points (such as parsing emails to restore blank Order IDs) and removed duplicated spacing.
- **Data Auditing:** Flagged and cleaned anomalous weight, quantity, and price entries (e.g., negative values) to ensure accurate downstream revenue calculations.
- **Formatting:** Restructured the file into a clean, strictly formatted CSV ready for direct database upload or BI tool ingestion.
