# 📘 ML Oncall Runbooks – Master Document

This document provides detailed runbooks for common machine learning oncall scenarios, written in a generic format using the Iris dataset as a neutral example.

---

## Table of Contents
1. [Model Deployment Runbook](#1-model-deployment-runbook--example)
2. [Model Retraining and Update Runbook](#2-model-retraining-and-update-runbook--example)
3. [Model Monitoring and Alerting Runbook](#3-model-monitoring-and-alerting-runbook--example)
4. [Data Pipeline Failure Runbook](#4-data-pipeline-failure-runbook--example)
5. [ML Infrastructure Scaling Runbook](#5-ml-infrastructure-scaling-runbook--example)
6. [Data Quality & Availability Runbook](#6-data-quality--availability-runbook--example)
7. [Access & Permissions Runbook](#7-access--permissions-runbook--example)
8. [Incident Communication Runbook](#8-incident-communication-runbook--example)

---

# 1. Model Deployment Runbook – Example

**Scenario:**  
A new machine learning model (`iris_classifier_v2`) trained on the Iris dataset has passed validation and needs to replace the current production model (`iris_classifier_v1`).

**Objective:**  
Deploy a new or updated ML model into production, validate functionality, and roll back if issues occur.

## Steps (Example)
1. Verify model artifact integrity and version.
2. Configure deployment environment.
3. Load model and dependencies.
4. Perform smoke tests and inference checks.
5. Gradual rollout strategy.
6. Monitor post-deployment health.
7. Rollback plan.

## Troubleshooting (Example Issues)
- Deployment error: container fails on startup.
- Dependency conflict.
- Resource limits.

## Contact Points
- Primary: ML Engineering oncall
- Secondary: DevOps / Platform Engineering

## Acceptance Criteria
- New model live in production, serving >95% of traffic.
- Smoke tests and canary rollout validate successfully.
- Monitoring shows no anomalies compared to previous version.
- Rollback plan validated.
---

# 2. Model Retraining and Update Runbook – Example

**Scenario:**  
The current production model may be outdated. New Iris dataset samples have been collected and a retrained version needs to be validated and promoted.

**Objective:**  
Retrain models with updated data, evaluate performance, and update the deployed version without regressions.

## Steps (Example)
1. Validate new data.
2. Retrain the model.
3. Evaluate model performance.
4. Version control.
5. Deploy retrained model.
6. Monitor post-update performance.

## Troubleshooting (Example Issues)
- Training fails.
- Model underperforms.
- Deployment mismatch.

## Contact Points
- Primary: ML Engineering oncall
- Secondary: Data Engineering

## Acceptance Criteria
- Retrained model stored in registry with metadata.
- Accuracy ≥ previous model.
- Logs archived for reproducibility.
- Deployment successful.
---

# 3. Model Monitoring and Alerting Runbook – Example

**Scenario:**  
An alert fires because the deployed model shows a drop in accuracy or unexpected input distributions compared to baseline.

**Objective:**  
Investigate and resolve alerts related to model performance degradation, data drift, or inference issues.

## Steps (Example)
1. Review alert details.
2. Investigate input data.
3. Check model outputs.
4. Evaluate drift and degradation.
5. Decide action.
6. Communicate incident status.

## Troubleshooting (Example Issues)
- False alarm.
- Bad input data.
- Performance regression.

## Contact Points
- Primary: ML Engineering oncall
- Secondary: Data Engineering

## Acceptance Criteria
- Root cause identified and documented.
- Corrective action taken.
- Alert closed with resolution details.
---

# 4. Data Pipeline Failure Runbook – Example

**Scenario:**  
The training or inference data pipeline fails, preventing new data from being ingested or processed.

**Objective:**  
Resolve failures in data pipelines that feed training or inference models.

## Steps (Example)
1. Identify the failure.
2. Check upstream data source.
3. Validate schema and transformations.
4. Re-run or repair the pipeline.
5. Validate pipeline output.
6. Monitor downstream effects.

## Troubleshooting (Example Issues)
- Missing data file.
- Schema mismatch.
- Transformation error.

## Contact Points
- Primary: Data Engineering
- Secondary: ML Engineering

## Acceptance Criteria
- Pipeline restored and validated.
- Data integrity confirmed.
- Downstream jobs consuming data successfully.
---

# 5. ML Infrastructure Scaling Runbook – Example

**Scenario:**  
The deployed model is receiving more inference requests than usual, causing high latency and timeouts.

**Objective:**  
Scale ML infrastructure to meet demand for inference or training workloads.

## Steps (Example)
1. Identify scaling trigger.
2. Determine scaling approach.
3. Apply scaling changes.
4. Validate system performance.
5. Monitor after scaling.
6. Plan resource cleanup.

## Troubleshooting (Example Issues)
- Scaling doesn’t reduce latency.
- Autoscaler misconfigured.
- GPU contention.

## Contact Points
- Primary: ML Engineering oncall
- Secondary: Platform/DevOps Engineering

## Acceptance Criteria
- Latency and error rates within SLOs.
- Autoscaling tested and documented.
- Cost impact reviewed.
---

# 6. Data Quality & Availability Runbook – Example

**Scenario:**  
The model receives input data with missing or corrupted features, or a data source is delayed.

**Objective:**  
Handle situations where upstream data is delayed, missing, corrupted, or otherwise unusable.

## Steps (Example)
1. Confirm the issue.
2. Validate schema and ranges.
3. Assess model impact.
4. Apply workarounds.
5. Escalate if needed.
6. Validate fix.

## Troubleshooting (Example Issues)
- Missing features.
- Out-of-range values.
- Corrupted file.

## Contact Points
- Primary: Data Engineering
- Secondary: ML Engineering

## Acceptance Criteria
- Root cause identified and documented.
- Workaround or fix applied.
- Data validated.
- Model confirmed functional.
---

# 7. Access & Permissions Runbook – Example

**Scenario:**  
An engineer cannot access storage, model registry, or monitoring dashboard required for ML operations.

**Objective:**  
Resolve access and permission issues quickly.

## Steps (Example)
1. Confirm the issue.
2. Check authentication status.
3. Validate permissions.
4. Apply short-term workaround.
5. Escalate if unresolved.
6. Document and fix root cause.

## Troubleshooting (Example Issues)
- Expired credentials.
- Misconfigured role.
- Network/VPN issues.

## Contact Points
- Primary: ML Engineering
- Secondary: Security/Infrastructure

## Acceptance Criteria
- Access issue resolved.
- Engineer able to perform required actions.
- Workaround documented.
- Root cause fixed permanently.
---

# 8. Incident Communication Runbook – Example

**Scenario:**  
An alert indicates degraded performance. The oncall engineer needs to communicate status and updates.

**Objective:**  
Ensure clear, timely, and consistent communication during ML incidents.

## Steps (Example)
1. Acknowledge the alert.
2. Assign roles.
3. Open an incident bridge.
4. Provide regular updates.
5. Escalate if necessary.
6. Communicate resolution.
7. Close the loop.

## Troubleshooting (Example Issues)
- No updates being posted.
- Stakeholder confusion.
- Duplicate channels or bridges.

## Contact Points
- Primary: Incident Commander
- Secondary: ML, Data, and DevOps team leads

## Acceptance Criteria
- Incident acknowledged and communicated promptly.
- Roles assigned.
- Stakeholders informed until closure.
- Post-mortem completed.
