# Retail Sales Analysis — Power BI Mini Project

End-to-end Power BI project: 5-table relational retail dataset, cleaned in Power Query,
modeled as a star schema, analyzed with DAX, and visualized across multiple dashboard pages.

## Dataset (star schema)

| Table | Rows | Role | Key |
|---|---|---|---|
| `Orders.csv` | ~600 | Fact (order header) | order_id, customer_id, employee_id |
| `Order_Items.csv` | ~1500 | Fact (line items) | order_item_id, order_id, product_id |
| `Customers.csv` | 120 | Dimension | customer_id |
| `Products.csv` | 50 | Dimension | product_id |
| `Employees.csv` | 8 | Dimension (salespeople) | employee_id |

**Relationships (all 1:\*):**
- `Customers[customer_id]` → `Orders[customer_id]`
- `Employees[employee_id]` → `Orders[employee_id]`
- `Orders[order_id]` → `Order_Items[order_id]`
- `Products[product_id]` → `Order_Items[product_id]`
- `DateTable[Date]` → `Orders[order_date]` (build this table in Power BI)

`Orders` + `Order_Items` are Fact tables; `Customers`, `Products`, `Employees`, `DateTable` are Dimension tables.

**Intentional data-quality issues** (for Power Query cleaning practice):
- Inconsistent casing/whitespace in `city` (`"  mumbai "`, `"DELHI"`)
- Mixed date format in one `order_date` (`2023/05/14`)
- Lowercase `payment_method` value (`"cash"`)
- A few blank `region` / `email` values
- Duplicate order rows
- A null `quantity` and a negative `unit_price` in `Order_Items`

## Project Checklist

- [ ] Import all 5 CSVs into Power BI
- [ ] Power Query: fix casing, trim whitespace, fix date format, remove duplicates, handle nulls/negatives
- [ ] Build `DateTable` with `CALENDAR()`, mark as date table
- [ ] Build relationships (star schema) in Model view
- [ ] Core measures: Total Revenue, Total Orders, Total Items Sold, Average Order Value, Total Profit
- [ ] Time Intelligence measures: MTD, YTD, YoY Growth
- [ ] Page 1 — Overview: KPI cards + region/category revenue + trend line
- [ ] Page 2 — Customer Insights: top customers, repeat vs new, city-wise
- [ ] Page 3 — Product Insights: category performance, top/bottom products, profit margin
- [ ] Page 4 — Sales Team: salesperson leaderboard, target vs achieved (if added)
- [ ] Slicers: date range, region, category on every page
- [ ] Navigation buttons + drill-through (Order details by customer/product)
- [ ] Formatting: consistent theme, data labels, titles
- [ ] Publish to Power BI Service
- [ ] Push `.pbix`, screenshots, and this README to GitHub

## Tech Stack
Power BI Desktop · Power Query (M) · DAX · Star Schema Data Modeling

## Author
[Mohd] — Data Analyst Mini-project 
