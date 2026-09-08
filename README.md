# Office Solutions Sales Analysis and Recommendation Dashboard

Data analytics project using transaction-level sales data to identify profit drivers, underperforming products, regional opportunities, and practical recommendations for increasing sales.

## Business question

Office Solutions wants to increase overall sales by 20%. This project analyzes sales, profit, discounts, customer segments, regions, product categories, and order composition to identify where the business should focus its growth strategy.

## Recommendation

Office Solutions should focus growth efforts on high-margin products and profitable customer opportunities rather than expanding every product category equally.

The recommended strategy is to:

1. Prioritize high-profit products such as Copiers, Accessories, and Paper in corporate outreach and preferred product catalogs.
2. Reduce emphasis on persistently unprofitable categories, especially Tables, while reviewing product-level pricing and fulfillment costs.
3. Promote complementary product bundles and cross-selling, especially in the West and East regions.
4. Keep discounts controlled. The data shows positive profitability at lower discount levels and substantial losses at the highest discount levels.
5. Use corporate account acquisition and retention to support higher-value orders and recurring revenue.

## Key findings

- The dataset contains 9,994 sales transactions with approximately **$2.30M in sales** and **$286K in profit**.
- Profitability is concentrated in a small number of sub-categories. Copiers generated approximately **$55.6K profit** with a **37.2% margin**; Accessories generated **$41.9K**; and Paper generated **$34.1K**.
- Tables generated approximately **-$17.7K profit**, followed by Bookcases at **-$3.5K** and Supplies at **-$1.2K**.
- West and East were the strongest regions by sales, generating approximately **$725.5K** and **$678.8K**, respectively.
- Multi-item orders had an average order value of approximately **$716**, compared with **$208** for single-item orders.
- Discounting above 30% produced approximately **-$125K in total profit**, while the 0%-10% discount range produced approximately **$330K in total profit**.

## Power BI dashboard

The Power BI dashboard is designed to communicate the analysis through interactive views of:

- Sales and profit by region
- Sales and profit by customer segment
- Product and sub-category profitability
- Discount level versus profit
- Single-item versus multi-item order performance
- Recommended growth opportunities

## Dashboard resources
[View the Power BI dashboard PDF](office-solutions-business-performance-dashboard.pdf).

[View the dashboard build specification](dashboard-build-spec.md)
 
## Project files

```text
office-solutions-sales-analysis-PowerBI-dashboard/
├── README.md
├── TableauSalesData.xlsx
├── office-solutions-business-performance-dashboard.pdf
└── dashboard-build-spec.md
```

## Analysis workflow

1. Import the `Orders` worksheet from the Excel workbook into a SQL table named `sales_orders`.
2. Inspect columns, data types, missing values, and descriptive statistics.
3. Group sales and profit by category, sub-category, region, segment, and discount range.
4. Compare single-item and multi-item orders by grouping rows by `Order ID`.
5. Identify profitable products and categories that may support targeted growth.
6. Translate the findings into a business recommendation and Power BI dashboard design.

## Example SQL analysis

```sql
SELECT
    "Sub-Category",
    ROUND(SUM("Sales"), 2) AS total_sales,
    ROUND(SUM("Profit"), 2) AS total_profit,
    ROUND(SUM("Profit") / NULLIF(SUM("Sales"), 0) * 100, 2) AS profit_margin_percent
FROM sales_orders
GROUP BY "Sub-Category"
ORDER BY total_profit ASC;
```

This query summarizes sales, profit, and profit margin by sub-category and places loss-making sub-categories first.

## Tools

SQL · Microsoft Excel · Power BI · Data Visualization · Business Analysis

## Limitations

This analysis is based on historical transaction data and describes relationships in the dataset. 
It does not establish causation or guarantee that the recommended strategy will produce a 20% sales increase.
Additional testing should include a defined time period, measurable targets, product-level cost information,
and post-launch performance monitoring.
