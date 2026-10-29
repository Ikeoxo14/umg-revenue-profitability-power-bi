# Universal Music Group Revenue and Profitability

I built this two-page Power BI report to explore how Universal Music Group's revenue and profitability changed from 2022 to 2025, and which business segments contributed the most.

**Period:** 2022-2025  
**Financial amounts:** USD millions, unless stated otherwise  
**Tools:** Excel, Power Query, Power BI, and DAX

## Report Files

| File | Description |
| --- | --- |
| [View the PDF report](UMG_Revenue_Profitability_USD.pdf) | View both dashboard pages without Power BI. |
| [Download the Power BI report](UMG_Revenue_Profitability_USD.pbix) | Open the interactive report in Power BI Desktop. |
| [Download the Excel source data](UMG_Financial_Data.xlsx) | Review the annual figures, currency conversions, and source references. |

## Business Questions

- How have UMG's revenue and profitability changed over time?
- Which business segments generate the most revenue?
- How do adjusted EBITDA margins compare across segments?
- Does higher revenue consistently translate into higher net profit?

## Dashboard Pages

### Company Overview

- Selected-year cards for revenue, adjusted EBITDA, adjusted EBITDA margin, and net profit attributable to the parent.
- Annual revenue comparison for 2022-2025.
- Adjusted EBITDA and net profit trends.
- Annual results table with USD revenue growth, operating profit, and profitability measures.

The year slicer controls the KPI cards. The historical charts and annual table retain all four years for comparison.

### Business Segments

- Revenue comparison across Recorded Music, Music Publishing, and Merchandising and Other.
- Adjusted EBITDA margin comparison.
- Segment results table.
- Year slicer for comparing segment performance in a selected year.

## Key Findings

- Converted USD revenue increased from approximately **$10.89 billion in 2022 to $14.14 billion in 2025**.
- Group adjusted EBITDA margin increased from **20.6% to 22.5%** across the period. Both 2024 and 2025 round to 22.5%.
- **Recorded Music** generated the most segment revenue in 2025 and had the highest segment adjusted EBITDA margin at **25.6%**.
- **Merchandising and Other** had a 2025 adjusted EBITDA margin of **2.0%**, the lowest of the three segments.
- Net profit attributable to the parent declined in 2025 despite higher adjusted EBITDA. UMG attributed the decline mainly to lower gains from revaluing listed investments.

### 2025 Segment Comparison

| Segment | Revenue ($m) | Adjusted EBITDA ($m) | Adjusted EBITDA Margin |
| --- | ---: | ---: | ---: |
| Recorded Music | $10,690.95 | $2,739.44 | 25.6% |
| Music Publishing | $2,555.16 | $620.70 | 24.3% |
| Merchandising and Other | $916.92 | $18.09 | 2.0% |

## Data Preparation and Model

1. Organized the official group and segment financial results in Excel tables.
2. Preserved the original EUR figures and added annual exchange rates and converted USD columns.
3. Imported the named tables into Power BI and checked data types in Power Query.
4. Created a shared Years table and active, single-direction relationships to both financial tables.
5. Created DAX measures for financial totals, adjusted EBITDA margins, and USD revenue growth.
6. Configured slicer interactions and built the two report pages.

| Model Table | Purpose |
| --- | --- |
| UMG_Group | One row per year containing consolidated company results. |
| UMG_Segments | One row per segment per year containing segment results. |
| Years | Shared year filter connected to both financial tables. |

## Currency Conversion and Calculations

UMG reports these financial results in **EUR millions**. For this project, I converted the figures to **USD millions** using Federal Reserve annual average exchange rates.

| Year | USD per EUR |
| --- | ---: |
| 2022 | 1.0534 |
| 2023 | 1.0817 |
| 2024 | 1.0820 |
| 2025 | 1.1306 |

**USD millions = EUR millions x USD per EUR**

Core calculations:

- **Adjusted EBITDA margin:** Adjusted EBITDA / Revenue
- **Revenue YoY:** (Current-year USD revenue - Prior-year USD revenue) / Prior-year USD revenue

Example DAX measures:

~~~dax
UMG Revenue USD =
SUM(UMG_Group[Revenue_USDm])
~~~

~~~dax
UMG Adj EBITDA Margin =
DIVIDE(
    [UMG Adjusted EBITDA USD],
    [UMG Revenue USD]
)
~~~

## Interpretation Notes

- USD figures are analytical conversions of the reported EUR results. USD growth includes exchange-rate movements; it is not constant-currency growth.
- The 2025 USD revenue growth rate is **10.4%**. This differs from UMG's reported EUR growth rate of **5.7%** because of currency conversion.
- The 2022 YoY value is blank because 2021 is outside the dataset. A blank does not mean zero growth.
- Adjusted EBITDA is a **non-IFRS measure** and differs from net profit.
- Net profit refers to profit attributable to equity holders of the parent.
- Reported segment revenue includes intersegment transactions. Consolidated group results also reflect eliminations and unallocated corporate centre costs, so segment totals should not be treated as consolidated totals.

## How to Use

1. Open the PDF for a quick view of both report pages.
2. Download the PBIX file and open it in Power BI Desktop to use the interactive report.
3. Use the year slicers to explore selected-year results.
4. To refresh the report on another computer, update its Excel source path to the downloaded workbook before refreshing.

## Sources

- [UMG FY2023 results](https://assets.ctfassets.net/e66ejtqbaazg/1psEFHkZbqpN6GxbUUYhPL/eae1981f98c7c682e5d09a2b324e1df0/UMG_4Q___FY23_Press_Release.pdf) - source for 2022 and 2023 financial figures.
- [UMG FY2025 results](https://www.universalmusic.com/universal-music-group-n-v-reports-financial-results-for-the-fourth-quarter-and-full-year-ended-december-31-2025/) - source for 2024 and 2025 financial figures.
- [Federal Reserve G.5A annual exchange rates](https://www.federalreserve.gov/releases/g5a/20260105/) - source for the 2022-2025 USD-per-EUR rates.

## Author

**Ike Okoroafor**  
[GitHub: Ikeoxo14](https://github.com/Ikeoxo14)

