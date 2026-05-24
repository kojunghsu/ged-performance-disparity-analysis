# Analytical Framework — GED Performance Disparity Analysis

This document outlines the analytical methodology used in this project. Data, pipeline code, and feature engineering logic are excluded per data confidentiality requirements.

---

## Data Scope

The analysis drew on candidate testing information and testing center infrastructure data provided by GED Testing Service for the states included in the analysis. Three performance metrics were tracked throughout as primary outcome measures:

- **Pass Rate** — share of exam attempts that meet the passing standard
- **Average Score** — mean score across exam attempts
- **No-Show Rate** — share of registered attempts where the candidate did not appear

---

## Phase 1 — Exploratory Data Analysis

Initial EDA examined patterns across demographic variables including age group, primary language, education level, gender, race, and ethnicity, as well as geographic indicators such as state and urban-rural classification.

This phase surfaced the key performance differences that informed the later segmentation and driver analysis.

Notable patterns identified:

- Pass rate and average score generally decline with age, while no-show rates remain relatively stable across age groups
- English-speaking candidates outperform Spanish-speaking candidates, while both groups show similar no-show rates
- Education level is associated with GED performance, with some unexpected patterns among lower education groups

---

## Phase 2 — Resource Distribution Analysis

Testing center distribution was analyzed across geographic areas, including urban and rural segments. Candidate-per-center ratios were used to identify resource pressure across state and urbanicity segments.

Minnesota's urban testing market emerged as a significant outlier, with more than 5,900 candidates per center, approximately 10 times the national average. Other high-pressure urban segments included Idaho, Utah, and New York.

---

## Phase 3 — Demographic Segmentation (K-Modes)

K-Modes clustering was used to segment candidate profiles based on categorical demographic variables, including language, age group, gender, education level, race, and ethnicity.

The clustering analysis identified four learner segments with different GED outcomes:

1. Higher Performing
2. Moderate Performing
3. Lower Performing
4. At Risk

The resulting segments showed meaningful differences in pass rate, average score, and no-show rate. Pass rates ranged from 39.2% in the at-risk segment to 59.0% in the higher-performing segment, directly informing the candidate support recommendations.

---

## Phase 4 — Geographic Segmentation (K-Means)

K-Means clustering was used to segment states based on five state-level indicators:

- Enrollment rate
- No-show rate
- Pass rate
- Average score
- Online testing share

The analysis identified lower-performing geographic clusters that required different intervention strategies. Cluster 2 showed conversion and preparation challenges, Cluster 3 showed stronger participation but weaker pass outcomes, and Cluster 4 appeared as a large-scale outlier with strong engagement but very low pass rates.

---

## Phase 5 — Infrastructure Stress Index (PCA + Regression)

To capture structural constraints in testing accessibility, an Infrastructure Stress Index was constructed using PCA. The index summarized infrastructure pressure related to candidate congestion and limited online access.

Regression analysis was then used to examine the relationship between infrastructure pressure and state-level pass rates. The results suggested that higher infrastructure pressure was associated with lower pass rates, with states such as Minnesota, Idaho, and Utah showing particularly high candidate-to-center ratios.

This analysis supported the recommendation to rebalance testing infrastructure, expand capacity in high-pressure areas, and increase hybrid online/offline testing options.

---

## Tools

Python was used for data analysis, clustering, PCA, regression modeling, and visualization.