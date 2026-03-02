# Ecommerce-Sales-Analysis-Power-BI-Dashboard

# Ecommerce Sales Analysis – Power BI Dashboard

## 📌 Live Dashboard Link
https://app.powerbi.com/view?r=eyJrIjoiOTI0YjE2NzctNDE1Yi00MTlmLWIyYmMtODdjNjg4Nzk4ZGFkIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9

### 🏠 1. SALE ANALYSIS PAGE

![Sales Analysis Preview](/SALES%20ANALYSIS%20PAGE.jpeg)

The **Sales Analysis Page** hat tracks total sales (49.53M), recent 28-day performance (3.62M), daily trends with a 14-day moving average, and highlights top vendors—enabling data-driven insights through dynamic filters and drill-through reports.

---

### 📊 2. DRILL THROUGH BY VENDOR PAGE

![Vendor Details](/VENDOR%20DETAILS.jpeg)

The **Vendor details page** focus on vendor-level drill-through Power BI report showcasing Vendor's performance, highlighting total sales (49.53M), 514K items sold, and a detailed monthly sales breakdown to enable focused vendor performance analysis.

---
## 📌 Project Overview

This project focuses on analyzing the sales performance of a large ecommerce platform selling 25,000+ products through multiple vendors nationwide. The objective was to create an analytical dashboard for the Sales Team to:

* Track overall sales performance
* Analyze vendor-wise and item-wise contribution
* Identify underperforming products
* Visualize sales trends and distribution patterns

The dashboard was built using **three Excel datasets**:

1. **2021Sales.xls** – Order data including OrderID, Date, ItemID, Quantity, and Sales Amount
2. **Item-Vendor.xls** – Mapping of items to vendors
3. **Vendor-Manager.xls** – Mapping of vendors to sales managers

---

## 🗂 Data Model

A clean **star schema** was developed consisting of:

* **Fact Table** – Sales transactions
* **Dimension Tables** – Vendors, Items, Sales Managers
* Relationships connected using ItemID and VendorID

---

## 🎯 Key Features & Insights

### 🔹 Dynamic Slicers

* Vendor
* Sales Manager
* Date Range

### 🔹 14-Day Moving Average (Last 3 Months)

A dual-line chart displaying:

* Daily Sales
* 14-Day moving average
* Responsive to slicers

**DAX Example:**

```
14-Day Moving Avg =
AVERAGEX(
    DATESINPERIOD('Date'[Date], MAX('Date'[Date]), -14, DAY),
    [Total Sales]
)
```

---

### 🔹 Period Slicer (7d / 14d / 28d)

A separate visual showing short-term sales trends:

* Only responds to the period slicer
* Ignores all report-level filters
* Created using `REMOVEFILTERS` and `ALL` for isolation

---

### 🔹 Box Plot – Top 10 Vendor Sales Distribution

Using AppSource visual to show:

* Min
* Max
* Median
* Quartiles
* Spread of daily vendor performance

---

### 🔹 Second Best-Selling Item Per Vendor (RankX Table)

Custom calculated table using `RANKX`:

```
Second Best Item =
FILTER(
    ADDCOLUMNS(
        SUMMARIZE(
            Sales,
            Vendor[VendorName],
            Item[ItemID],
            "TotalSales", [Total Sales]
        ),
        "Rank", RANKX(
            CALCULATETABLE(
                SUMMARIZE(Sales, Item[ItemID])
            ),
            [Total Sales],
            ,
            DESC
        )
    ),
    [Rank] = 2
)
```

Manually validated for accuracy using Excel.

---

### 🔹 Drillthrough Reporting

Vendor-level detailed page with:

* Dedicated KPIs
* Key vendor performance visuals
* Back navigation to main dashboard

---

## 🧰 Techniques & Power BI Skills Used

* Data Modeling & Star Schema Design
* Advanced DAX (RankX, REMOVEFILTERS, ALL, AVERAGEX)
* Time-Series Analysis
* Drillthrough and Navigation
* Dynamic/Responsive Visuals
* Custom Box Plot Visual Integration
* Dynamic Page Titles

---

## 📊 KPIs Built

* Total Sales Revenue
* Total Quantity Sold
* Vendor Contribution
* Item Performance
* Moving Average Trends
* Second-Best Item by Vendor

---


## 💻 Repository Structure

```
📁 Ecommerce-Sales-Analysis
 ├── 📂 Data
 ├── 📂 Screenshots
 ├── 📂 Documentation
 ├── README.md
 └── Ecommerce-Sales.pbix
```

---

## 🙌 Swarna

**Swarna A B**
Data Analyst | Power BI | SQL | DAX
