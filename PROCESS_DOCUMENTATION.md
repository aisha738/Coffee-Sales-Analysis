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
```

### Conditional Logic (IF statements)

The raw data used abbreviations for product types (e.g., "Rob", "Exc").  
I created a new column `Coffee Type Name` using nested IF functions (or a lookup table) to expand these into readable categories:

- Robusta
- Excelsa
- Arabica
- Liberica

### Derived Columns

Created a **Sales** column to quantify revenue:

```excel
=[@Quantity] * [@Unit_Price]
```

## 3. Data Analysis (Pivot Tables)

I created a dedicated "Processing" sheet to house Pivot Tables.  
This keeps the raw data separate from the presentation layer (Dashboard), ensuring **data integrity**.

- **Time Series Analysis:** Grouped `Order Date` by Years and Months to track revenue trends.  
- **Categorical Segmentation:** Aggregated Sales by `Coffee Type` and `Roast Type`.  
- **Top N Analysis:** Sorted customer data by Sum of Sales (Descending) to isolate the **Top 5 customers**.

---

## 4. Visualization & Dashboard Design

### Chart Selection Strategy

- **Line Charts:** For timeline trends (visualizing volatility and seasonality).  
- **Bar Charts:** For categorical comparison (Country and Top 5 Customers).

### Interactivity (Slicers & Timelines)

- Inserted **Slicers** for `Loyalty Card`, `Roast Type Name`, and `Size`.  
- Inserted a **Timeline** for `Order Date`.

**Crucial Step:**  
Used "Report Connections" to link all slicers to every Pivot Table/Chart.  
This ensures that when a user filters by "United States", every chart on the dashboard updates simultaneously.

---

## 5. Challenges & Solutions

**Challenge:** The raw product codes were unintuitive for end-users.  
**Solution:** Mapped codes to full descriptions (e.g., `"M" -> "Medium"`) before visualizing.

**Challenge:** Ensuring the dashboard fits on a single screen (No scrolling).  
**Solution:** Designed a **grid layout**, hid gridlines, and collapsed the ribbon for a cleaner UI.
