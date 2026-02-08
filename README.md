# Sales-Customer-Dashboards-Dynamic-

**📊 Project Overview**
A comprehensive dual-dashboard Tableau visualization system designed for advanced sales and customer analytics. This dynamic dashboard solution provides year-over-year comparisons, trend analysis, and actionable insights through interactive KPIs and visualizations. Built with multi-table data modeling, the dashboard offers real-time filtering capabilities and performance tracking across multiple business dimensions.

<img width="599" height="395" alt="image" src="https://github.com/user-attachments/assets/fd8d77bc-511e-47b2-b9cd-ec8dafa65054" />


**🎯 Objective**
The primary objectives of this dashboard system are to:

Monitor Sales Performance across products, categories, regions, and time periods
Analyze Customer Behavior through distribution patterns and purchasing trends
Enable Year-over-Year Comparisons with dynamic year selection (2020-2023)
Track Business KPIs including Sales, Profit, Quantity, Orders, and Customer metrics
Identify Trends through weekly sales patterns and subcategory performance
Provide Actionable Insights via comparative analysis and visual indicators
Support Data-Driven Decisions through interactive filtering and drill-down capabilities

**📝 Description**

This project consists of two interconnected dashboards that provide a 360-degree view of business performance:

**🏪 Sales Dashboard**

A comprehensive sales analytics interface featuring:

6 Dynamic KPIs with current year (CY) vs previous year (PY) comparisons

Weekly trend analysis with sparklines showing sales patterns

Subcategory performance comparison with visual indicators

Geographic and segment-level filtering

Real-time calculations based on selected year parameter

**👥 Customer Dashboard**

A customer-centric analytics interface featuring:

Customer distribution analysis by order volume

Top 10 customers by sales performance

Customer segmentation insights

Order patterns and purchasing behavior

Customer lifetime value indicators

**Technical Architecture
Data Model:**

**4 CSV data sources with relational connections:**

Orders.csv (9,994 records) - Transaction data

Customers.csv - Customer master data

Location.csv - Geographic information

Products.csv (1,646 products) - Product catalog



**Key Features:**

Dynamic year selection via parameter control (2020-2023)

Advanced calculated fields for CY/PY metrics

Color-coded KPI indicators (Above/Below average)

Min/Max value highlighting in trend charts

Interactive filtering across all dimensions

Responsive design for desktop viewing

**🔑 Key Performance Indicators (KPIs)**

The Sales Dashboard features 6 primary KPIs, each with:

Current Year (CY) value

Previous Year (PY) value

Year-over-Year percentage change

Visual indicator (▲ positive, ▼ negative)

**1. Sales KPI**

