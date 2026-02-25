README – GitHub Project Description

Project Title:
End-to-End Sales Funnel, Customer Retention & Pipeline Forecast Analytics Dashboard (Power BI)

------------------------------------------------------------

PROJECT OVERVIEW
This project is a multi-page, enterprise-style Power BI dashboard designed to analyze the complete sales lifecycle, including Sales Funnel performance, Customer Retention, Sales Performance, and Pipeline Forecasting.

The dashboard simulates a real-world CRM analytics environment (similar to Salesforce/HubSpot) and demonstrates advanced Business Intelligence capabilities using Star Schema data modeling, DAX measures, and interactive dashboard design.

This project reflects a career transition from 10+ years in Sales to Data Analytics, combining strong business domain knowledge with technical BI skills.

------------------------------------------------------------
## 📊 Dashboard Preview

### 🏠 Home Page
![Home Page](Images/Home_Page.png)

### 📈 Executive Dashboard
![Executive Dashboard](Images/Executive_Dashboard.png)

### 🔍 Funnel & Conversion Analysis
![Funnel Analysis](Images/Funnel_Conversion.png)

### 👥 Customer Intelligence
![Customer Intelligence](Images/Customer_Intelligence.png)

### 📊 Pipeline Forecast & Revenue Insights
![Pipeline Forecast](Images/Pipeline_Forecast.png)

### 📑 Drillthrough – Deal Details
![Drillthrough](Images/Drillthrough.png)


BUSINESS PROBLEM
Sales organizations often struggle with:
- Lack of visibility into funnel conversion
- Poor pipeline forecasting
- Limited customer retention insights
- Fragmented sales performance reporting

This dashboard solves these challenges by providing a centralized analytics solution for:
- Sales Leadership
- Business Analysts
- CRM Teams
- Revenue Operations

------------------------------------------------------------

DATA MODEL & ARCHITECTURE (STAR SCHEMA)

Fact Table:
- Fact_Deals (Deal Value, Stage, Deal Date, CustomerID, SalesRepID, LeadSourceID)

Dimension Tables:
- Dim_Date
- Dim_Customer
- Dim_SalesRep
- Dim_LeadSource

Relationships:
- One-to-Many (Dimension → Fact)
- Single Direction Filtering
- Marked Date Table for Time Intelligence

------------------------------------------------------------

DASHBOARD PAGES (ENTERPRISE BI APPLICATION)

1. Home / Navigation Page
- Application-style landing page
- Button-based navigation
- Professional BI UX design

2. Executive Overview (Sales Funnel Dashboard)
Key KPIs:
- Total Revenue
- Total Deals
- Won Deals
- Conversion Rate %

Insights:
- Funnel stage distribution
- Monthly revenue trends
- Pipeline value by stage
- Dynamic executive insights (DAX-driven)

3. Customer Intelligence Dashboard
Key Metrics:
- Unique Customers
- Returning Customers
- Repeat Customer %
- New Customers
- Average Deal Size

Business Value:
- Customer retention analysis
- Growth vs retention tracking
- Regional segmentation

4. Sales Performance Analysis
Key Visuals:
- Revenue by Sales Representative
- Revenue by Region
- Top Customers by Revenue
- Lead Source Performance

Business Impact:
- Identifies top-performing reps and regions
- Supports strategic sales planning

5. Funnel & Conversion Analysis
Key Features:
- Deals by Stage Trend (Multi-line)
- Conversion Rate by Region
- Conversion Rate by Lead Source
- Win vs Loss distribution

Business Insight:
- Detects funnel bottlenecks
- Improves conversion optimization

6. Pipeline & Forecast Insights
Advanced Metrics:
- Open Pipeline Value
- Weighted Pipeline Forecast
- Revenue vs Forecast Comparison

Forecast Logic (Stage Probability):
- Lead = 10%
- Qualified = 30%
- Proposal = 60%
- Negotiation = 80%

7. Drillthrough – Deal Detail Breakdown
- Deal-level deep dive analysis
- Customer, Stage, Deal Value, Sales Rep, Region
- Context-aware filtering from all visuals

------------------------------------------------------------

KEY DAX MEASURES (ADVANCED)

Core KPIs:
Total Revenue = SUM(Fact_Deals[DealValue])
Total Deals = COUNT(Fact_Deals[DealID])
Won Deals = CALCULATE([Total Deals], Fact_Deals[Stage] = "Won")
Lost Deals = CALCULATE([Total Deals], Fact_Deals[Stage] = "Lost")
Conversion Rate % = DIVIDE([Won Deals], [Total Deals], 0)

Customer Retention:
Unique Customers = DISTINCTCOUNT(Fact_Deals[CustomerID])

Returning Customers =
CALCULATE(
    DISTINCTCOUNT(Fact_Deals[CustomerID]),
    FILTER(
        VALUES(Fact_Deals[CustomerID]),
        CALCULATE(COUNT(Fact_Deals[DealID])) > 1
    )
)

Repeat Customer % =
DIVIDE([Returning Customers], [Unique Customers], 0)

New Customers =
[Unique Customers] - [Returning Customers]

Forecasting & Pipeline:
Open Pipeline Value =
CALCULATE(
    SUM(Fact_Deals[DealValue]),
    KEEPFILTERS(
        NOT(Fact_Deals[Stage] IN {"Won","Lost"})
    )
)

Weighted Pipeline =
SUMX(
    Fact_Deals,
    Fact_Deals[DealValue] *
    SWITCH(
        Fact_Deals[Stage],
        "Lead", 0.1,
        "Qualified", 0.3,
        "Proposal", 0.6,
        "Negotiation", 0.8,
        0
    )
)

Advanced UX Measures:
Dynamic Title = 
"Sales Funnel Dashboard - " & SELECTEDVALUE(Dim_Date[Year], "All Years")

Executive Insights uses:
- VAR
- TOPN
- CONCATENATEX
- FORMAT
- UNICHAR (Dynamic Narrative Reporting)

------------------------------------------------------------

KEY FEATURES IMPLEMENTED
- Multi-page dashboard architecture (7 pages)
- Star Schema data modeling
- Advanced DAX (SUMX, FILTER, CALCULATE, VAR)
- Drillthrough functionality
- Dynamic titles & executive insights
- Synced slicers (Year, Region, Sales Rep)
- Interactive navigation (App-style UX)
- Probability-based revenue forecasting

------------------------------------------------------------

DATASET INFORMATION
- Type: Synthetic CRM-style dataset
- Structure: Star Schema
- Inspired by real-world CRM systems (Salesforce / HubSpot)
- Purpose: Portfolio project for realistic sales analytics simulation
- Data Privacy: No real company data used

------------------------------------------------------------

TOOLS & TECHNOLOGIES
- Microsoft Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query
- Data Modeling (Star Schema)
- Business Intelligence & Data Visualization
- Analytical Storytelling

------------------------------------------------------------

## 🛠 Skills Demonstrated
- Power BI (Advanced Dashboard Development)
- DAX (KPIs, Forecasting, Retention Metrics)
- Data Modeling (Star Schema)
- Business Intelligence & KPI Analytics
- CRM & Sales Funnel Analysis
- Interactive Reporting & Drillthrough Analysis

------------------------------------------------------------

WHY THIS PROJECT STANDS OUT
- Real business use-case (CRM Analytics)
- Advanced DAX & Forecasting Logic
- Enterprise-style UX & Navigation
- Domain + Analytics combination (Sales → Data)
- Multi-page interactive BI solution (not a generic dashboard)
