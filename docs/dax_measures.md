# DAX Measures

Table and column names follow the visible model (`_Measures`, `Dim_Dates`). Adjust the fact-table names to match.

## Existing measure (used in each report)

```DAX
YoY Avg. Del Time =
VAR CurrentShipmentdays      = [Avg Delivery Time]
VAR PreviousYearShipmentdays = CALCULATE ( [Avg Delivery Time], SAMEPERIODLASTYEAR ( 'Dim_Dates'[Date] ) )
VAR ShipmentdaysGrowth       = DIVIDE ( CurrentShipmentdays - PreviousYearShipmentdays, PreviousYearShipmentdays, 0 )
VAR Result =
    SWITCH (
        TRUE (),
        ShipmentdaysGrowth > 0, FORMAT ( ShipmentdaysGrowth, "0.0%" ) & UNICHAR ( 9660 ),
        ShipmentdaysGrowth < 0, FORMAT ( ShipmentdaysGrowth, "0.0%" ) & UNICHAR ( 9650 ),
        "0%"
    )
RETURN Result
```

## Other KPIs (same pattern)

```DAX
Total Sales       = SUM(FactSales[Sales])
Total Profit      = SUM(FactSales[Order Profit Per Order])
Total Qty         = SUM(FactSales[Order Item Quantity])
Total Customers         = DISTINCTCOUNT('FactSales'[Customer Id])

YTD Sales   = TOTALYTD(SUM(FactSales[Sales]),Dim_Dates[Date])
Prev Sales  = CALCULATE(SUM(FactSales[Sales]), SAMEPERIODLASTYEAR(Dim_Dates[Date]))
YoY Sales = VAR CurrentSales = [Total Sales] VAR PreviousYearSales = CALCULATE([Total Sales],SAMEPERIODLASTYEAR('Dim_Dates'[Date])) VAR SalesGrowth = DIVIDE(CurrentSales - PreviousYearSales, PreviousYearSales,0) VAR Result = Switch( TRUE(),SalesGrowth > 0, FORMAT(SalesGrowth, "0.0%") & UNICHAR(9650), SalesGrowth < 0, FORMAT(SalesGrowth, "0.0%") & UNICHAR(9660), "0%") RETURN result 

YTD Profit  = TOTALYTD(SUM(FactSales[Order Profit Per Order]),Dim_Dates[Date])
Prev. Profit = CALCULATE(SUM(FactSales[Order Profit Per Order]), SAMEPERIODLASTYEAR(Dim_Dates[Date]))
YoY Profit   = VAR CurrentOrderProfitPerOrder = [Total Profit] VAR PreviousYearOrderProfitPerOrder = CALCULATE([Total Profit],SAMEPERIODLASTYEAR('Dim_Dates'[Date])) VAR OrderProfitPerOrderGrowth = DIVIDE(CurrentOrderProfitPerOrder - PreviousYearOrderProfitPerOrder, PreviousYearOrderProfitPerOrder,0) VAR Result = Switch( TRUE(),OrderProfitPerOrderGrowth > 0, FORMAT(OrderProfitPerOrderGrowth, "0.0%") & UNICHAR(9650), OrderProfitPerOrderGrowth < 0, FORMAT(OrderProfitPerOrderGrowth, "0.0%") & UNICHAR(9660), "0%") RETURN result

YTD Avg. Del Time = TOTALYTD(AVERAGE(FactSales[Shipment Days (Actual)]),Dim_Dates[Date])
Prev Avg. Del Time = CALCULATE(AVERAGE(FactSales[Shipment Days (Actual)]), SAMEPERIODLASTYEAR(Dim_Dates[Date]))
YoY Avg. Del Time = VAR CurrentShipmentdays = [Avg Delivery Time] VAR PreviousYearShipmentdays = CALCULATE([Avg Delivery Time],SAMEPERIODLASTYEAR('Dim_Dates'[Date])) VAR ShipmentdaysGrowth = DIVIDE(CurrentShipmentdays - PreviousYearShipmentdays, PreviousYearShipmentdays,0) VAR Result = Switch( TRUE(),ShipmentdaysGrowth > 0, FORMAT(ShipmentdaysGrowth, "0.0%") & UNICHAR(9650), ShipmentdaysGrowth < 0, FORMAT(ShipmentdaysGrowth, "0.0%") & UNICHAR(9660), "0%") RETURN result

YTD Total Cust = TOTALYTD(COUNT(FactSales[Customer Id]),Dim_Dates[Date])
Prev Total Cus = CALCULATE(COUNT(FactSales[Customer Id]), SAMEPERIODLASTYEAR(Dim_Dates[Date]))
YoY Cus = VAR CurrentCustomerID = [Total Customers] VAR PreviousYearCustomerID = CALCULATE([Total Customers],SAMEPERIODLASTYEAR('Dim_Dates'[Date])) VAR CustomerIDGrowth = DIVIDE(CurrentCustomerID - PreviousYearCustomerID, PreviousYearCustomerID,0) VAR Result = Switch( TRUE(),CustomerIDGrowth > 0, FORMAT(CustomerIDGrowth, "0.0%") & UNICHAR(9650), CustomerIDGrowth < 0, FORMAT(CustomerIDGrowth, "0.0%") & UNICHAR(9660), "0%") RETURN result

YTD Avg. Del Time = TOTALYTD(AVERAGE(FactSales[Shipment Days (Actual)]),Dim_Dates[Date])
Prev Avg. Del Time = CALCULATE(AVERAGE(FactSales[Shipment Days (Actual)]), SAMEPERIODLASTYEAR(Dim_Dates[Date]))
YoY Avg. Del Time = VAR CurrentShipmentdays = [Avg Delivery Time] VAR PreviousYearShipmentdays = CALCULATE([Avg Delivery Time],SAMEPERIODLASTYEAR('Dim_Dates'[Date])) VAR ShipmentdaysGrowth = DIVIDE(CurrentShipmentdays - PreviousYearShipmentdays, PreviousYearShipmentdays,0) VAR Result = Switch( TRUE(),ShipmentdaysGrowth > 0, FORMAT(ShipmentdaysGrowth, "0.0%") & UNICHAR(9650), ShipmentdaysGrowth < 0, FORMAT(ShipmentdaysGrowth, "0.0%") & UNICHAR(9660), "0%") RETURN result

YTD Total Qty = TOTALYTD(SUM(FactSales[Order Item Quantity]),Dim_Dates[Date])
Prev total Qty = CALCULATE(SUM(FactSales[Order Item Quantity]), SAMEPERIODLASTYEAR(Dim_Dates[Date]))
YoY Total Qtd = VAR CurrentOrderItemQuantity = [Total Quantity Sold] VAR PreviousOrderItemQuantity = CALCULATE([Total Quantity Sold],SAMEPERIODLASTYEAR('Dim_Dates'[Date])) VAR Growth = DIVIDE(CurrentOrderItemQuantity - PreviousOrderItemQuantity, PreviousOrderItemQuantity,0) VAR Result = Switch( TRUE(),Growth > 0, FORMAT(Growth, "0.0%") & UNICHAR(9650), Growth < 0, FORMAT(Growth, "0.0%") & UNICHAR(9660), "0%") RETURN result

