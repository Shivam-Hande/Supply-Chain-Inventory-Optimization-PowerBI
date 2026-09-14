
# Supply Chain & Inventory Optimization Analytics

> An end-to-end Microsoft Power BI analytics project designed to help supply chain teams monitor inventory, understand demand patterns, evaluate warehouse and supplier performance, and make data-driven inventory decisions.

---

## 📊 Project Overview

Supply chain teams often struggle with maintaining the right inventory levels while balancing demand, inventory holding costs, supplier lead times, and operational efficiency.

This project develops an interactive **Supply Chain & Inventory Optimization Dashboard** using Microsoft Power BI.

The solution transforms daily SKU-level inventory and demand data into an analytical reporting system that helps identify:

- Inventory availability and coverage
- High-demand products
- Inventory concentration across warehouses
- Supplier lead-time patterns
- Demand vs inventory gaps
- Potential stockout risk
- Reorder requirements
- Inventory optimization opportunities
- Demand forecasting accuracy

The project follows an end-to-end analytics workflow:

**Raw Data → Power Query → Data Model → DAX → Interactive Dashboard → Business Insights**

---

# 🎯 Business Problem

A retail/e-commerce supply chain organization needs better visibility into its inventory and demand operations.

The business wants to answer questions such as:

- How much inventory is currently available?
- Which products contribute most to inventory value?
- Which warehouses hold the most inventory?
- Where is demand highest?
- Is available inventory sufficient relative to demand?
- Which suppliers have longer lead times?
- Which products may be at risk of inventory shortage?
- Which products require replenishment?
- How accurately is demand being forecast?
- How can inventory decisions be improved using data?

The dashboard provides a centralized analytical view to support these decisions.

---

# 🗂️ Dataset

The project uses a **High-Dimensional Supply Chain Inventory Dataset** containing daily SKU and warehouse-level operational data.

### Dataset Statistics

| Attribute | Value |
|---|---:|
| Records | 91,250 |
| SKUs | 50 |
| Warehouses | 5 |
| Suppliers | 10 |
| Regions | 4 |
| Dates | 365 |
| Time Period | Jan 2024 – Dec 2024 |
| Original Columns | 15 |
| Missing Values | 0 |
| Duplicate Rows | 0 |

The dataset has a daily grain at the:

**SKU + Warehouse + Date**

level.

This means each record represents the operational state of a particular SKU at a particular warehouse on a particular day.

---

# 📋 Data Dictionary

| Column | Description |
|---|---|
| Date | Daily observation date |
| SKU_ID | Unique product/SKU identifier |
| Warehouse_ID | Warehouse identifier |
| Supplier_ID | Supplier identifier |
| Region | Operational region |
| Units_Sold | Units sold during the day |
| Inventory_Level | Available inventory level |
| Supplier_Lead_Time_Days | Supplier lead time in days |
| Reorder_Point | Inventory threshold for replenishment |
| Order_Quantity | Quantity ordered for replenishment |
| Unit_Cost | Cost per unit |
| Unit_Price | Selling price per unit |
| Promotion_Flag | Indicates whether a promotion was active |
| Stockout_Flag | Stockout indicator |
| Demand_Forecast | Forecasted demand |

Additional analytical columns were created during Power Query transformation:

- `Inventory_Value`
- `Sales_Value`
- `Gross_Margin`

---

# 🛠️ Technology Stack

### Data Analysis & Transformation
- Python
- Pandas
- NumPy
- SQL
- Power Query

### Business Intelligence
- Microsoft Power BI
- DAX
- Power BI Data Modeling
- Interactive Visualizations

### Analytics Concepts
- KPI Analysis
- Demand Analysis
- Inventory Analysis
- Supplier Analysis
- Warehouse Analysis
- Inventory Coverage
- Reorder Point Analysis
- Stock Risk Analysis
- Forecast Error Analysis
- ABC Analysis
- Inventory Optimization

### Portfolio
- GitHub

---

# 🏗️ Data Architecture

The project uses a **Star Schema** to improve model organization, filtering, and analytical performance.

```text
                    ┌──────────────┐
                    │   DimDate    │
                    └──────┬───────┘
                           │
                           │
┌──────────────┐     ┌─────▼─────────────────────┐     ┌────────────────┐
│ DimProduct   │────►│   Fact_Inventory_Daily    │◄────│ DimWarehouse   │
└──────────────┘     └──────────┬─────────────────┘     └────────────────┘
                                 │
                                 │
                         ┌───────▼────────┐
                         │  DimSupplier   │
                         └────────────────┘
