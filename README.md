# priyankavobalaboina_2511666_part4_tableau_dashboard
 # Executive Sales Dashboard — README

## Project Overview

An interactive Tableau dashboard analyzing sales performance, profitability, and operational metrics for a retail business across the 2024-2025 fiscal period. The dashboard provides executive-level insights across regional performance, product categories, customer segments, discount impact, shipping efficiency, and return rates.

---

## Dataset

| Attribute | Detail |
|---|---|
| **File** | `dashboard_sales_data.xlsx` |
| **Records** | ~4,200 orders |
| **Time Period** | 2024-2025 |
| **Currency** | Indian Rupees (₹) |
| **Regions** | East, North, South, West |
| **Categories** | Furniture, Office Supplies, Technology |
| **Customer Segments** | Consumer, Corporate, Home Office |

### Key Fields Used

| Field | Type | Usage |
|---|---|---|
| Order ID | Dimension | Unique order identifier |
| Order Date | Date | Time-based analysis |
| Ship Date | Date | Shipping delay calculation |
| Ship Mode | Dimension | Shipping performance analysis |
| Customer Segment | Dimension | Segment analysis & filter |
| Region | Dimension | Regional performance & filter |
| Category | Dimension | Category profitability & filter |
| Sub-Category | Dimension | Detailed profitability breakdown |
| Sales | Measure | Revenue analysis |
| Profit | Measure | Profitability analysis |
| Discount | Measure | Discount impact analysis |
| Quantity | Measure | Order volume |
| Returns | Dimension | Return rate calculation |

### Calculated Fields Created in Tableau

| Field Name | Formula | Purpose |
|---|---|---|
| Profit Margin (%) | `SUM(Profit) / SUM(Sales) * 100` | KPI card & color encoding |
| Return Rate (%) | `COUNT(Returned Orders) / COUNT(Orders) * 100` | Heat map & shipping analysis |
| Shipping Delay (Days) | `DATEDIFF('day', [Order Date], [Ship Date])` | Shipping delay bucket creation |
| Shipping Delay Bucket | `IF [Shipping Delay] = 0 THEN "Same Day" ELSEIF [Shipping Delay] <= 2 THEN "Fast (1-2 days)" ELSEIF [Shipping Delay] <= 4 THEN "Standard (3-4 days)" ELSEIF [Shipping Delay] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Categorize shipping speed |

---

## Dashboard Components

### KPI Summary (Top Row)
- Total Sales: ₹217M
- Profit Margin: 15.35%
- Total Profit: ₹33.3M
- Return Rate: 4.55%

### Analytical Views (6 Charts)

| # | View Name | Chart Type | Key Insight |
|---|---|---|---|
| 1 | Regional Sales Performance | Horizontal Bar | South leads with ₹65M (30% of total) |
| 2 | Category Profitability | Grouped Horizontal Bar | Technology drives 84% of profit |
| 3 | Customer Segment | Grouped Vertical Bar | Home Office leads sales (₹74.5M) and profit (₹11.6M) |
| 4 | Discount Impact on Profitability | Scatter Plot | Negative correlation r = -0.27 |
| 5 | Shipping Delay Bucket | Horizontal Bar + Color | Standard shipping has highest volume (1,570) and returns (4.90%) |
| 6 | Return Rate by Category & Segment | Heat Map | Furniture + Home Office = 9.14% (highest risk) |

### Interactive Features
- **4 Filters:** Region, Category, Customer Segment, Shipping Delay Bucket
- **Filter Type:** Multiple Values (Checkbox List)
- **Filter Scope:** Applied to all worksheets using the data source
- **Filter Action:** Click on Regional Performance bar → filters entire dashboard to selected region

---

## File Structure

```
project/
├── dashboard_sales_data.xlsx          # Source data file
├── Executive_Sales_Dashboard.twbx     # Tableau Packaged Workbook
├── outputs/
│   ├── business_insights.md           # Key findings and recommendations
│   ├── dashboard_story.md             # Narrative walkthrough of the dashboard
│   ├── chart_selection_justification.md  # Chart type rationale for each view
│   └── README.md                      # This file
└── screenshots/
    ├── executive_dashboard.png        # Full dashboard screenshot
    ├── regional_performance_view.png  # Regional bar chart
    ├── category_profitability_view.png # Category profitability chart
    ├── customer_segment_view.png      # Customer segment grouped bars
    ├── discount_impact_view.png       # Scatter plot with trend lines
    ├── shipping_delay_bucket_view.png # Shipping delay horizontal bars
    ├── return_rate_heatmap_view.png   # Return rate highlight table
    └── shipping_performance_view.png  # Ship mode delivery speed chart
```

---

## How to Open

1. **Install** Tableau Desktop or Tableau Public (free)
2. **Open** `Executive_Sales_Dashboard.twbx` — this is a packaged workbook containing both the dashboard and data
3. **Navigate** to the "Executive Dashboard" tab at the bottom
4. **Interact** using the filters on the right panel or click any region bar to filter

---

## Design Decisions

| Decision | Rationale |
|---|---|
| Horizontal bars for Regional & Category | Readable labels without rotation; natural for categorical comparison |
| Scatter plot for Discount vs Profit | Only appropriate chart for two continuous variables showing correlation |
| Heat map for Return Rates | Compact 3×3 matrix reveals category×segment interaction patterns |
| KPIs at top | Information hierarchy — executives see summary first |
| Filters on right panel | Keeps main chart area uncluttered; accessible without scrolling |
| Color: Red/Green diverging for returns | Universal association — red = problem, green = healthy |
| Color: Blue gradient for profit | Single-hue gradient for ordered quantitative data |
| Removed gridlines | Improves data-ink ratio; reduces visual clutter |
| ₹K format for Category Profitability | Prevents Office Supplies values from displaying as ₹0M |

---

## Key Findings Summary

1. **South region** generates 30% of revenue — geographic concentration risk
2. **Technology** drives 84% of profit with 16-18% margins
3. **Discounts above 20%** consistently destroy profitability (r = -0.27)
4. **Home Office + Furniture** = 9.14% return rate — highest risk combination
5. **Same Day shipping** achieves 36% lower return rate than Standard shipping
6. **Customer segments** are well-balanced (~₹70-75M each) — diversification strength

---

## Tools & Technologies

- **Tableau Desktop** — Dashboard creation and visualization
- **Excel** — Source data format
- **Calculated Fields** — Profit Margin, Return Rate, Shipping Delay Bucket
- **Tableau Analytics** — Trend lines, reference lines, correlation coefficient

