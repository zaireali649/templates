# 📘 ML Oncall Runbooks – Master Document

## 1. Model Deployment Runbook – Example
**Scenario:** A new machine learning model (`iris_classifier_v2`) trained on the Iris dataset has passed validation and needs to replace the current production model (`iris_classifier_v1`).  
**Objective:** Deploy a new or updated ML model into production, validate functionality, and roll back if issues occur.

---

## 2. Model Retraining and Update Runbook – Example
**Scenario:** The current production model (`iris_classifier_v2`) may be outdated. New Iris dataset samples have been collected and a retrained version (`iris_classifier_v3`) needs to be validated and promoted.  
**Objective:** Retrain models with updated data, evaluate performance, and update the deployed version without regressions.

---

## 3. Model Monitoring and Alerting Runbook – Example
**Scenario:** An alert fires because the deployed model (`iris_classifier_v3`) shows a drop in accuracy or unexpected input distributions compared to baseline.  
**Objective:** Investigate and resolve alerts related to model performance degradation, data drift, or inference issues.

---

## 4. Data Pipeline Failure Runbook – Example
**Scenario:** The training or inference data pipeline for the Iris classifier fails, preventing new data from being ingested or processed.  
**Objective:** Resolve failures in data pipelines that feed training or inference models to restore normal operation.

---

## 5. ML Infrastructure Scaling Runbook – Example
**Scenario:** The deployed Iris classifier (`iris_classifier_v3`) is receiving more inference requests than usual, causing high latency and occasional timeouts.  
**Objective:** Scale ML infrastructure to meet demand for inference or training workloads while maintaining performance and availability.

---

## 6. Data Quality & Availability Runbook – Example
**Scenario:** The Iris classifier (`iris_classifier_v3`) receives input data with missing or corrupted features, or an expected data source is delayed.  
**Objective:** Handle situations where upstream data is delayed, missing, corrupted, or otherwise unusable to minimize disruption to ML workflows.

---

## 7. Access & Permissions Runbook – Example
**Scenario:** An ML engineer cannot access the model registry, object storage, or monitoring dashboard required to deploy or debug the Iris classifier (`iris_classifier_v3`).  
**Objective:** Resolve access and permission issues for ML systems quickly so oncall engineers can continue operations.

---

## 8. Incident Communication Runbook – Example
**Scenario:** An alert indicates degraded performance in the Iris classifier (`iris_classifier_v3`). The oncall engineer needs to communicate status, updates, and resolution across teams.  
**Objective:** Ensure clear, timely, and consistent communication during ML incidents so stakeholders remain informed and actions are coordinated.
