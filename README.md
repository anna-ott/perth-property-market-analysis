# Perth Property Insights

This project explores housing trends in Perth, Western Australia using a SQL data model and a Power BI dashboard.

I built this as an end-to-end data project to understand how property prices evolve over time, what drives those changes, and how supply, demand, and affordability interact across different areas.

---

## What I focused on

* Analysing how the Perth property market has performed over time
* Comparing suburbs to identify high-performing and underperforming areas
* Looking at how Perth compares to the broader Australian market
* Understanding key drivers of price (e.g. location, proximity to amenities, property features)
* Exploring supply vs demand using building approvals and population growth

---

## Data model

The data is structured in a star schema with separate dimension and fact tables.

I built the model in SQL to keep transformations and relationships clear and reusable, and then connected Power BI directly to this model.

![Data Model](assets/data_model.png)

---

## Dashboard

### Overview

High-level view of the Perth market including median price, price per sqm, overall trends, and geographic distribution.

![Overview](assets/dashboard_overview.png)

### Suburb Detail

Focused view of individual suburbs, allowing comparison of price levels, sales activity, and distribution patterns.

![Suburb Analysis](assets/suburb_analysis.png)

### Perth vs Australia

Comparison of Perth housing trends against national data to highlight differences in growth and market behaviour.

![Comparison](assets/perth_vs_australia_comparison.png)

### Price Drivers

Explores how factors such as distance to the CBD, transport, schools, and beaches relate to property prices.

![Drivers](assets/price_drivers_analysis.png)

### Supply & Demand

Examines the relationship between population growth and building approvals to highlight potential supply imbalances.

![Supply Demand](assets/supply_demand_analysis.png)

---

## How the project is built

* Raw CSV datasets were imported into SQL Server
* Data was cleaned, reshaped, and standardised
* Wide tables were converted to long format using SQL (UNPIVOT)
* Dimension tables (location, property, dwelling type, date) were created
* Fact tables were built for sales, population, approvals, earnings, and prices
* Power BI connects to the SQL model for analysis
* DAX is used for KPIs, YoY calculations, and dynamic reporting

---

## Data preparation

The raw data required significant cleaning and restructuring before it was ready for analysis. This included:

* Removing irrelevant sheets, rows, and columns from source files
* Renaming columns to consistent, meaningful names
* Converting data types (e.g. strings to numeric values)
* Standardising units (e.g. distances to kilometres, prices to correct scale)
* Converting wide datasets into long format for easier analysis
* Creating consistent DateID fields across all tables
* Handling missing or unrealistic values (e.g. garages, build year, extreme values)

All transformations are documented in the SQL scripts and data cleaning log.

---

## Data handling decisions

Outliers in price, land area, and floor area were identified using the interquartile range (IQR) method in SQL.

Quartiles (Q1 and Q3) were calculated using window functions, and values outside the range
(Q1 − 1.5 × IQR, Q3 + 1.5 × IQR) were flagged as outliers.

These outliers were not removed from the dataset, but instead flagged and filtered out in the report visuals to avoid distorting trends and averages. This ensures the analysis reflects typical market behaviour while preserving the original data.

---

## Key insights

Some of the main observations from the analysis include:

* Properties closer to key amenities (CBD, beach, transport) tend to achieve higher prices
* Suburb-level performance varies significantly, with some areas consistently outperforming others
* Smaller land parcels tend to achieve higher prices per sqm, suggesting that land value per sqm decreases as lot size increases
* Supply (building approvals) does not always keep pace with demand (population growth)
* FY2021 shows an exceptional rebound in supply (+88.5%), likely reflecting post-COVID market activity
* Perth shows different price trends compared to national averages, particularly compared to eastern states

---

## Limitations

Some parts of the analysis were limited by data availability:

* Population and building approvals data are not always available at suburb level
* This makes it harder to fully assess supply vs demand for specific suburbs

Despite this, the available data still provides a strong view of overall market trends.

---

## Data sources

* Perth House Prices (Kaggle)
* ABS Building Approvals
* ABS Population Estimates
* ABS Average Weekly Earnings
* ABS Dwelling Prices
* Australian Postcodes dataset
* Manually compiled Perth beach data

---

## Tech stack

* SQL Server (data modelling and transformations)
* Power BI (visualisation and reporting)
* CSV files (source data)

---

## Project structure

```text id="xv7cl0"
Perth-Property-Insights/
  powerbi/
  sql/
  assets/
```

---

## Notes

* SQL handles most of the data preparation and modelling
* Power BI is used mainly for measures and visualisation
* SQL scripts are organised in execution order (see `sql/00_README_RUN_ORDER.sql`)

---

## Author

Anna Ott

