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
| 2 | Outlier handling, data model, core DAX measures | Planned |
| 3 | Overview dashboard: KPIs, price distribution, listings by body type and brand | Planned |
| 4 | Trend analysis: price vs year, mileage vs price, engine type breakdown | Planned |
| 5 | Brand and segment deep dive with slicers | Planned |
| 6 | Polish: formatting, tooltips, bookmarks, drill-through, mobile layout | Planned |
| 7 | Final review, insights write-up, publish | Planned |

## Day 1: Data import and cleaning

- Imported `car_ad.csv` with **Get Data > Text/CSV > Transform Data**, so cleaning happens in Power Query before loading.
- **Engine volume (`engV`)**: the column was text with `"NA"` strings mixed in. Replaced `"NA"` with null and changed the type to Decimal Number, so missing values are handled correctly in calculations.
- **Duplicates**: removed true full-row duplicates with `Table.Distinct` across all columns (deduplicating on a single column would wrongly drop distinct cars that share a value).
- **Noted for Day 2**: listings with `price = 0` or `mileage = 0` look like data-entry errors and will be handled as outliers.

## Files

- `Automotive_Analysis.pbix`: the Power BI report (open with Power BI Desktop)

## Tools

Power BI Desktop, Power Query (M), DAX
