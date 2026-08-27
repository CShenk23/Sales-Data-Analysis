# Data Source Notes

The Power BI project was built from a cleaned e-commerce workbook containing transaction, customer, product, geography, and customer-year analytical tables.

The primary model tables are:

- `fact_orders_clean`
- `dim_customer`
- `dim_product`
- `fact_customer_year`

The source workbook available during project development was `skincare_beauty_powerbi_build_kit.xlsx`.

## Why the workbook is not committed here

This repository deployment is focused on the reproducible Power BI model, DAX, theme, dashboard specification, and documented findings. The connected GitHub publishing interface used for this deployment supports text-based repository files but did not provide a safe direct binary upload path for the workbook or a finished `.pbix` file.

To reproduce the model, place the workbook in this folder and follow the root README instructions.

Recommended local structure:

```text
data/
├── README.md
└── skincare_beauty_powerbi_build_kit.xlsx
```

Do not load the workbook's old `dim_date` or summary tabs into the final Power BI model. Use the DAX-generated `DateTable` and `YearTable` documented in `../dax/powerbi_measure_pack.dax`.
