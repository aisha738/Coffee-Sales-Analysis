# Technical Process Documentation

## Project Overview

This project simulates a real-world **Data Analyst workflow** using Microsoft Excel. It covers the full cycle of data analysis:

1. Extracting and gathering raw data  
2. Cleaning, transforming, and denormalizing data  
3. Building a structured data model  
4. Creating interactive visualizations and dashboards for decision-making  

**Tools Used:** Microsoft Excel (Office 365)  
**Key Techniques:** Data Modeling (Star Schema), ETL (Extract, Transform, Load), Pivot Tables, Dynamic Visualizations, Interactive Dashboards  

---

## 1. Data Gathering & Schema Understanding

The dataset consists of **three relational tables**:

| Table      | Type           | Key Fields & Description |
|------------|----------------|-------------------------|
| `orders`   | Fact Table     | Order ID, Order Date, Customer ID, Product ID, Quantity |
| `customers`| Dimension Table| Customer ID, Name, Email, Country, Loyalty Status |
| `products` | Dimension Table| Product ID, Coffee Type, Roast Type, Size, Unit Price |

**Technical Decision:**  
- Used Excel formulas for denormalization instead of Power Query  
- Demonstrated proficiency with lookup functions  

---

## 2. Data Cleaning & Transformation (ETL)

### 2.1 Handling Missing Data
1. Checked all columns for **null or blank values**  
2. Verified **critical keys** (Customer ID, Product ID) were populated  

### 2.2 Data Formatting
1. Standardized **Order Date** (`dd-mmm-yyyy`)  
2. Formatted **Unit Price** and **Sales** as currency  
3. Applied custom number format to **Size** (`0.0 "kg"`)  

### 2.3 Data Merging / Denormalization

#### Strategy: Hybrid Lookup Approach
1. **Customer Information (XLOOKUP)**
 ```excel
   =IF(XLOOKUP([@CustomerID], customers[CustomerID], customers[CustomerName])=0,"",XLOOKUP([@CustomerID], customers[CustomerID], customers[CustomerName]))
```
## 2.4 Product Information (INDEX-MATCH)

- Retrieves **Coffee Type, Roast Type, Size, Unit Price**  
- Dynamic column referencing for multiple fields  

---

## 3. Data Cleaning & Standardization

| Abbreviation | Full Name  |
|--------------|------------|
| Rob          | Robusta    |
| Exc          | Excelsa    |
| Ara          | Arabica    |
| Lib          | Liberica   |
| M            | Medium     |
| L            | Light      |
| D            | Dark       |

---

## 4. Feature Engineering (Calculated Columns)

### 4.1 **Sales Metric**  
```excel
[@Unit Price] * [@Quantity]
```

### 4.2 Loyalty Check

- Loyalty Card (Yes/No) for segmentation  

---

## 5. Data Analysis (Pivot Tables)

1. Converted **Master Table** to Excel Table (`Ctrl+T`)  
2. Created **Processing Sheet** to separate raw data  

**Pivot Table Structure:**  
- Total Sales over Time (Year & Month)  
- Sales by Country (US, UK, Ireland)  
- Top 5 Customers (Sales Descending, Top N filter)  

---

## 6. Visualization & Dashboard Design

### 6.1 Chart Selection
- Line Chart: Sales over Time  
- Bar Chart: Country & Top Customers  

### 6.2 Interactivity
- Slicers: Roast Type, Size, Loyalty Card  
- Timeline: Order Date for month/year filtering  
- Report Connections: All slicers/timelines connected  

### 6.3 UI / Styling
- Purple Theme (RGB: 60, 20, 100)  
- Grid layout, hidden gridlines, collapsed ribbon  

---

## 7. Challenges & Solutions

| Challenge                        | Solution                                                        |
|----------------------------------|-----------------------------------------------------------------|
| Raw product codes unintuitive     | Mapped codes to full descriptions before visualization         |
| Dashboard fitting on single screen | Grid layout, optimized chart sizing, hidden interface elements |

---

## 8. Key Takeaways

- Full-cycle Excel-based data analysis  
- Hybrid lookup methods (XLOOKUP + INDEX-MATCH)  
- Interactive dashboard with slicers, timelines, connected charts  
- Data cleaning, transformation, and standardization best practices  
- Actionable insights: sales trends, top customers, segmentation by loyalty & product type  

   ```excel
   =IF(XLOOKUP([@CustomerID], customers[CustomerID], customers[CustomerName])=0,"",XLOOKUP([@CustomerID], customers[CustomerID], customers[CustomerName]))
   ```
  ### Note on ETL Process

- This workflow follows **ETL (Extract, Transform, Load)** principles:

  1. **Extract:** Pull data from `customers` and `products` into `orders`  
  2. **Transform:** Clean, format, denormalize, and calculate in the Master Table  
  3. **Load:** Store enriched data in the `orders` Master Table ready for analysis 

