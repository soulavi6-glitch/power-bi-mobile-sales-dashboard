# power-bi-mobile-sales-dashboard
# Mobile Sales Dashboard (Power BI)

Interactive Power BI dashboard analysing 3 years of mobile phone sales (Oct 2021 – Oct 2024): sales by city, model and brand, monthly sales volume, payment methods and customer ratings.

## Tools Used

- Power BI Desktop
- Power Query (data cleaning and transformation)
- DAX (measures)

## Dashboard Preview

![Dashboard overview](dashboard.png)

## Dataset

Mobile sales data from an Excel file (practice dataset) with **3,835 transactions**, **5 brands**, **15 mobile models** and **19 cities**.

Columns: Transaction ID, Date, Day Name, Brand, Mobile Model, Units Sold, Price Per Unit, Customer Name, Customer Age, City, Payment Method, Customer Ratings.

## Data Preparation (Power Query)

- Loaded the Excel sheet and promoted the first row to headers
- Set correct data types (whole numbers, decimals, text)
- Built a proper `DATE` column by combining the separate Day, Month and Year columns, then converted it to a date type
- Removed the separate Day, Month and Year columns
- Created `Day Name` from the date to analyse sales by weekday

## Data Model

Single table (`sales_data`) with an auto-generated date hierarchy (Year, Quarter, Month, Day) used for the month slicer and the trend chart.

## DAX Measures

| Measure | DAX | Purpose |
| ------- | --- | ------- |
| Total_sales_ammount | `SUMX(sales_data, sales_data[Units Sold] * sales_data[Price Per Unit])` | Total sales value, calculated row by row |
| Total_Quantity | `SUM(sales_data[Units Sold])` | Total units sold |
| Transaction | `COUNTROWS(sales_data)` | Number of transactions |
| Average | `AVERAGE(sales_data[Price Per Unit])` | Average price per unit |

## Dashboard Visuals

| Visual | What it shows |
| ------ | ------------- |
| 4 KPI cards | Total sales, total units sold, number of transactions, average price per unit |
| Map | Sales by city |
| Line chart | Units sold by month and day |
| Month slicer | Filters the whole dashboard by month |
| Bar chart | Sales by mobile model |
| Pie chart | Transactions by payment method |
| Funnel chart | Customer ratings |

## Questions the Dashboard Answers

1. Which cities bring in the most sales?
2. Which mobile models sell the most?
3. How do units sold change over time?
4. How do customers pay?
5. How satisfied are customers?

## Key Insights

- **Total sales:** about 769.2 million from 19,150 units across 3,835 transactions. Average price per unit is about 40,114.
- **Two cities lead:** Delhi (26.5%) and Mumbai (16.5%) together make up 43% of total sales. Every other city is at about 4% or less.
- **No single brand dominates:** Apple 21.0%, Samsung 20.8%, OnePlus 20.0%, Vivo 19.5% and Xiaomi 18.7% are all within about 2 points of each other.
- **Top models by sales:** iPhone SE (59.6M), OnePlus Nord (57.9M) and Galaxy Note 20 (56.0M). Redmi 9 is the lowest at 44.7M.
- **Payments are evenly split:** UPI 26.4% of transactions, Debit Card 24.7%, Credit Card 24.7%, Cash 24.2%.
- **Customer ratings:** 60.8% of transactions are rated 4 or 5 stars (38.8% are 5 stars), while 22.3% are rated 1 or 2 stars.
- **Monthly sales are fairly steady:** apart from the partial first and last months, the highest month is July 2022 (24.7M) and the lowest is September 2024 (18.6M).

## Files

- `final dashboard.pbix`: Power BI dashboard file
- `dashboard.png`: dashboard screenshot
