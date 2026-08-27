# Project Notes and Analytical Findings

## Scope

This project analyzes a global skincare and beauty e-commerce dataset in Power BI using a structured analytical model, DAX measures, and three report pages.

## Data Preparation

The project preparation workflow included:

- Removing duplicate business rows
- Trimming and standardizing text values
- Creating a stable `Product_Key` for products that repeat across category/subcategory combinations
- Adding Year, Quarter, Month, Year-Month, Year-Quarter, and Season fields
- Adding profit-margin calculations
- Creating discount bands
- Creating repeat-customer and returning-customer flags

## Verified Overall Metrics

- Total revenue: **$6,517,641**
- Total profit: **$1,065,426**
- Overall profit margin: **16.3%**
- Unique customers: **17,415**
- Repeat customers: **5,436**
- Repeat-customer rate: **31.2%**
- Multi-year customers: **4,417** (**25.4%**)

## Market Performance

| Market | Revenue | Profit | Profit Margin |
|---|---:|---:|---:|
| Africa | $486,811 | $66,213 | 13.6% |
| Asia Pacific | $1,831,648 | $228,743 | 12.5% |
| Europe | $1,487,444 | $331,645 | 22.3% |
| LATAM | $1,339,726 | $216,043 | 16.1% |
| USCA | $1,372,012 | $222,782 | 16.2% |

### Interpretation

- **Asia Pacific** is the largest market by revenue, but its margin is below the overall portfolio margin.
- **Europe** combines high revenue with the strongest market-level margin, making it the most profitable market on a percentage basis.
- **Africa** is the smallest market and also has a below-target margin, making it a useful candidate for deeper product, discount, and customer analysis.

## Discount Strategy

| Discount Band | Revenue | Profit | Profit Margin |
|---|---:|---:|---:|
| 0% | $3,580,519 | $1,135,323 | 31.7% |
| 0.1%-10% | $631,106 | $120,046 | 19.0% |
| 10.1%-20% | $829,183 | $98,604 | 11.9% |
| 20.1%-30% | $134,263 | $7,142 | 5.3% |
| 30.1%-50% | $826,565 | -$128,974 | -15.6% |
| 50.1%-100% | $516,005 | -$166,715 | -32.3% |

### Interpretation

The strongest commercial finding is the relationship between discount depth and profitability. Non-discounted sales generate the highest aggregate margin, while discount bands above 30% are loss-making in aggregate. The dashboard is designed to let users drill into the markets, categories, products, and customer segments behind those losses rather than treating discounting as a single company-wide metric.

## Model Design

The model avoids many-to-many and bidirectional relationships. Date analysis is handled through a continuous DAX-generated `DateTable`, while annual returning-customer analysis is connected through a separate `YearTable` and `fact_customer_year` table. This separates transaction-grain analysis from customer-year retention analysis and reduces ambiguous filter paths.

## Dashboard Design Goals

The three report pages are intentionally organized around different decision levels:

1. **Executive Overview** — overall performance and targets
2. **Product Performance** — product mix, profitability, and discount behavior
3. **Customer & Geography** — retention, customers, markets, countries, and discount bands

This structure keeps executive KPIs separate from drill-down diagnostics while allowing consistent slicers across the report.
