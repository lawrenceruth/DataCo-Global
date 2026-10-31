# DataCo Global: Sales & Customer Intelligence Dashboard

> **Business question:** Where is DataCo Global earning and losing profit across customer segments, regions and product categories, and what does delivery performance mean for where management should invest next?

---

## Executive Summary

DataCo Global generated **$36.78M in sales**, **$3.97M in profit** (a **10.8% net margin**) and **384K units** across the reporting window (1 Jan 2015 to 31 Jan 2018). Against the prior-period comparison the dashboard reports growth of **+43.3% in sales, +44.6% in profit and +33.6% in units**. Because sales grew about 10 points faster than volume, revenue per unit rose from roughly **$89.44 to $95.78 (about +7%)**. That points to a price and mix lift as well as volume growth. Margin was essentially flat (10.7% to 10.8%), so growth has not been bought with discounting.

Three patterns shape the recommendations:

1. **Concentration.** Consumer delivers **51.91% of sales ($19.1M)**. Corporate adds **30.36% ($11.17M)** and Home Office **17.73% ($6.52M)**. The top two segments account for 82% of revenue.
2. **Profit sits in a few categories and regions.** Fishing is the top profit category at **$756,220.76 (about 19% of total profit)**. Western Europe and Central America lead profit by region.
3. **Delivery is the early-warning signal.** Average delivery time is **3 days**, but the January 2018 YTD figure is **4 days**, alongside a YTD margin of **10.2%** (against 10.8% for the full period).

---

## Business Context

DataCo Global is a multinational B2C company selling a wide product portfolio across several markets (Africa, Europe, LATAM, Pacific Asia and USCA). Its customer base is growing fast, and leadership wants a single view of:

- sales performance over time
- profit contribution by region and category
- how delivery performance and customer-service indicators affect business outcomes
- customer segmentation and regional trends

This repository holds the analytical model, the Power BI report and the supporting documentation that answer those questions.

## Objectives

1. Turn raw order-level data into a clean analytical model with consistent KPIs (sales, profit, quantity, delivery time, customers).
2. Track each KPI as a total, against the prior period and year-to-date (YTD).
3. Quantify profit contribution by **region**, **customer segment** and **product category**.
4. Measure delivery performance and late-delivery risk by region.
5. Convert the findings into prioritised, number-backed recommendations for management.

## Data Overview

| Item | Detail |
|---|---|
| Subject area | B2C order, product, customer and shipping data for DataCo Global |
| Time window | 1 Jan 2015 to 31 Jan 2018 (date slicer range in the report) |
| Dimensions | Order Region, Market, Customer Segment (Consumer / Corporate / Home Office), Department, Product Category, Order Date, Delivery Status |
| Measures | Sales, Order Profit, Order Item Quantity, Delivery Days, Late Delivery Risk, Customers |
| Delivery status values | Advance shipping, Shipping on time, Late delivery, Shipping canceled |
| Model | Star-schema style model built in Power BI (fact orders + date, geography, product and customer dimensions) |

Full field definitions are in [`docs/data_dictionary.md`](docs/data_dictionary.md). Measure logic is in [`docs/dax_measures.md`](docs/dax_measures.md).

## Key Findings

**1. Scale and profitability.** Sales of $36.78M and profit of $3.97M give a 10.8% margin. Average revenue is $95.78 per unit and average profit about $10.34 per unit. The prior-period comparison shows $25.67M sales, $2.74M profit and 287K units, a margin of 10.7%.

**2. Growth is more price/mix than volume.** Sales growth (+43.3%) outpaced unit growth (+33.6%) by 9.7 percentage points. Profit growth (+44.6%) edged ahead of sales growth, so the margin held.

**3. Early 2018 shows margin and service pressure.** January 2018 YTD gives $331.65K sales, $33.84K profit (10.2% margin), about 2K units and a 4-day average delivery time against 3 days previously.

**4. Segment concentration.** Consumer, Corporate and Home Office contribute 51.91%, 30.36% and 17.73% of sales. The single largest region-segment node is Western Europe Consumer at **$3,084,308.52 (8.4% of total sales)**.

**5. Home Office dilutes margin.** In the segment view ($15.28M of sales, $1.68M of profit), margins are:

| Segment | Share of sales | Share of profit | Margin | Profit-to-sales index |
|---|---|---|---|---|
| Consumer | 51.94% | 53.01% | 11.2% | 1.02 |
| Corporate | 30.32% | 30.83% | 11.2% | 1.02 |
| Home Office | 17.73% | 16.16% | 10.0% | 0.91 |

Corporate earns the same margin as Consumer, so growing Corporate does not dilute profitability.

