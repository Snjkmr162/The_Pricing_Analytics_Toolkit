# Data

This project uses the **Walmart Recruiting Store Sales Forecasting** dataset from Kaggle.

Source: https://www.kaggle.com/competitions/walmart-recruiting-store-sales-forecasting

## Files used

- `train.csv` - weekly sales by store and department
- `features.csv` - store-level features (temperature, fuel price, CPI, unemployment, markdown events)
- `stores.csv` - store type and size

## Download instructions

1. Join the competition (required before the API will allow downloads):
   https://www.kaggle.com/competitions/walmart-recruiting-store-sales-forecasting/rules

2. Get your Kaggle API token: Kaggle account settings > API > Create New API Token (downloads `kaggle.json`)

3. Run:

pip install kaggle

mkdir -p ~/.kaggle

cp kaggle.json ~/.kaggle/

chmod 600 ~/.kaggle/kaggle.json
kaggle competitions download -c walmart-recruiting-store-sales-forecasting

unzip walmart-recruiting-store-sales-forecasting.zip -d data/

unzip data/train.csv.zip -d data/

unzip data/test.csv.zip -d data/

unzip data/features.csv.zip -d data/

## Notes on data limitations

The raw dataset does not include unit-level price, competitor pricing, or margin data. Where these are required (Week 1 competitor simulation, Week 3 margin assumptions), they are derived or simulated, with assumptions clearly documented in each module's notebook and code.

Raw CSV files are not committed to this repo (size and Kaggle's terms of use). Download them locally using the steps above before running any notebook.
