# Leading Indicator ML Engine for EHS Risk Forecasting

This project implements a **machine learning–based leading indicator system** to forecast near‑term Environmental Health & Safety (EHS) risk using proactive operational signals rather than lagging injury metrics.

The engine produces **weekly, site‑level risk scores** that help safety and operations teams prioritize preventive actions before incidents occur.

---

## 🔍 Problem Statement

Traditional EHS metrics such as TRIR and DART are **lagging indicators**—they describe outcomes after harm has already occurred. While necessary for compliance, they provide limited operational insight for prevention in complex, fast‑moving environments.

This project explores whether **leading indicators**—such as near misses, hazard reports, overtime, overdue maintenance, and open corrective actions—can be used to **predict elevated incident risk weeks in advance**, enabling earlier intervention and risk reduction.

---

## 🎯 Project Goals

- Forecast incident risk within a **28‑day forward-looking window**
- Use **only non‑personal, system‑level leading indicators**
- Prevent data leakage with time‑based modeling
- Produce **explainable, action‑oriented outputs**, not black‑box scores
- Demonstrate how ML can support EHS decision‑making at scale

---

## 🧠 Approach

### Unit of Analysis
- **Site × Week** (panel time‑series data)

### Data Inputs (examples)
- Exposure hours and overtime
- Near miss and hazard reporting rates
- Stop‑work events and safety observations
- Overdue preventive maintenance
- Open corrective actions (CAPAs)
- Training compliance indicators

> ⚠️ The public repository uses **synthetic data** generated to mirror realistic EHS patterns. No proprietary or identifiable company data is included.

---

## 🏗 Feature Engineering

- Rolling window features (4‑, 8‑, and 12‑week lookbacks)
- Rate normalization per exposure hours
- Trend indicators (recent vs longer‑term changes)
- All features use **prior‑week values only** to avoid label leakage

---

## 🤖 Modeling

- Binary classification: *incident occurring within next 28 days*
- Leakage‑safe **time‑based train/test split**
- Baseline and ensemble models (tree‑based boosting)
- Evaluation focuses on **operationally meaningful metrics**, not accuracy alone

### Key Metrics
- **PR‑AUC** (appropriate for rare events)
- **Recall@Top‑10% risk** (who to intervene on this week)
- ROC‑AUC (reported for context)

---

## 📊 Outputs

### Risk Scoring
- Weekly probability‑based risk score per site
- Ranked list to support prioritization

### Actionability Layer
Risk drivers are mapped to **preventive control themes**, such as:
- Fatigue management and staffing adjustments
- Preventive maintenance escalation
- Corrective action closure discipline
- Targeted training refreshers

> The model is designed as **decision support**, not automated enforcement.

---

## 🖥 Dashboard

A lightweight Streamlit dashboard allows users to:
- Review weekly ranked risk by site
- Filter by time period
- Inspect high‑risk locations for follow‑up

*(Screenshots or GIFs can be added here in future iterations.)*

---

## ✅ Responsible AI & Ethics

- No personal identifiers or individual‑level predictions
- No surveillance or behavioral tracking
- Outputs are advisory and require human judgment
- Explicitly **not intended** for disciplinary use

Bias, drift, and reporting‑culture effects are acknowledged and documented.

---

## ⚠️ Limitations

- Leading indicators depend on reporting quality and safety culture
- Incident outcomes are rare, creating class imbalance
- Synthetic data does not capture every real‑world nuance
- Model performance must be monitored over time for drift

---

## 🚀 Future Improvements

- SHAP‑based local explainability for individual predictions
- Subgroup performance audits (e.g., contractors vs FTEs)
- Calibration analysis and retraining cadence
- Scenario analysis: effect of specific control interventions
- Live ingestion from EHS management systems

---

## 🧩 Repository Structure
