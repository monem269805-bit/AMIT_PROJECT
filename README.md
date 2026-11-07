# Phone Market Dashboard - Power BI Project (PBIP)

## Open it
1. Unzip to `C:\PhoneProject\` (keeps the default CSV path working).
2. Double-click `PhoneProject.pbip` (Power BI Desktop, current version).
3. If the data does not load: Home > Transform data > Manage parameters > set `CsvPath` to the full path of `data\phone_search.csv`, then Close & Apply.
4. To get a .pbix: File > Save As > choose .pbix.

## Power Query steps (table `phones`)
Remove duplicate ASINs (25) | strip `$` and convert prices to decimal | decode `&amp;` / `&quot;` in titles |
parse `sales_volume` ("4K+ bought in past month" -> 4000) into `sales_volume_num`, junk text -> null |
set boolean/number types | nulls: currency -> USD, coupon -> "No coupon", availability -> "Not specified",
original price / rating / price left null (blank = no value, excluded from averages) | drop empty unit_price, unit_count.

## DAX
Columns: Price Gap (original - min offer), Price Gap %, Badge, Prime Label, Climate Label, Price Band (+ sort order).
Measures: Avg Product Price, Avg Star Rating, Total Sales Volume, Sales per Product, Number of Offers,
Best Sellers Count, Amazon Choice Count, Prime %, Climate Friendly %, Avg Price Gap, Est. Revenue, Product Count.

## Why each visual
- KPI cards: headline numbers at a glance.
- Donuts (Prime, Climate, Badge): part-to-whole with 2-4 categories.
- Column charts by Price Band: compare sales and discount depth across ordered groups.
- Bar chart: Prime vs Non-Prime rating comparison.
- Scatter: relationship between price, rating and sales (3 variables).
- Table: exact side-by-side values for Best Seller / Amazon's Choice / Regular.

## Values to expect after dedup (315 products) - use to verify
Avg price ~ $160.15 | Avg rating ~ 4.08 | Total sales volume (min) 130,800 | Offers 2,632 |
Avg price gap ~ $78.54 (134 products have both prices) | Climate friendly 23.5% | Prime 72.4% |
Best sellers 2 | Amazon's Choice 1.
