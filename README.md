# Coffee Sales Analysis Project

## Project Overview
This project involves the analysis of a retail coffee sales dataset to identify key business trends and performance metrics. Using **Microsoft Excel**, I cleaned, modeled, and visualized the data to create an interactive dashboard. The goal was to transform raw transaction records into actionable insights regarding sales performance across different countries, product types, and time periods.

---

## Problem Statement
A coffee retail business needs a consolidated view of its sales performance to make informed decisions. Currently, sales data is dispersed across multiple spreadsheets (**Orders**, **Customers**, **Products**), making it difficult to:

- Track revenue trends  
- Identify top-paying customers  
- Monitor product popularity  

The objective is to build a **dynamic dashboard** that allows stakeholders to filter and view data by **time**, **product type**, and **customer location** to improve strategic planning.

---

## Data Source
The dataset used for this project is a **synthetic dataset** representing coffee sales transactions from **2019 to 2022**. It includes three main tables:

- **Orders**  
  Transactional data including order dates, quantities, and customer links.

- **Customers**  
  Demographic data including location, loyalty card status, and contact information.

- **Products**  
  Product details including coffee type, roast type, size, and unit price.

---

## Tools Used
### Microsoft Excel
- **Data Cleaning:** Handling duplicates and formatting inconsistencies  
- **Data Modeling:** Using `XLOOKUP` and `INDEX-MATCH` to create relationships between tables  
- **Pivot Tables:** Aggregating data for analysis  
- **Interactive Dashboard:** Creating slicers and timelines for dynamic user filtering  

---

## Key Objectives
- **Trend Analysis:**  
  Visualize sales performance over time (yearly and monthly) to identify seasonal patterns.

- **Geographic Performance:**  
  Compare sales distribution across key markets (United States, United Kingdom, Ireland).

- **Customer Insights:**  
  Identify top 5 customers by revenue to target for loyalty programs.

- **Product Analysis:**  
  Analyze sales volume by coffee type (Arabica, Robusta, Liberica, Excelsa) and roast type.

---

## Project Deliverables

- **Raw Data File:** Original, unmodified Excel dataset used as input.
- **Interactive Excel Dashboard:** A fully functional Excel workbook (.xlsx) containing the raw data, pivot tables, and the dynamic dashboard interface.
- **Process Documentation:** Brief documentation of data cleaning and transformation steps.
- **Dashboard Screenshot:** Static preview of the Excel dashboard.

---

## Dashboard Features
- **Timeline & Slicers:**  
  Allows users to filter data by specific dates, roast types, and loyalty card status.

- **Total Sales Cards:**  
  Immediate view of high-level metrics such as total sales.

- **Bar & Line Charts:**  
  Visual representation of sales trends and categorical comparisons.

---

## Insights and Recommendations

### 1. Market Disparity
**Insight:**  
The United States is the primary revenue driver (**$35.6k**), while the United Kingdom is significantly underperforming (**$2.8k**) relative to Ireland (**$6.7k**), despite having a much larger market size.

**Recommendation:**  
Investigate UK pricing structures and logistics to identify and resolve the market penetration gap.


### 2. Customer Concentration
**Insight:**  
Revenue is heavily reliant on a small “whale” cohort (top 5 customers), with individual customer spend exceeding **$270**.

**Recommendation:**  
Implement a Key Account Management protocol to retain high-value customers and reduce revenue volatility.


### 3. Product Strategy
**Insight:**  
Arabica and Liberica beans generate higher profit margins compared to the high-volume Robusta sales.

**Recommendation:**  
Prioritize marketing of **Premium Roast bundles** to encourage volume buyers to transition toward higher-margin products.


### 4. Seasonal Trends
**Insight:**  
Sales data shows consistent post-holiday demand slumps during **January and February**.

**Recommendation:**  
Replace aggressive discounting with **bundle strategies** during low-demand months to preserve Average Order Value (AOV).