**6. Profit leader is not the volume leader.** The top profit categories are Fishing, Cleats, Camping & Hiking, Cardio Equipment and Women's Apparel. The weakest are Crafts, Children's Clothing, Cameras and Garden. Cleats leads units in every segment (38K Consumer, 22K Corporate, 14K Home Office, about 46.5% of the 159K units in the segment view). Consumer Fishing sells only 9K units yet ranks first for profit.

**7. Department concentration.** Fan Shop contributes **$9,818,647.44, or 64.3% of the $15.28M** in the segment view. Apparel is a distant second, and Technology, Outdoors and Footwear are marginal.

**8. Geography.** Western Europe and Central America are the largest profit contributors, followed by South America, Southeast Asia and East of USA. Europe and LATAM carry the largest unit volumes in each segment.

**9. Demand step-change.** Daily sales ran at roughly $15K to $20K from January 2015 to mid-2017, then rose to a peak near $100K in late 2017. This pattern drives most of the reported growth. It needs validation (genuine demand versus a change in order capture) before it is used for forecasting.

## Recommendations

| # | Recommendation | Evidence | Indicative impact |
|---|---|---|---|
| 1 | **Ring-fence the core.** Prioritise stock, marketing and service levels for Consumer in Western Europe and Central America. | Consumer is 51.91% of sales. Western Europe Consumer alone is $3.08M. | Protects about half of revenue |
| 2 | **Close the Home Office margin gap.** Review discounting and bundle pricing for Home Office to reach margin parity with Consumer and Corporate (about 11.2%). | Home Office margin is 10.0% against 11.2%. | About +1.2 pp on $6.52M, roughly $75K profit |
| 3 | **Grow Corporate through category bundles.** Offer B2B bundles around Cleats and Indoor/Outdoor Games. | Corporate margin matches Consumer. Corporate Cleats is 22K units and Indoor/Outdoor Games 18K. | Growth without margin dilution |
| 4 | **Rebalance the portfolio.** Cross-sell Fishing to Cleats buyers. Run an SKU-rationalisation review of Crafts, Children's Clothing, Cameras and Garden. Reduce dependence on Fan Shop (64.3%). | Fishing leads profit at $756K, and the tail categories contribute least. | Higher profit per unit and lower concentration risk |
| 5 | **Restore the 3-day delivery standard.** Set a 3-day SLA and a late-delivery-rate KPI. Run a carrier and ship-mode root-cause analysis, starting with the largest-profit regions. | YTD delivery time is 4 days against 3 days previously. | Protects margin and repeat purchase |
| 6 | **Validate the late-2017 demand spike before planning capacity.** Reconcile order counts and dates with the source system, then build a monthly forecast. | Daily sales rose from about $15K–$20K to a peak near $100K. | Avoids over- or under-stocking |

## Dashboard Pages

| Page | Purpose |
|---|---|
| Executive Dashboard | Headline KPIs (sales, profit, quantity, delivery time), with prior-period and YTD comparison, sales by region and segment, profit by category |
| Sales Analysis | Sales by department, late-delivery risk by region, sales trend over time |
| Customer Analysis | Customer count, sales and profit by segment, unit volume by segment and market |
| Recommendation | Profit by region, delivery risk and sales trend supporting the actions above |
| Product Analysis | Product and category-level drill-down |

## Data Quality Notes and Limitations

- The Sales, Customer and Recommendation pages carry a product-category filter, so their totals ($15.28M sales, $1.68M profit, 159K units) differ from the Executive Dashboard ($36.78M, $3.97M, 384K). Headline figures in this README come from the Executive Dashboard. Segment and department findings are labelled as the filtered view.
- YTD in this report covers 1 to 31 January 2018 only (one month), so it is a directional signal, not a trend.
- Growth percentages are as reported by the dashboard. The comparison basis is being aligned to like-for-like YTD versus prior-year YTD. See [`docs/review_log.md`](docs/review_log.md).
- Late-delivery counts and the customer count are under validation. See the review log.

## Repository Structure

```
dataco-sales-customer-intelligence/
├── README.md
├── data/
│   ├── raw/                  # source extract (or download link if too large for Git)
│   └── processed/            # cleaned model tables
├── powerbi/
│   └── Lawrence_Ruth_BI_Capstone_Project.pbix
├── docs/
│   ├── project_brief.md
│   ├── data_dictionary.md
│   ├── dax_measures.md
│   ├── insights_and_recommendations.md
│   └── review_log.md
└── images/                   # one screenshot per report page
```

## Tools

Power BI (data model, DAX, report design), Power Query (cleaning and transformation), GitHub (version control and documentation).

## Author

Ruth Lawrence, Junior Data Analyst. Reviewed by the Senior Data Analyst before submission.
