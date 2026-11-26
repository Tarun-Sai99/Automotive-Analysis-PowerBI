# Automotive Analysis using Power BI

An end-to-end data analysis project on a car sale advertisements dataset, built in Power BI Desktop as a Data Analyst portfolio project.

## Dataset

`car_ad.csv`: about 9,576 used-car listings, inspired by the Kaggle "Car Sale Advertisements" dataset.

| Column | Description |
|---|---|
| car | Manufacturer / brand |
| price | Listing price |
| body | Body type (sedan, crossover, van, ...) |
| mileage | Mileage |
| engV | Engine volume (litres) |
| engType | Engine / fuel type |
| registration | Whether the car is registered |
| year | Model year |
| model | Model name |
| drive | Drive type (front, rear, full) |

## Project plan

| Day | Focus | Status |
|---|---|---|
| 1 | Import CSV and clean data in Power Query | Done |
| 2 | Outlier handling, data model, core DAX measures | Done |
| 3 | Overview dashboard: KPIs, price distribution, listings by body type and brand | Planned |
| 4 | Trend analysis: price vs year, mileage vs price, engine type breakdown | Planned |
| 5 | Brand and segment deep dive with slicers | Planned |
| 6 | Polish: formatting, tooltips, bookmarks, drill-through, mobile layout | Planned |
| 7 | Final review, insights write-up, publish | Planned |

## Day 1: Data import and cleaning

- Imported `car_ad.csv` with **Get Data > Text/CSV > Transform Data**, so cleaning happens in Power Query before loading.
- **Engine volume (`engV`)**: the column was text with `"NA"` strings mixed in. Replaced `"NA"` with null and changed the type to Decimal Number, so missing values are handled correctly in calculations.
- **Duplicates**: removed true full-row duplicates with `Table.Distinct` across all columns (deduplicating on a single column would wrongly drop distinct cars that share a value).
- **Noted for Day 2**: listings with `price = 0` or `mileage = 0` looked suspicious and were investigated on Day 2.

## Day 2: Outlier handling and core DAX measures

- **Price = 0**: 240 listings (about 2.5%) had a price of 0. These are missing prices, not free cars, and would drag every average down, so they were removed in Power Query (`Table.SelectRows(..., each [price] <> 0)`, step "Removed zero prices").
- **Mileage = 0**: kept. Most of these are 2016 models, so they are most likely genuinely new cars.
- **Row count**: 9,576 raw listings → 9,223 after removing 113 duplicate rows (Day 1) and 240 zero-price rows (Day 2).
- **Data model**: a single clean table (`car_ad`), so no relationships are needed at this stage.
- **DAX measures**: Total Listings, Avg Price and Avg Mileage, checked with card visuals. See [MEASURES.md](MEASURES.md).

## Files

- `Automotive_Analysis.pbix`: the Power BI report (open with Power BI Desktop)
- `MEASURES.md`: DAX measure definitions and notes

## Tools

Power BI Desktop, Power Query (M), DAX
