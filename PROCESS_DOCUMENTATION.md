# Technical Process Documentation

## Project Scope
This document outlines the end-to-end technical procedure for creating the **Coffee Sales Dashboard**.  
The project simulates a real-world **Data Analyst workflow**: extracting raw data, cleaning and transforming it, building a data model, and creating visual narratives for decision-making.

---

## 1. Data Gathering & Schema Understanding

The dataset consisted of **three separate relational tables**.  
The first step was to understand the schema and relationships in order to merge them correctly.

### Tables Overview
- **orders (Fact Table)**  
  Contains transactional events  
  - Order ID  
  - Order Date  
  - Quantity  

- **customers (Dimension Table)**  
  Contains customer attributes  
  - Customer ID  
  - Customer Name  
  - Country  
  - Loyalty Status  

- **products (Dimension Table)**  
  Contains product specifications  
  - Product ID  
  - Coffee Type  
  - Roast Type  
  - Unit Price  

### Technical Decision
Instead of using **Power Query** (a more advanced option), Excel formulas were used to **denormalize** the data into a single master table.

**Rationale:**  
This approach demonstrates strong proficiency with **core Excel lookup functions**, which are essential for ad-hoc and real-world spreadsheet analysis.

---

## 2. Data Cleaning & Transformation (ETL)

Before analysis, a structured data quality and transformation process was carried out.

### Handling Missing Data
- Checked all columns for null or blank values.
- Verified that critical keys (**Customer ID** and **Product ID**) were populated across all records.

### Data Formatting
- Standardized **Order Date** into a recognizable Date format.
- Formatted **Unit Price** and **Sales** columns as Currency ($).

### Data Enrichment (XLOOKUP & INDEX-MATCH)
To enable analysis by customer attributes:
- Merged fields from the `customers` table into the `orders` table using **XLOOKUP**.

**Example Formula:**
```excel
=XLOOKUP([@CustomerID], customers[CustomerID], customers[CustomerName])
