# Project Brief

DataCo Global is a multinational B2C company with a rapidly growing customer base and a wide product portfolio. Executives want to understand:

- sales performance over time
- profit contribution by region and category
- customer segmentation and regional trends


As a Junior Data Analyst transform the company’s raw sales data into a clean analytical model and use it to create a professional dashboard and reports in Power BI.

## Your Tasks
Data Modeling (Star Schema Required),
Using the provided flat dataset, you are required to build a proper dimensional model following this structure:
Fact Table: FactSales

- FactSales ID
- Order Id
- Order Date
- Shipment Date
- Customer Id (FK → DimCustomer)
- Product Card Id (FK → DimProduct)
- Location Key (FK → DimLocation)
- Sales and order metrics (e.g., Sales, Quantity, Discount, Profit)
- Shipment metrics (e.g., Shipment Days, Delivery Status, Late Risk)

## Dimension Tables

DimCustomer

- Customer ID, Name, Segment, Address, State, Country


DimProduct

- Product ID, Name, Price, Status, Category, Department


DimLocation

- Location Key, Market, Region, City, Country, Latitude, Longitude


## DimDate
Create a custom Date Table from scratch using DAX or Power Query. This table must cover all dates present in the dataset and include standard calendar fields like:


- Date
- Year
- Month
- Quarter
- Month Name
- Week Number
- Day of Week

