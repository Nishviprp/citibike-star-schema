# Citi Bike Star Schema Transformation

## Project Goal
This project transforms Citi Bike trip data into a clean **Star Schema** for analytics.  
The output includes one **fact** table (rides) and multiple **dimension** tables (date, time-of-day, rideable type, member type).

## Dataset Source
Citi Bike trip data (monthly files).  
Note: The assignment requires **NYC Citi Bike** datasets (not JC). Use the NYC monthly tripdata zip files when running the notebook.

## Months Used
June 2025 to November 2025 (upload the monthly ZIP files for these months when running the notebook).

## How to Run (Google Colab)
1. Open the notebook in Colab:
   - `notebooks/transform_star_schema.ipynb`
2. Upload the monthly tripdata ZIP files at runtime (Colab → Files → Upload).
3. Run all cells from top to bottom.
4. Outputs will be saved to:
   - `/content/outputs/`

## Star Schema Outputs
### Fact Table
- `fact_rides.csv`
  - Contains ride-level events with:
    - integer `ride_id`
    - foreign keys: `date_key`, `rideable_type_key`, `member_type_key`, `time_of_day_key`
    - station names only: `start_station_name`, `end_station_name`
    - measures: `duration_min`

### Dimensions
- `dim_date.csv`
  - `date_key`, `date`, day/month/year fields, quarter, and `holiday_name`
- `dim_time_of_day.csv`
  - `time_of_day_key`, `time_of_day`
- `dim_rideable_type.csv`
  - `rideable_type_key`, `rideable_type`
- `dim_member_type.csv`
  - `member_type_key`, `member_casual`

## Validation Checks (Included in Notebook)
The notebook includes checks to confirm:
- `ride_id` is integer
- fact table does not contain station IDs or latitude/longitude
- no missing foreign keys
- all fact keys exist in the corresponding dimension tables

## Repo Structure
```text
citibike-star-schema/
  README.md
  notebooks/
    transform_star_schema.ipynb
  .gitignore
