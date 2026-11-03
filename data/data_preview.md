## Data Overview

The analysis is built on a single order-level extract of **180,520 rows and 50 columns**, covering **1 Jan 2015 to 31 Jan 2018**. Each row is one order line, so an order with several products appears on several rows. This is why the extract holds 180,520 rows against **384,079 units sold** (about 2.1 units per row) and **20,652 distinct customers** (about 8.7 order lines per customer).
![DataTable](../assets/Data_Preview1.PNG)
Definitions are in [`docs/data_dictionary.md`](docs/data_dictionary.md). Measure logic is in [`docs/dax_measures.md`](docs/dax_measures.md).

## Data Model (Star Schema)

The model follows a **star schema**: one central fact table at order-line grain, surrounded by dimension tables that describe who, what, where, when and how. Every dimension relates to the fact table one-to-many, with filters flowing from the dimension to the fact.

**Why a star schema.**
- **Time intelligence needs a proper date table.** `DATESYTD` and `SAMEPERIODLASTYEAR` only work on a continuous, marked date table. `Dim_Date` should run from 1 Jan 2014 to 31 Dec 2018 so that prior-year comparisons exist for the first months of 2015.
- **One slicer filters every visual.** Order Region, Product Category and Customer Segment each live in one place, so the same selection flows to all four pages.
- **Customer counts come from the right grain.** Counting distinct Customer Id in the fact table gives 20,652 buyers, while a row count would give 180,520. Because it respects date filters, it also gives the correct count for YTD and prior-year windows.
- **A lighter, faster model.** Of the 50 source columns, only the fields the report needs are loaded, and repeated text attributes sit in small dimensions rather than 180,520 times in the fact table.
![DataModel](../assets/Data_Model.PNG)