Metric: Total Sales Revenue
Format: Currency ($#,##0K)
Calculation: SUM(Sales) for selected year
Comparison: CY Sales vs PY Sales
Formula: (CY Sales - PY Sales) / PY Sales
Use Case: Primary revenue performance tracking

**2. Profit KPI**

Metric: Total Profit
Format: Currency ($#,##0K)
Calculation: SUM(Profit) for selected year
Comparison: CY Profit vs PY Profit
Formula: (CY Profit - PY Profit) / PY Profit
Use Case: Profitability analysis and margin tracking

**3. Quantity KPI**

Metric: Total Units Sold
Format: Number (#,##0)
Calculation: SUM(Quantity) for selected year
Comparison: CY Quantity vs PY Quantity
Formula: (CY Quantity - PY Quantity) / PY Quantity
Use Case: Volume tracking and inventory planning

**4. Orders KPI**

Metric: Total Number of Orders
Format: Number (#,##0K)
Calculation: COUNTD(Order ID) for selected year
Comparison: CY Orders vs PY Orders
Formula: (CY Orders - PY Orders) / PY Orders
Use Case: Transaction volume and order frequency analysis

**5. Customers KPI**

Metric: Total Unique Customers
Format: Number (#,##0K)
Calculation: COUNTD(Customer ID) for selected year
Comparison: CY Customers vs PY Customers
Formula: (CY Customers - PY Customers) / PY Customers
Use Case: Customer acquisition and retention tracking

**6. Sales Per Customer KPI**

Metric: Average Sales Per Customer
Format: Currency ($#,##0)
Calculation: Total Sales / Total Customers
Comparison: CY Sales/Customer vs PY Sales/Customer
Formula: SUM(CY Sales) / COUNTD(CY Customers)
Use Case: Customer value and spending behavior analysis

**📈 Dashboard Components**
**Sales Dashboard**
**1. KPI Cards (Top Section)**

Six side-by-side KPI cards
Each card displays:

KPI title
Current year value
Previous year value
Percentage change with directional arrow
Color-coded indicator



**2. Weekly Trends for Sales (Sparkline Chart)**

Line chart showing sales by week
Features:

Highlights max and min values in red
Shows current year data
Enables weekly pattern identification
Compact visualization for trend spotting


Calculation: WINDOW_MAX/MIN functions
Insight: Identify seasonality and sales cycles

**3. Sales by Subcategory Comparison**

Horizontal bar chart with dual metrics
Features:

CY Sales (dark bars)
PY Sales (light gray bars)
Color-coded circles indicating performance above/below average
Sorted by sales volume


**17 Subcategories tracked:**

Phones, Chairs, Storage, Tables, Binders, Machines, Accessories, Copiers, Bookcases, Appliances, Furnishings, Paper, Supplies, Art, Envelopes, Labels, Fasteners


**Visual Indicators:**

🔵 Blue circle = Above average sales
🔴 Orange circle = Below average sales



**4. Interactive Filters**

Year selector (2020-2023)
Category filter (Furniture, Office Supplies, Technology)
Subcategory multi-select
Segment filter (Consumer, Corporate, Home Office)
Region filter (Central, East, South, West)
State/City filters

**Customer Dashboard
1. Customer Distribution**

Bar chart showing customer count by order volume
**Features:**

Groups customers by number of orders placed
Identifies customer loyalty patterns
Shows distribution spread


Calculation: 
FIXED [Customer ID]: COUNTD([Order ID])

Insight: Understanding customer engagement levels

**2. Top 10 Customers**

Ranked list of highest-revenue customers
Features:

Customer name
Total sales value
Visual bar indicator
Sorted by sales descending


Use Case: VIP customer identification and relationship management

**3. Customer Segmentation View**

Breakdown by customer segment:

Consumer
Corporate
Home Office


**Sales and order metrics by segment

🔢 Data Structure & Fields**
**Orders.csv (Transaction Data)**

Row ID: Unique record identifier
Order ID: Unique order identifier (3,377 unique orders)
Order Date: Transaction date (1,405 unique dates)
Ship Date: Delivery date
Ship Mode: Shipping method
Customer ID: Customer identifier (link to Customers.csv)
Segment: Customer segment (Consumer, Corporate, Home Office)
Postal Code: Location identifier (link to Location.csv)
Product ID: Product identifier (link to Products.csv)
Sales: Revenue amount
Quantity: Units sold
Discount: Discount percentage
Profit: Profit amount

**Customers.csv (Customer Master)**

Customer ID: Unique customer identifier
Customer Name: Customer full name

**Location.csv (Geographic Data)**

Postal Code: Geographic identifier
City: City name
State: State name
Region: Geographic region (4 regions)
Country/Region: Country (Germany)

**Products.csv (Product Catalog)**

Product ID: Unique product identifier (1,646 products)
Category: Product category (3 categories: Furniture, Office Supplies, Technology)
Sub-Category: Product subcategory (17 subcategories)
Product Name: Full product name (1,637 unique products)

**🧮 Advanced Calculated Fields**

Year-Based Calculations

Current Year (CY) Sales:
IF YEAR([Order Date]) = [Parameters].[Parameter 1] 
THEN [Sales]
END

Previous Year (PY) Sales:
IF YEAR([Order Date]) = [Parameters].[Parameter 1]-1 
THEN [Sales]
END

CY Customers:
IF YEAR([Order Date]) = [Parameters].[Parameter 1] 
THEN [Customer ID]
END

CY Orders:
IF YEAR([Order Date]) = [Parameters].[Parameter 1] 
THEN [Order ID]
END

CY Profit:
IF YEAR([Order Date]) = [Parameters].[Parameter 1] 
THEN [Profit]
END

CY Quantity:
IF YEAR([Order Date]) = [Parameters].[Parameter 1] 
THEN [Quantity]
END

**Comparative Calculations**
% Difference Sales:
(SUM([CY Sales]) - SUM([PY Sales])) / SUM([PY Sales])

% Difference Profit:
(SUM([CY Profit]) - SUM([PY Profit])) / SUM([CY Profit])

% Difference Quantity:
(SUM([CY Quantity]) - SUM([PY Quantity])) / SUM([PY Quantity])

% Difference Orders:
(COUNTD([CY Orders]) - COUNTD([PY Orders])) / COUNTD([PY Orders])

% Difference Customers:
(COUNTD([CY Customers]) - COUNTD([PY Customers])) / COUNTD([PY Customers])

**KPI Performance Indicators**

Sales Above/Below Average:
IF SUM([CY Sales]) > WINDOW_AVG(SUM([CY Sales]))
THEN 'Above'
ELSE 'Below'
END

Profit Above/Below Average:
IF SUM([CY Profit]) > WINDOW_AVG(SUM([CY Profit]))
THEN 'Above'
ELSE 'Below'
END

Current Year Less Than Previous Year Indicator:
IF SUM([CY Sales]) < SUM([PY Sales]) 
THEN '⬤'
ELSE ''
END

**Min/Max Calculations**

Min/Max Sales:
IF SUM([CY Sales]) = WINDOW_MAX(SUM([CY Sales]))
THEN SUM([CY Sales])
ELSEIF SUM([CY Sales]) = WINDOW_MIN(SUM([CY Sales]))
THEN SUM([CY Sales])
END

Min/Max Profit:
IF SUM([CY Profit]) = WINDOW_MAX(SUM([CY Profit]))
THEN SUM([CY Profit])
ELSEIF SUM([CY Profit]) = WINDOW_MIN(SUM([CY Profit]))
THEN SUM([CY Profit])
END

**Customer Metrics**

Sales Per Customer:
SUM([CY Sales]) / COUNTD([CY Customers])
Customer Order Count:
{FIXED [CY Customers]: COUNTD([CY Orders])}

Total Sales (LOD Expression):
{SUM([CY Sales])}

**🎨 Design & Visual Elements**
Color Scheme

Primary KPI Values: Black (#212121)
Secondary/Previous Year: Light Gray (#CECECE)
Positive Performance: Blue (#1DA2D0)
Negative Performance: Orange (#FF5500)
Min/Max Indicators: Red (#E15759)
Trend Line: Blue (#4E79A7)

Typography & Formatting

Currency Format: $#,##0K for thousands
Percentage Format: ▲ 0.0% / ▼ -0.0% (with directional arrows)
Number Format: #,##0 for whole numbers
Date Settings: Week starts on Monday

Visual Indicators

▲ Green arrow for positive year-over-year change
▼ Red arrow for negative year-over-year change
🔵 Blue circle for above-average performance
🔴 Orange circle for below-average performance
⬤ Black dot for specific performance flags

**🛠️ Technical Specifications**
Tableau Version

Built with: Tableau Desktop 2023.2.0
Build: 20232.23.0611.2007
Platform: Windows
Compatibility: Tableau Desktop 2023.2 and later

Data Extract

Format: Hyper extract (.hyper)
Total Records: 9,994 order records
Refresh Date: August 4, 2023
Encoding: UTF-8 / Windows-1252
Locale: English (Germany) - en_DE
Currency: Euro (€)

Performance Optimizations

Data extract for faster query performance
Indexed fields for filtering
Aggregated calculations where possible
Efficient LOD expressions
Optimized worksheet layouts

**📊 Business Insights & Use Cases
For Sales Managers**

Track daily/weekly sales performance against targets

Identify top-performing subcategories for strategic focus

Monitor year-over-year growth across all metrics

Spot seasonal trends in weekly sales patterns

Evaluate regional performance for territory management

**For Marketing Teams**

Segment analysis for targeted campaigns

Customer behavior insights for personalization

Product category performance for promotional planning

Geographic targeting based on regional sales

Customer acquisition trends monitoring

**For C-Level Executives**

High-level KPI monitoring at a glance

Strategic performance evaluation across time periods

Business health indicators with YoY comparisons

Quick decision-making support through visual clarity

Trend identification for long-term planning

**For Financial Analysts**

Profit margin analysis by product and category

Revenue forecasting based on historical trends

Cost optimization insights through profit metrics

ROI tracking on sales initiatives

Financial performance benchmarking

**For Customer Success Teams**

Top customer identification for relationship management

Customer distribution analysis for segmentation

Customer lifetime value calculation

Retention pattern recognition

VIP customer program development

**🎯 Sample Analysis Questions**

This dashboard system can answer questions such as:
**Sales Performance:**

What is our year-over-year sales growth for 2023?
Which subcategories are performing above average?
What are the weekly sales trends showing?
How do sales compare across different regions?
Which product categories drive the most revenue?

**Customer Analytics:**

How many active customers do we have this year?
What is the average sales per customer?
Who are our top 10 customers by revenue?
How are customers distributed by order frequency?
What is our customer growth rate year-over-year?

**Profitability:**

What is our profit margin trend?
Which subcategories are most profitable?
How does profit compare to previous year?
What is the relationship between sales and profit?

**Operational Metrics:**

How many orders are we processing?
What is the average order quantity?
How do different segments perform?
What are the shipping patterns?

**📁 Repository Structure**
├── Sales___Customer_Dashboards.twbx          # Main Tableau packaged workbook

├── README.md                                  # This file

├── data/                                      # Data files (if included)

│   ├── Orders.csv

│   ├── Customers.csv

│   ├── Location.csv

│   └── Products.csv

├── screenshots/                               # Dashboard screenshots

│   ├── sales_dashboard.png

│   └── customer_dashboard.png

└── documentation/                             # Additional documentation

    ├── data_dictionary.md
    
    └── calculation_guide.md
