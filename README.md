# Cybersecurity Network Behaviour Analytics — Project 1

## Challenge
Cybersecurity — What Does Normal Network Behaviour Look Like?

## What is included
- `data/network_flow.csv` — synthetic anonymized input dataset
- `data/network_flow_raw.csv` — dataset with controlled quality issues
- `data/network_flow_clean.csv` — cleaned dataset
- `data/synthetic_validation_truth.csv` — synthetic-only benchmark labels
- `notebooks/cybersecurity_analysis.ipynb` — complete executable notebook
- `visualizations/` — four required charts
- `results/knn_anomaly_results.csv` — KNN scores and flags
- `PROJECT1_REPORT.md` — report
- `cybersecurity_project.py` — starter script

## Run
Install:
`pip install pandas numpy matplotlib scikit-learn jupyter`

Then open:
`notebooks/cybersecurity_analysis.ipynb`

Run all cells.

## Important academic disclosure
The challenge PDF specifies the schema and required analysis but does not provide actual network-flow rows. Therefore the dataset in this implementation is synthetic. The validation labels are synthetic benchmark labels only and must not be presented as real attack labels or real company data.
