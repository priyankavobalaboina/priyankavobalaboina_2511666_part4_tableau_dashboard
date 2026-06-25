
# Business Insights

## Calculated Fields Explanation

| # | Calculated Field | Formula in Tableau | Logic |
|---|-----------------|-------------------|-------|
| 1 | Profit Margin | `[Profit] / [Sales]` | Divides profit by sales to get profitability percentage per transaction |
| 2 | Cost | `[Sales] - [Profit]` | Derives cost by subtracting profit from sales revenue |
| 3 | Average Order Value | `[Sales] / COUNTD([Order Id])` | Total sales divided by distinct order count to get per-order revenue |
| 4 | Return Rate | `SUM([Return Flag]) / COUNT([Order Id])` | Proportion of orders that were returned |
| 5 | Shipping Delay Bucket | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2 days)" ELSEIF [Delivery Days] <= 4 THEN "Normal (3-4 days)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Groups delivery days into business-meaningful categories |
| 6 | Discount Category | `IF [Discount] = 0 THEN "No Discount" ELSEIF [Discount] <= 0.1 THEN "Low (1-10%)" ELSEIF [Discount] <= 0.2 THEN "Medium (11-20%)" ELSE "High (21%+)" END` | Categorizes discount levels for impact analysis |

---

## Insight 1: Sales Trend – Seasonal Patterns with Growth Stability

**Observation**: Monthly sales fluctuate between ₹63 Lakh and ₹1.09 Cr, with identifiable seasonal peaks and troughs across 2024-2025.

**Data Evidence**:
- Peak months: Feb 2024 (₹1.05 Cr), Sep 2024 (₹1.05 Cr), Aug 2025 (₹1.09 Cr)
- Trough months: Aug 2024 (₹63 Lakh), Apr 2025 (₹72 Lakh), Jun 2025 (₹73 Lakh)
- Average monthly sales: ~₹90 Lakh

**Business Interpretation**: The business experiences predictable seasonal dips in April-May (post-financial year) and mid-year (Jun-Aug). Peaks align with Q3 (Sep-Oct) and early Q1 (Jan-Feb), likely driven by corporate procurement cycles and festive season demand.

**Recommended Action**: Plan inventory buildup and marketing campaigns 4-6 weeks before peak months. Consider promotional offers during trough months (Apr-May) to smooth revenue.

---

## Insight 2: Regional Performance – South Leads but All Regions Are Balanced

**Observation**: The South region generates the highest sales and profit, but all four regions maintain similar profit margins (15.1%–15.6%).

**Data Evidence**:
- South: ₹6.47 Cr sales, ₹1.00 Cr profit (15.44% margin), 1,210 orders
- North: ₹5.46 Cr sales, ₹0.83 Cr profit (15.24% margin), 1,056 orders
- West: ₹4.89 Cr sales, ₹0.74 Cr profit (15.14% margin), 1,037 orders
- East: ₹4.89 Cr sales, ₹0.76 Cr profit (15.55% margin), 897 orders

**Business Interpretation**: The business has a well-distributed geographic presence. South's lead is driven by higher order volume (1,210 orders) rather than higher margins. East has the fewest orders but the highest margin, suggesting untapped potential.

**Recommended Action**: Invest in expanding East region order volume through targeted marketing. Maintain current strategies in South. Investigate why East has fewer orders despite strong profitability.

---

## Insight 3: Category Profitability – Technology Dominates, Furniture Struggles

**Observation**: Technology generates 71% of total sales and 84% of total profit, while Furniture has the lowest profit margin despite significant revenue.

**Data Evidence**:
- Technology: ₹15.39 Cr sales, ₹2.80 Cr profit, 18.22% margin
- Furniture: ₹5.16 Cr sales, ₹0.36 Cr profit, 6.89% margin
- Office Supplies: ₹1.15 Cr sales, ₹0.17 Cr profit, 14.85% margin

**Business Interpretation**: The business is heavily dependent on Technology for profitability. Furniture's low margin (6.89% vs. 18.22% for Technology) indicates either high costs, heavy discounting, or pricing issues in this category.

**Recommended Action**: Review Furniture pricing strategy and supplier costs. Consider reducing Furniture SKUs with negative margins. Protect and grow Technology category as the profit engine.

---

## Insight 4: Customer Segment Behavior – Home Office Returns Are Concerning

**Observation**: Home Office segment has the highest return rate at 5.67%, significantly above Consumer (3.91%) and Corporate (4.00%).

**Data Evidence**:
- Home Office: ₹7.45 Cr sales, 5.67% return rate, 1,446 orders
- Corporate: ₹7.06 Cr sales, 4.00% return rate, 1,399 orders
- Consumer: ₹7.19 Cr sales, 3.91% return rate, 1,355 orders

**Business Interpretation**: Home Office customers may have different expectations or purchasing patterns leading to higher dissatisfaction. This segment also has the highest order count, amplifying the return cost impact.

**Recommended Action**: Investigate root causes of Home Office returns (product mismatch? quality issues? delivery problems?). Implement better product descriptions and size guides for Home Office buyers. Consider a pre-purchase consultation service.

---

## Insight 5: Discount Impact – Aggressive Discounting Destroys Profit

