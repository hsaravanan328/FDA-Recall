# FDA Recall Data Warehouse & Natural Language Analytics Engine

This project delivers a high-performance, normalized data warehouse for FDA product recall data spanning seven years (2018–2024), enabling scalable analytics, historical tracking, and intuitive natural-language search over regulatory data.

The system integrates robust SQL schema design, Python-based ETL pipelines, and NLP-driven semantic search to transform complex FDA recall datasets into an accessible, analytics-ready platform for both technical and non-technical users.

---

## 🔍 Project Overview

FDA recall data is complex, multi-source, and historically inconsistent, often published across XML and CSV formats with evolving company and product metadata.  
This project addresses those challenges by engineering:

- A fully normalized relational data warehouse (3NF / BCNF)
- Reliable ingestion of large-scale regulatory data (~500K records)
- Historical tracking using Slowly Changing Dimensions (SCD Type 2)
- A natural-language query interface powered by NLP similarity search

The result is a **regulatory-grade analytics backend** optimized for accuracy, performance, and usability.

---

## 📊 Data Used

### Source Systems
- **XML datasets:** Annual FDA recall files (2018–2024)
- **CSV datasets:** Consolidated FDA recall metadata with product, firm, classification, and distribution details

### Data Characteristics
- Semi-structured XML recall notices
- Structured CSV metadata
- Inconsistent naming conventions
- Repeated entities across time (companies, products, reasons)

### Scale
- ~500,000 recall-related records
- Multi-year historical coverage
- Multiple recall dimensions and hierarchies

---

## 🧠 Proposed Methodology

### 1. Schema Design & Normalization
- Designed a fully normalized relational model (3NF / BCNF)
- Separated dimensions for:
  - Company
  - Product
  - Product Type
  - Recall Reason
  - Recall Source
  - Identification & Dates
- Implemented bridge tables to resolve many-to-many relationships
- Enforced referential integrity via foreign keys

### 2. Slowly Changing Dimensions (SCD)
- **SCD Type 2** implemented for:
  - Company
  - Identification metadata
- Preserves historical accuracy for regulatory and trend analysis
- Enables point-in-time reporting and auditability

### 3. ETL Pipeline (Python + MySQL)
- XML parsing using `ElementTree`
- CSV ingestion using `pandas`
- Automated:
  - Data cleaning
  - De-duplication
  - Date normalization
  - Foreign key mapping
- Optimized inserts using:
  - Indexed lookups
  - Duplicate checks
  - Controlled batch operations

### 4. Analytical Layer (STAR Schema)
- Designed a STAR schema centered on `FACT_RECALL_SNAPSHOT`
- Supports fast analytical queries for:
  - Recall trends over time
  - Company recall history
  - Product-type risk analysis
  - Classification patterns

---

## 🔎 Natural Language Query Engine (NLP)

To make technical data accessible to non-technical users, a semantic search engine was implemented:

- Combined textual attributes into a unified document representation:
  - Company name
  - Product description
  - Recall reason
  - Product type
  - Source
- Vectorized text using **TF-IDF**
- Applied **cosine similarity** to rank relevant recall records
- Supports plain-English queries such as:
  - “Undeclared allergens in nut products”
  - “Salmonella recalls from dairy manufacturers”

This significantly reduces dependency on SQL knowledge while preserving analytical depth.

---

## 📈 Visualizations (To Be Added)

Planned visuals include:
- Entity Relationship Diagram (ERD)
- STAR Schema diagram
- ETL workflow
- Sample NLP query outputs

> Diagrams and screenshots will be added in a future update.

---

## 🧾 Concise Interpretation of Results

This system converts fragmented regulatory data into:
- A reliable, query-optimized analytics warehouse
- A historically accurate recall tracking system
- An intuitive semantic search interface for exploratory analysis

The combination of normalized storage and NLP-driven retrieval enables both **precision analytics and discovery-driven insights**.

---

## 💼 Business Outcome for Stakeholders

### Regulatory Analysts & Public Health Researchers
- Faster access to recall patterns
- Accurate historical trend analysis
- Improved root-cause investigation

### Data & Analytics Teams
- Clean, extensible data model
- BI-ready STAR schema
- Scalable ETL framework

### Non-Technical Users
- Natural-language access to complex regulatory data
- Reduced reliance on SQL or technical tooling

---

## 🛠️ Tech Stack

- **Database:** MySQL  
- **ETL & Processing:** Python  
- **Data Parsing:** XML (ElementTree), CSV (Pandas)  
- **Modeling:** 3NF, BCNF, STAR Schema  
- **NLP:** TF-IDF, Cosine Similarity  
- **Version Control:** Git & GitHub  

---
