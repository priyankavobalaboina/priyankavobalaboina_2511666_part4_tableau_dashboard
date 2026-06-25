# priyankavobalaboina_2511666_part4_tableau_dashboard
# Part 4: Tableau Executive Dashboard & Data Storytelling

## Business Problem Summary

The retail leadership team requires an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns across Indian markets. The goal is to identify business opportunities and risks to support data-driven decision-making.

## Dataset Description

| Attribute | Detail |
|-----------|--------|
| File | `dashboard_sales_data.xlsx` |
| Records | 4,200 orders |
| Time Period | January 2024 – December 2025 |
| Regions | North, South, East, West |
| States | 19 unique states |
| Cities | 20 unique cities |
| Categories | Furniture, Office Supplies, Technology |
| Sub-categories | 13 (Tables, Storage, Accessories, Furnishings, Labels, Art, Copiers, Chairs, Binders, Phones, Paper, Machines, Bookcases) |
| Customer Segments | Consumer, Corporate, Home Office |
| Ship Modes | Standard Class, Second Class, First Class, Same Day |
| Campaign Channels | Organic, Social, Referral, Paid, Email |

### Field Types

- **Date fields**: order_date, ship_date
- **Geographic fields**: region, state, city
- **Categorical fields**: customer_segment, category, sub_category, product_name, ship_mode, campaign_channel
- **Numerical measures**: sales, quantity, discount, profit, delivery_days, customer_rating
- **Binary/flag fields**: return_flag (1 = returned, 0 = not returned)

## Tableau Workbook Description

The workbook `executive_dashboard.twbx` contains:
- 1 Executive Dashboard
- 7+ individual worksheet views
- 5+ calculated fields
- Interactive filters and dashboard actions

## Calculated Fields Created

| Calculated Field | Tableau Formula | Purpose |
|-----------------|-----------------|---------|
| Profit Margin | `[Profit] / [Sales]` | Measures profitability as a percentage of revenue |
| Cost | `[Sales] - [Profit]` | Derives the cost component from sales and profit |
| Average Order Value | `[Sales] / COUNTD([Order Id])` | Calculates revenue per unique order |
| Return Rate | `SUM([Return Flag]) / COUNT([Order Id])` | Measures the proportion of returned orders |
| Shipping Delay Bucket | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2 days)" ELSEIF [Delivery Days] <= 4 THEN "Normal (3-4 days)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Categorizes delivery performance into meaningful groups |
| Discount Category | `IF [Discount] = 0 THEN "No Discount" ELSEIF [Discount] <= 0.1 THEN "Low (1-10%)" ELSEIF [Discount] <= 0.2 THEN "Medium (11-20%)" ELSE "High (21%+)" END` | Groups discount levels for analysis |

## Dashboard Components

### KPI Cards (Top Section)
1. Total Sales (₹21.70 Cr)
2. Total Profit (₹3.33 Cr)
3. Profit Margin (15.35%)
4. Total Orders (4,200)
5. Return Rate (4.55%)

### Charts/Views Included
1. **Sales Trend View** – Line chart showing monthly sales over 2024-2025
2. **Regional Performance View** – Bar chart showing sales and profit by region
3. **Category Profitability View** – Bar chart showing profit by category and sub-category
4. **Customer Segment View** – Bar chart comparing segments by sales, profit, and return rate
5. **Shipping Performance View** – Bar chart showing delivery days by ship mode
6. **Discount vs Profit View** – Scatter plot showing discount-profit relationship
7. **Return Analysis View** – Bar chart showing return rates by category

## Filters and Interactions Used

### Interactive Filters
1. **Region** – Filter all views by geographic region
2. **Category** – Filter by product category
3. **Customer Segment** – Filter by Consumer, Corporate, or Home Office
4. **Date Range** – Filter by order date
5. **Ship Mode** – Filter by shipping method
6. **Campaign Channel** – Filter by acquisition channel

### Dashboard Actions
- **Filter Action**: Clicking on a region in the Regional Performance chart filters all other views to show data for that region only
- **Highlight Action**: Hovering over a category highlights related data across views

## Key Business Insights

1. Technology drives 71% of total sales (₹15.39 Cr) with the highest profit margin (18.22%)
2. Furniture has the highest return rate (7.67%) — nearly double the overall average
3. Discounts above 30% result in negative profit margins (-4.95%)
4. Home Office segment has the highest return rate (5.67%) despite strong sales
5. South region leads in total sales (₹6.47 Cr) and profit (₹1.00 Cr)
6. Standard Class shipping accounts for 58% of orders but has the longest average delivery (4.7 days)
7. Sales show seasonal peaks in Feb, Sep-Oct and dips in Apr-May, Aug
8. Sub-categories Copiers, Accessories, Phones, and Machines drive 84% of total profit

## Dashboard Story Summary

The business is performing well overall with a 15.35% profit margin. Technology is the growth engine, while Furniture presents both risk (high returns, low margins) and opportunity (high revenue potential if returns are reduced). Aggressive discounting (>30%) destroys value. The Home Office segment needs attention due to elevated return rates. Regional performance is balanced, suggesting a well-distributed market presence.

## Assumptions and Limitations

### Assumptions
- Sales and profit values are in Indian Rupees (₹)
- Return_flag = 1 indicates a completed return (not just initiated)
- Delivery_days represents business days between order and ship date
- All records are valid transactions (no test/dummy data)
- Campaign_channel with missing values (~32 records) treated as "Unknown"

### Limitations
- No customer lifetime value data available
- No product cost breakdown (only derived cost)
- No reason codes for returns
- No competitor benchmarking data
- Two-year window may not capture long-term trends
- No inventory or stock-out data to explain sales dips

## Screenshots Included

| Screenshot | Description |
|-----------|-------------|
| `full_dashboard.png` | Complete executive dashboard with all views and filters |
| `sales_trend_view.png` | Monthly sales line chart for 2024-2025 |
| `regional_performance_view.png` | Sales and profit by region bar chart |
| `category_profitability_view.png` | Category and sub-category profit analysis |
| `filter_interaction_view.png` | Dashboard with filter applied showing interaction |
