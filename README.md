# GED Testing Service — Performance Disparity Analysis

## Overview

GED Testing Service helps adults earn a high school equivalency credential by passing four subject exams: Math, Language Arts, Science, and Social Studies. Each year, approximately 600,000 learners begin this journey, yet only around 35% progress to completing the exams.

This project investigates where testing performance disparities exist across candidate groups and geographic regions, and what demographic, geographic, and infrastructure-related factors may be associated with those differences.

> **Data Confidentiality:** This project uses proprietary GED Testing Service materials. Raw data, candidate-level datasets, data processing code, and feature engineering logic are excluded from this public repository.

The central question driving this project:

> **Where do testing performance disparities exist across candidate groups and geographic regions, and what factors drive these differences?**

The analysis spans five phases: exploratory data analysis, resource distribution mapping, demographic segmentation, geographic segmentation, and regression-based driver analysis. The final recommendations focus on targeted candidate support, state-level interventions, and infrastructure rebalancing.

---

## Repository Contents

- [`README.md`](./README.md) — project overview, findings, and recommendations
- [`analytical_framework.md`](./analytical_framework.md) — methodology summary and analytical approach
- [`ged_performance_disparity_analysis.pdf`](./ged_performance_disparity_analysis.pdf) — stakeholder-facing presentation deck

---

## Methodology

A detailed discussion of feature selection, clustering methodology, dimensionality reduction, and regression modeling is available in [`analytical_framework.md`](./analytical_framework.md).

---

## Key Findings

### 1. Demographic Segmentation

K-Modes clustering on candidate profiles surfaced four segments with meaningfully different outcomes:

| Segment | Profile | Pass Rate | Avg Score | Primary Barrier |
|---|---|---|---|---|
| High Performing | English, Male, 18–24 | 59.0% | 144.1 | Scheduling delay despite readiness |
| Moderate Performing | English, Male, 15–17 | 52.8% | 142.2 | Unclear preparation path |
| Lower Performing | English, Female, 18–24 | 50.7% | 141.1 | Disengagement risk |
| At Risk | Spanish, Female, 25–34, Hispanic | 39.2% | 137.2 | Language barriers, limited access |

**Supporting EDA findings:**

- Pass rates decline sharply with age, from approximately 57.8% for the 15–17 group to 22.6% for the 65+ group
- English-speaking candidates outperformed Spanish-speaking candidates, with pass rates of 49.1% and 37.5%, respectively
- No-show rates remained relatively stable across age groups, generally ranging from 4% to 6%, suggesting that performance differences were not primarily driven by attendance behavior

### 2. Geographic Segmentation

K-Means clustering on five state-level indicators identified three geographic clusters with below-average performance, each requiring a distinct intervention type:

**Cluster 2 — New York**
Large candidate base (21,782 registered) but approximately 63% conversion from registration to exam-taking. Its test-to-pass conversion was 14.6%, indicating both conversion and preparation challenges.

**Cluster 3 — IN, LA, MO, NH, NJ, TN**
Strong participation relative to other lower-performing clusters, but pass rates remain weak at 27.2%. Candidates in this cluster averaged 5.46 attempts per passed candidate. The results suggest that performance readiness, rather than participation, may be the primary challenge.

**Cluster 4 — Minnesota**
Extreme outlier: 365,740 registered candidates, 96% take-exam rate, but only 9% pass rate. Candidates average 9.5 attempts before passing. Strong engagement suggests that preparation quality, learning support, or exam readiness may be contributing factors.

### 3. Resource Distribution

- 62% of all testing centers are located in urban areas; only 18% are rural — allocation tracks population density, not candidate need
- Minnesota Urban: over 5,900 candidates per testing center, approximately 10× the national average
- Other high-pressure urban segments (excluding MN): Idaho (~225 candidates/center), Utah (~219), New York (~190)

### 4. Infrastructure Stress and Pass Rates

An Infrastructure Stress Index was constructed using PCA to summarize structural testing-access constraints, including candidate congestion and limited online access.

Regression analysis suggested a negative relationship between infrastructure pressure and state-level pass rates. States with higher candidate congestion and more limited online testing access tended to show weaker pass outcomes.

---

## Strategic Recommendations

### Recommendation 1 — Cluster-Based Candidate Support

Personalize intervention pathways by demographic segment rather than applying uniform outreach:

- **High Performing:** Deploy automated scheduling nudges triggered when GED Ready diagnostic scores exceed the passing threshold — convert demonstrated readiness into timely action
- **Moderate Performing:** Provide structured diagnostic assessments and guided study plans with clear milestones
- **Lower Performing:** Surface personalized practice targeting subject-level weaknesses; address disengagement through progress-based feedback
- **At Risk:** Expand Spanish-language content, bilingual support services, and culturally localized resources

### Recommendation 2 — State-Level Geographic Interventions

- **New York:** Address conversion gap with automated booking reminders, simplified scheduling flows, and local preparation partnerships
- **IN, LA, MO, NH, NJ, TN:** Deploy mock exam programs and targeted diagnostic tools to close the performance gap; focus on multi-subject failure patterns
- **Minnesota:** Prioritize readiness support and capacity planning due to high engagement but weak pass outcomes

### Recommendation 3 — Infrastructure Rebalancing

1. Add testing center capacity in the top 10 most resource-constrained urban segments, prioritizing MN, ID, and UT
2. Partner with community colleges and public libraries in congested urban markets to expand available seats; pilot mobile testing units in underserved rural areas
3. Expand online testing from its current share toward 30%+ of total volume to reduce geographic dependency on physical testing centers

---

## Technical Stack

| Category | Tools / Methods |
|---|---|
| Language | Python |
| Clustering | K-Modes (categorical candidate profiles), K-Means (continuous state-level indicators) |
| Dimensionality Reduction | PCA — Infrastructure Stress Index |
| Regression | OLS — state-level pass rate driver analysis |
| Visualization | Matplotlib, Seaborn |


