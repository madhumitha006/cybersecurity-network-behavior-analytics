# Project 1 — Cybersecurity Network Behaviour Analytics

## Problem
Establish normal network behaviour from anonymised network-flow data and identify communication patterns that differ strongly from normal behaviour.

## Dataset
A synthetic anonymised dataset was created because the supplied challenge PDF specifies the required fields but does not provide actual data rows.

Fields:
Flow_ID, Timestamp, Source, Destination, Bytes_Transferred, Duration, Protocol, Connection_Frequency

## Data Preparation
- Removed duplicate records.
- Converted timestamps to datetime.
- Validated numeric fields.
- Imputed small numbers of missing numeric values with medians.
- Imputed missing protocol values with the mode.
- Verified required source/destination fields.

## KNN Method
A distance-based KNN anomaly detector was used with:
- Features: Bytes_Transferred, Duration, Connection_Frequency
- StandardScaler normalization
- k = 10
- Anomaly score = mean distance to the nearest 10 neighbours
- Threshold = 92nd percentile of KNN anomaly scores

A high score means that a flow is substantially different from nearby network-flow behaviour. It does NOT by itself prove that the flow is malicious.

## Validation
The synthetic dataset contains a hidden validation flag representing injected unusual behaviour. This flag is used only to evaluate the implementation and is not part of the challenge-style input dataset.

Precision: 0.867
Recall: 0.812
F1-score: 0.839

Confusion matrix:
[[1356, 16], [24, 104]]

## Key Insights
1. KNN flagged 120 of 1500 cleaned flows as unusual using the 92nd-percentile distance threshold.
2. The protocol with the highest KNN unusual-rate was UDP, with an unusual rate of 10.9%.
3. The most active source device was DEV-021, generating 52 flows.
4. The source device with the highest total transferred volume was DEV-012, with approximately 627,687 bytes.
5. The hour with the highest unusual-traffic rate was 02:00.
6. The KNN validation benchmark achieved precision 0.867, recall 0.812, and F1-score 0.839.
7. Unusual records should be investigated using source, destination, protocol, time, volume and connection-frequency context rather than automatically being labelled malicious.

## Practical Action Plan
1. Investigate high KNN-score flows first.
2. Review the source and destination devices involved in repeated unusual flows.
3. Compare unusual activity with the normal protocol and hourly baseline.
4. Prioritise devices with both high activity and repeated unusual flows.
5. Review large-volume transfers and unusually high connection frequencies.
6. Do not classify an anomaly as malicious without additional contextual evidence.
7. Re-run the baseline periodically as normal network behaviour changes.

## Deliverables
- network_flow_raw.csv
- network_flow_clean.csv
- network_flow_with_knn_results.csv
- 4 PNG visualisations
- validation metrics
- this report
