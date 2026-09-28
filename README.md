# Indo-Pacific Chinese Coast Guard Conflict Tracker

A Python data pipeline that queries the GDELT 2.0 database via Google BigQuery to track Chinese Coast Guard (CCG) territorial confrontations in the South China Sea and East China Sea from 2015 to the present.

### Features
- Queries the GDELT 2.0 event registry (`gdelt-bq.gdeltv2.events`) using SQL and the Google BigQuery API, isolating CAMEO material conflict root codes (`17` Coerce, `18` Assault, `19` Fight).
- Eliminates domestic Chinese media reporting and dateline bias by cross-referencing actor string identifiers (`Actor1Name`, `Actor2Name`) with FIPS 10-4 geographic action codes (`ActionGeo_CountryCode`).
- Aggregates overall incident volume and verified annual bilateral clash trends across six key regional actors (Philippines, South Korea, United States, Taiwan, Japan, Vietnam).
- Includes a pre-extracted dataset (`ccg_events_backup.csv`) as a local cache fallback so the analysis and visualizations run out of the box without requiring active Google Cloud credentials.

### Tech Stack & Dependencies
- Python 3.x
- `pandas`
- `matplotlib` / `seaborn`
- `google-cloud-bigquery`

### How to Use
1. Install dependencies: `pip install pandas matplotlib seaborn google-cloud-bigquery`
2. Clone or download this repository (ensuring `ccg_events_backup.csv` is in the same directory as the notebook).
3. Run `gdelt_maritime_tracker.ipynb` to process the cached GDELT records and generate the time-series visualizations (or place a Google Cloud `service_account.json` key in the directory to run a fresh BigQuery extraction).
