# Global Skincare & Beauty E-Commerce Analysis

A portfolio Power BI project focused on sales performance, profitability, customer retention, product performance, geographic trends, and discount strategy for a global skincare and beauty e-commerce dataset.

## Project Overview

This project uses **Power BI, Power Query, DAX, and dimensional data modeling** to turn transactional e-commerce data into a three-page analytical report designed for business decision-making.

The model analyzes revenue and profit trends, product/category performance, market and country performance, customer retention, discount strategy, and top customers/products.

## Key Results

- **$6.52M** total revenue
- **$1.07M** total profit
- **16.3%** overall profit margin
- **17,415** unique customers
- **5,436 repeat customers**
- **31.2% repeat-customer rate**
- **Europe** produced the strongest market margin at about **22.3%**
- **Asia Pacific** generated the highest market revenue at about **$1.83M**
- Discount bands above **30%** produced negative aggregate profit in the analyzed data

## Tech Stack

- Microsoft Power BI
- Power Query
- DAX
- Dimensional / star-schema modeling
- Excel
- Data cleaning and transformation
- Business intelligence and KPI design

## Data Model

Primary tables:

- `fact_orders_clean`
- `dim_customer`
- `dim_product`
- `fact_customer_year`
- `DateTable` — generated with DAX
- `YearTable` — generated with DAX

Relationships are intentionally one-to-many, active, and single-direction. See [`model/relationship_map.txt`](model/relationship_map.txt).

## Dashboard Structure

### Page 1 — Executive Overview
- Revenue, profit, profit margin, orders, customers, and YoY growth KPI cards
- Revenue vs. profit margin by year
- Quarterly revenue
- Seasonal revenue
- Market target performance

### Page 2 — Product Performance
- Top 10 products by units sold
- Top 10 products by revenue
- Revenue by category and subcategory
- Product profitability matrix
- Discount vs. profit margin scatter plot
- Profit-driver decomposition tree

### Page 3 — Customer & Geography
- Customer and retention KPI cards
- Returning-customer trend
- Top customers by revenue
- Market revenue trends
- Revenue and profit by country
- Profit by discount band

See [`docs/visual_build_order.md`](docs/visual_build_order.md) for the full report specification.

## DAX

The reusable DAX pack includes core KPIs, time intelligence, targets, retention metrics, product metrics, discount metrics, and display helpers. See [`dax/powerbi_measure_pack.dax`](dax/powerbi_measure_pack.dax).

## Repository Structure

```text
Sales-Data-Analysis/
├── README.md
├── dax/
│   └── powerbi_measure_pack.dax
├── docs/
│   ├── visual_build_order.md
│   └── project_notes.md
├── model/
│   └── relationship_map.txt
├── theme/
│   └── skincare_beauty_theme.json
└── data/
    └── README.md
```

## Reproducing the Report

1. Open Power BI Desktop.
2. Import the source workbook/dataset.
3. Load `fact_orders_clean`, `dim_customer`, `dim_product`, and `fact_customer_year`.
4. Create `DateTable` and `YearTable` using the DAX definitions.
5. Build the relationships shown in `model/relationship_map.txt`.
6. Mark `DateTable[Date]` as the model's date table.
7. Add the DAX measures.
8. Import the theme from `theme/skincare_beauty_theme.json`.
9. Build the three report pages using `docs/visual_build_order.md`.

## Power BI File

The project files available during this deployment did not include the final `.pbix` binary. This repository therefore preserves the **reproducible model, DAX, theme, dashboard specification, and verified analytical findings**. The final PBIX can be added later without changing the repository structure.

## Author

**Caleb Shenkel**  
Electrical & Computer Engineering Technology | Controls, IT/OT, Data & Automation
