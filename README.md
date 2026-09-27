# Executive Sales & Profitability Analytics Dashboard

An end-to-end business intelligence dashboard built in Power BI to evaluate three years of enterprise retail data. This solution analyzes performance metrics, profitability margins, and geographical distribution to deliver actionable strategic insights for management.

> **Development Environment & Workflow Note:** 
> This report was updated and customized using **Power BI Web Service on macOS**. Visual layout modifications, custom visual theme applications, and graph restructuring were executed directly through the cloud authoring interface.

---

## 📋 Project Summary

* **Primary File:** `Retail_Sales_Performance_Dashboard.pbix`
* **Coverage Period:** January 2021 – March 15, 2023
* **Total Revenue Analyzed:** $25.66M
* **Gross Margin:** 32.5% ($8.34M Gross Profit)
* **Core Focus:** Visual redesign, graph structure optimization, color theme standardization, and key performance metric visibility.

---

## 🛠️ Data Infrastructure & Transformation

The underlying architecture consolidates transactional data across multiple enterprise dimensions using Power Query ETL processing.

### Source Data Structure
| Data Entity | Records | Focus Area |
| :--- | :--- | :--- |
| **Sales (2021–2023)** | 10,889 | Transaction-level order logs (2023 partial through Mar 15) |
| **Product Catalog** | 101 | Unit cost, retail price structure, and product mapping |
| **Customer Directory** | 801 | Master customer profiles and historical orders |
| **Territories & Locations** | 74 | Regional demographics, household counts, and coordinates |
| **Sales Team** | 45 | Account rep identification and performance logs |
| **Target Allocation** | 97 | Monthly & annual territory performance targets |

### ETL & Data Cleanup Highlights
* **Table Union:** Combined annual sales transactions into a single core fact table (`Fact_Sales`).
* **Field Standardization:** Corrected naming conventions (`Sales Person ID` $\rightarrow$ `Salesperson ID`), set schema types, and removed null or duplicate Order IDs.
* **Feature Engineering:** Added derived metrics including Line Revenue, Customer/Location composite labels, and sort keys.
* **Data Cleansing:** Addressed location name discrepancies across target sheets, handled duplicate customer profiles, and accounted for partial-year metrics in 2023.

---

## 📐 Data Model Architecture

The data foundation utilizes an optimized **Star Schema** with single-direction 1-to-Many relationships to ensure fast visual query performance.

```text
       [Dim_Product]        [Dim_Customer]
             \                   /
[Dim_Date] ─── [Fact_Sales] ─── [Dim_Salesperson]
    │                │
    │          [Dim_Location]
    │                │
    └────── [Fact_Budget]

    
