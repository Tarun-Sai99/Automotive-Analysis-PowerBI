# DAX Measures

All measures live in the `car_ad` table.

| Measure | DAX | What it returns |
|---|---|---|
| Total Listings | `Total Listings = COUNTROWS(car_ad)` | Number of listings in the current filter context |
| Avg Price | `Avg Price = AVERAGE(car_ad[price])` | Average listing price |
| Avg Mileage | `Avg Mileage = AVERAGE(car_ad[mileage])` | Average mileage (in thousands of km) |

## Notes

- **Measures vs columns:** measures are calculated on the fly for whatever filters are active (a slicer, a clicked bar), so `Total Listings` recounts automatically when you filter to one brand.
- **Column references** use the `Table[Column]` syntax, e.g. `car_ad[price]`.
- **Units:** `mileage` is stored in thousands of km, so an Avg Mileage of 141 means about 141,000 km.

## Results on the cleaned data (Day 2)

| Measure | Value |
|---|---|
| Total Listings | ~9K |
| Avg Price | ~15.7K |
| Avg Mileage | ~141 (thousand km) |
