# Power BI Visual Build Order

## Page 1 - Executive Overview

Purpose: show all-time revenue, yearly revenue, quarterly revenue, seasonal revenue, profit margin, and market target status.

Slicers:
- YearTable[Year]
- fact_orders_clean[Market]
- fact_orders_clean[Segment]
- dim_product[Category]

Visuals:
1. Card - Revenue -> [Revenue]
2. Card - Profit -> [Profit]
3. Card - Profit Margin -> [Profit Margin]
4. Card - Orders -> [Orders]
5. Card - Customers -> [Customers]
6. Card - Revenue YoY % -> [Revenue YoY %]
7. Line and clustered column chart - Revenue vs Profit Margin by Year
   - X-axis: YearTable[Year]
   - Column Y-axis: [Revenue]
   - Line Y-axis: [Profit Margin]
8. Clustered column chart - Quarterly Revenue
   - X-axis: DateTable[Year_Quarter]
   - Y-axis: [Revenue]
   - Tooltip: [Profit], [Profit Margin], [Orders]
9. Clustered column chart - Seasonal Revenue
   - X-axis: DateTable[Season]
   - Y-axis: [Revenue]
   - Tooltip: [Profit], [Profit Margin], [Quantity Sold]
10. Table - Market Target Performance
   - Rows: fact_orders_clean[Market]
   - Values: [Revenue], [Profit], [Profit Margin], [Revenue Gap to Market Target], [Meets Market Revenue Target]

## Page 2 - Product Performance

Purpose: show top products, best seller categories/subcategories, product profitability, and discount impact.

Slicers:
- YearTable[Year]
- fact_orders_clean[Market]
- dim_product[Category]
- dim_product[Subcategory]

Visuals:
1. Clustered bar chart - Top 10 Products by Units Sold
   - Y-axis: dim_product[Product]
   - X-axis: [Quantity Sold]
   - Visual filter: Top 10 by [Quantity Sold]
2. Clustered bar chart - Top 10 Products by Revenue
   - Y-axis: dim_product[Product]
   - X-axis: [Revenue]
   - Visual filter: Top 10 by [Revenue]
3. Treemap - Revenue by Category and Subcategory
   - Group: dim_product[Category]
   - Details: dim_product[Subcategory]
   - Values: [Revenue]
4. Matrix - Product Profitability Detail
   - Rows: Category, Subcategory, Product
   - Values: [Revenue], [Profit], [Profit Margin], [Quantity Sold], [Average Discount]
5. Scatter chart - Discount vs Profit Margin
   - X-axis: [Average Discount]
   - Y-axis: [Profit Margin]
   - Size: [Revenue]
   - Legend: dim_product[Category]
   - Details: dim_product[Subcategory]
6. Decomposition tree - Profit Driver Breakdown
   - Analyze: [Profit]
   - Explain by: Market, Segment, Category, Subcategory, Country

## Page 3 - Customer and Geography

Purpose: show returning customers, top customers, segment performance, markets, countries, and discount bands.

Slicers:
- YearTable[Year]
- fact_orders_clean[Market]
- fact_orders_clean[Country]
- fact_orders_clean[Segment]

Visuals:
1. KPI cards:
   - [Customers]
   - [Repeat Customers]
   - [Repeat Customer Rate]
   - [Returning Customers]
   - [Returning Customer Rate]
2. Line and clustered column chart - Returning Customer Trend
   - X-axis: YearTable[Year]
   - Column Y-axis: [Annual Active Customers]
   - Line Y-axis: [Returning Customer Rate]
3. Clustered bar chart - Top 10 Customers by Revenue
   - Y-axis: dim_customer[Customer_ID]
   - X-axis: [Revenue]
   - Visual filter: Top 10 by [Revenue]
4. Line chart with small multiples - Market Revenue Trend
   - X-axis: YearTable[Year]
   - Y-axis: [Revenue]
   - Small multiples: fact_orders_clean[Market]
5. Map - Revenue and Profit by Country
   - Latitude: fact_orders_clean[Country_latitude]
   - Longitude: fact_orders_clean[Country_longitude]
   - Size: [Revenue]
   - Tooltip: Country, Market, [Revenue], [Profit], [Profit Margin]
6. Clustered bar chart - Profit by Discount Band
   - Y-axis: fact_orders_clean[Discount_Band]
   - X-axis: [Profit]
   - Tooltip: [Revenue], [Profit Margin], [Orders], [Average Discount]
