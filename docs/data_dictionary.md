# Data Dictionary (fields observed in each report)

| Field | Type | Description |
|---|---|---|
| Order Date | Date | Order date (1 Jan 2015 to 31 Jan 2018), via `Dim_Dates` |
| Order Region | Text | Sales region (for example Central America, Western Europe, North Africa, Oceania, South of USA, Caribbean) |
| Market | Text | Market grouping (Africa, LATAM and others) |
| Customer Segment | Text | Consumer, Corporate, Home Office |
| Department Name | Text | For example Fan Shop, Apparel, Footwear, Outdoors |
| Product Category Name | Text | For example Fishing, Cleats, Camping & Hiking |
| Sales | Currency | Order sales value |
| Order Profit | Currency | Profit on the order |
| Order Item Quantity | Whole number | Units ordered |
| Late Delivery Risk | Category | High Risk / Low Risk classification |
| Delivery Days | Number | Days from order to delivery |
| Total Customers | Whole number | Distinct customers (20,652 in the full window), from `Dim_Customer` |

Add data types, null handling and source-system notes once confirmed against the source file.