**Observation**: Discounts above 30% result in negative profit margins, while zero-discount orders have the highest profitability.

**Data Evidence**:
- No Discount (0%): ₹6.58 Cr sales, 20.56% profit margin
- Low (1-10%): ₹5.76 Cr sales, 17.01% profit margin
- Medium (11-20%): ₹4.87 Cr sales, 13.63% profit margin
- High (21-30%): ₹4.29 Cr sales, 8.05% profit margin
- Very High (31-35%): ₹2.07 Cr sales, **-4.95% profit margin** (LOSS)

**Business Interpretation**: Each 10% increase in discount reduces profit margin by approximately 4-5 percentage points. At 31-35% discount, the company is selling at a loss. The 64 orders at 31-35% discount generated a net loss of ₹1.02 Lakh.

**Recommended Action**: Cap maximum discount at 25% unless approved by senior management. Eliminate 30%+ discounts immediately. Train sales team on profit-aware discounting. Implement discount approval workflows.

---

## Insight 6: Shipping/Delivery Performance – Standard Class Creates Delays

**Observation**: Standard Class shipping accounts for 58% of all orders but has the longest average delivery time (4.7 days), while Same Day and First Class are significantly faster.

**Data Evidence**:
- Same Day: 0.4 days average, 241 orders (5.7%)
- First Class: 1.8 days average, 630 orders (15%)
- Second Class: 2.7 days average, 894 orders (21.3%)
- Standard Class: 4.7 days average, 2,435 orders (58%)

**Business Interpretation**: The heavy reliance on Standard Class shipping means most customers experience 4-5 day delivery times. In an era of fast delivery expectations, this could impact customer satisfaction and repeat purchases.

**Recommended Action**: Negotiate better rates for First Class shipping to shift more orders to faster delivery. Offer free upgrade to Second Class for high-value orders. Monitor customer ratings correlation with delivery speed.

---

## Insight 7: Return Pattern – Furniture Returns Are a Major Risk

**Observation**: Furniture has a return rate of 7.67% — more than double Technology's rate (3.03%) and significantly above Office Supplies (3.65%).

**Data Evidence**:
- Furniture: 88 returns out of 1,147 orders (7.67%)
- Office Supplies: 61 returns out of 1,669 orders (3.65%)
- Technology: 42 returns out of 1,384 orders (3.03%)
- Overall: 191 returns out of 4,200 orders (4.55%)

**Business Interpretation**: Furniture items are likely returned due to size mismatch, quality not meeting expectations, or damage during shipping (larger items are more prone to transit damage). Each Furniture return is costly due to high shipping costs for bulky items.

**Recommended Action**: Add detailed dimensions and 360° product images for Furniture. Improve packaging for transit protection. Consider offering assembly services. Implement a "measure your space" tool on the website.

---

## Insight 8: Business Risk & Opportunity – Sub-Category Concentration Risk

**Observation**: Four Technology sub-categories (Copiers, Accessories, Phones, Machines) generate 84% of total profit (₹2.80 Cr out of ₹3.33 Cr), creating concentration risk.

**Data Evidence**:
- Copiers: ₹73.10 Lakh profit (21.9% of total)
- Accessories: ₹71.87 Lakh profit (21.6% of total)
- Phones: ₹70.97 Lakh profit (21.3% of total)
- Machines: ₹64.49 Lakh profit (19.4% of total)
- Remaining 9 sub-categories: ₹52.63 Lakh profit (15.8% of total)

**Business Interpretation**: While Technology drives growth, over-dependence on 4 sub-categories creates vulnerability. Any disruption (supply chain issues, competitor pricing, technology shifts) in these categories could severely impact overall profitability.

**Recommended Action**: Diversify profit sources by improving Furniture margins. Develop Office Supplies as a stable, high-volume profit contributor. Create contingency plans for Technology supply disruptions. Explore new sub-categories within Technology.

---

## Insight 9: Campaign Channel Effectiveness (Bonus Insight)

**Observation**: Orders come through 5 campaign channels (Organic, Social, Referral, Paid, Email), indicating a multi-channel acquisition strategy.

**Data Evidence**:
- All channels are represented across regions and segments
- Campaign channel data is available for analysis of customer acquisition cost effectiveness

**Business Interpretation**: A diversified acquisition strategy reduces dependency on any single channel. Analyzing profit per channel can reveal which channels bring the most valuable customers.

**Recommended Action**: Calculate customer lifetime value by campaign channel. Increase investment in channels that bring high-margin, low-return customers. Reduce spend on channels with high return rates.

---

## Insight 10: Average Customer Rating & Quality (Bonus Insight)

**Observation**: Average customer rating is 4.06 out of 5, with ratings ranging from 2.1 to 5.0.

**Data Evidence**:
- Mean rating: 4.06
- 25th percentile: 3.7
- 75th percentile: 4.4
- 32 records have missing ratings

**Business Interpretation**: Overall customer satisfaction is good but not exceptional. The spread (2.1 to 5.0) indicates inconsistent experiences. Low-rated orders may correlate with returns and delivery delays.

**Recommended Action**: Investigate orders with ratings below 3.5 for common issues. Correlate low ratings with delivery delays and return flags. Set a target to improve average rating to 4.3+ within 6 months.
