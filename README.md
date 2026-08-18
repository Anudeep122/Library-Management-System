# EnergyShift: OWID Energy Data Preprocessing

Visual analytics preprocessing pipeline for the **Our World in Data Energy Dataset**.

## Quick Start

```bash
pip install -r requirements.txt
python run_pipeline.py
```

## Outputs

### Processed Datasets (`data/processed/`)

| File | Description |
|------|-------------|
| `energy_master_clean.csv` | Full cleaned dataset with all entities and engineered features |
| `energy_viz_ready.csv` | Slim dashboard schema (~55 columns) |
| `energy_countries_viz.csv` | Countries only |
| `energy_aggregates.csv` | Regional/income/political aggregates |
| `energy_world.csv` | World entity timeline |
| `energy_long.csv` | Long-format electricity by source |
| `agg_*.csv` | Pre-computed aggregation tables |

### Reports (`data/reports/`)

- `summary_report.md` — Executive summary
- `data_cleaning_report.md` — Cleaning decisions and counts
- `missing_value_report.md` — Missing value treatment plan
- `outlier_report.md` — Outlier flags (not removed)
- `feature_engineering_report.md` — Engineered feature definitions
- `column_catalog.csv` — Full column metadata
- `figures/` — Missing value, outlier, and noise visualizations

## Source Data

- Raw: `data/raw/owid-energy-data.csv`
- Codebook: `data/reference/owid-energy-codebook.csv`
- [OWID Energy Dataset](https://ourworldindata.org/energy)

## Design Principles

1. Keep all geographic entities; filter via `entity_type` in views
2. Preserve full 1900–2024 range
3. Default missing = keep (structural absence is informative)
4. Remove only provable errors (negative volumes, invalid shares)
5. Preserve genuine historical events and spikes
