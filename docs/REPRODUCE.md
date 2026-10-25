# Reproduction scope

This portfolio includes contribution-related source and saved figures, not the full upstream team data package. Notebook outputs were cleared for a clean public-source presentation. Exact original source is retained privately in the working directory; source folders and upstream repository were not changed.

Use Python 3.11 and the upstream environment specification. Run code/04_modelling_table.ipynb after the team preprocessing and spatial pipelines; then run 08 -> 09 -> 10 for supplementary validation. Keep the kernel working directory at code/. The station helper runs from the repository root. Do not unpickle model artefacts from untrusted sources.

The main inputs include data/analysis_data/, data/curated/sa2_features.parquet, property_geo_features.parquet and master_modelling_table.parquet. Supplementary inputs include data/landing/barryplant_rentals_2026.parquet, vic_train_stations.parquet, and the geographic/amenity files referenced by notebook 09. The final external table is data/curated/plant_validation_features.parquet. build_train_stations.py also expects data/landing/ptv/gtfs.zip and data/raw/sa2_features.gpkg, separate from data/curated/sa2_features.gpkg.

Create the expected local folders, supply authorised files from the original project, and store ORS_API_KEY only in a local .env. The environment is not a complete dependency lock. No API or scraper calls were made during portfolio packaging.

## Input references from the included notebooks

- `04_modelling_table.ipynb`: `domain_df = pd.read_parquet("../data/analysis_data/")`
- `04_modelling_table.ipynb`: `sa2_df = pd.read_parquet("../data/curated/sa2_features.parquet")`
- `04_modelling_table.ipynb`: `spatial_df = pd.read_parquet("../data/curated/property_geo_features.parquet")`
- `09_plant_processing.ipynb`: `from dotenv import load_dotenv`
- `09_plant_processing.ipynb`: `plant = pd.read_parquet("../data/landing/barryplant_rentals_2026.parquet")`
- `09_plant_processing.ipynb`: `sa2 = gpd.read_file("../data/raw/sa2_features.gpkg")`
- `09_plant_processing.ipynb`: `sa2_features = pd.read_parquet("../data/curated/sa2_features.parquet")`
- `09_plant_processing.ipynb`: `load_dotenv()`
- `09_plant_processing.ipynb`: `ors_key = os.getenv("ORS_API_KEY")`
- `09_plant_processing.ipynb`: `assert ors_key is not None, "ORS_API_KEY not found"`
- `09_plant_processing.ipynb`: `stations = pd.read_parquet("../data/curated/vic_train_stations.parquet")`
- `09_plant_processing.ipynb`: `schools_raw = pd.read_csv(`
- `09_plant_processing.ipynb`: `training_geo = pd.read_parquet(`
- `10_plant_external_validation.ipynb`: `TRAINING_PATH = PROJECT_ROOT / "data/curated/master_modelling_table.parquet"`
- `10_plant_external_validation.ipynb`: `VALIDATION_PATH = PROJECT_ROOT / "data/curated/plant_validation_features.parquet"`
- `10_plant_external_validation.ipynb`: `MODEL_PATH = PROJECT_ROOT / "models/rental_best_model.joblib"`
- `10_plant_external_validation.ipynb`: `MODEL_PATH.parent.mkdir(parents=True, exist_ok=True)`
- `10_plant_external_validation.ipynb`: `if not MODEL_PATH.exists():`
- `10_plant_external_validation.ipynb`: `domain = pd.read_parquet(TRAINING_PATH)`
- `10_plant_external_validation.ipynb`: `"training_sha256": hashlib.sha256(TRAINING_PATH.read_bytes()).hexdigest(),`
- `10_plant_external_validation.ipynb`: `joblib.dump(artifact, MODEL_PATH)`
- `10_plant_external_validation.ipynb`: `model_artifact = joblib.load(MODEL_PATH)`
- `10_plant_external_validation.ipynb`: `plant_validation = pd.read_parquet(VALIDATION_PATH)`
