# 🧪 Showz: Revenue Optimization via Hypothesis Prioritization & A/B Testing


![Python](https://img.shields.io/badge/Python-3.12-blue) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Engineering-150458) ![SciPy](https://img.shields.io/badge/SciPy-Statistical%20Inference-8CAAE6) ![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)

A hypothesis-prioritization and A/B-test validation pipeline for Showz, combining the ICE/RICE scoring frameworks with a Mann-Whitney U significance test — including a rigor check the original scope of this analysis skipped: testing whether the experiment's revenue advantage is statistically real, not just its conversion advantage.

## 📌 Executive Summary & Strategic Wrap-Up

### 📝 Executive Overview
This project runs Showz's product-change decision through two disciplines: hypothesis backlog prioritization (ICE/RICE) and formal A/B test validation. The headline result is a split verdict, and reporting that split honestly is the actual value of this analysis: **Group B delivers a statistically validated conversion-rate improvement, but its apparent revenue/AOV advantage does not survive the same statistical test** — a distinction the original scope of this project never checked for.

### ⚡ Analysis Phase-by-Phase Flashback
- **Phase 1 (Data Sanitization & Segmentation Integrity):** Identified and removed 58 users active in both test groups, leaving 1,016 clean order records.
- **Phase 2 (Hypothesis Prioritization Engine):** Scored 9 backlog hypotheses via ICE and RICE; adding the Reach factor reordered the top priority from a birthday-discount promotion to a platform-wide subscription form.
- **Phase 3 (Cumulative Metrics Engineering):** Built daily and cumulative conversion, AOV, and revenue series; found a stable +15.98% conversion edge and a volatile −42.3%-to-+50.5% AOV swing.
- **Phase 4 (Anomaly Detection & Statistical Validation):** Flagged outliers via the 99th percentile, then ran Mann-Whitney U on **both** conversion and revenue per order — the second of which the original analysis never tested.
- **Phase 5 (Behavioral Storytelling & Visual Analytics):** Built a hero chart contrasting the validated conversion result against the untested revenue claim.
- **Phase 6 (Executive Conclusions & Business Impact):** Delivered a corrected implementation verdict — ship Group B on conversion, retract the unproven AOV claim.

### 💡 Key Insights & Business Value
- **Conversion is the real, defensible win:** **+18.95%** (outlier-filtered), **P = 0.0070** via Mann-Whitney U — robust to noise and stable through the second half of the test.
- **Revenue/AOV superiority was never actually tested in the original scope, and it doesn't hold up:** **P = 0.8220**, and the filtered effect reverses to **−3.19%**. The AOV spikes visible in the cumulative chart were the exact whale transactions the P99 outlier filter is designed to catch.
- **Reach changes the roadmap, not just the A/B verdict:** under RICE, a platform-wide subscription form outranks a higher-impact but narrow-reach birthday-discount promotion — a separate, ongoing prioritization insight independent of this specific test.
- **A split verdict, reported honestly, is more credible than an inflated one:** shipping Group B on a validated conversion lift is a strong, defensible outcome that doesn't need an unproven revenue claim attached to it.

### 🚀 Proactive Recommendations & Strategic Action Plan

| 🚀 Ship & Monitor | 📊 Prioritization | 🔬 Statistical Rigor |
|---|---|---|
| Roll out Group B to 100% of traffic on the strength of the validated +18.95% conversion lift. | Build the subscription-form hypothesis (RICE winner) into the next roadmap cycle — highest reach-adjusted ROI in the backlog. | Standardize a two-metric (conversion + revenue) Mann-Whitney check as the default protocol for all future Showz A/B tests. |
| Track AOV post-launch without assuming it will improve — this analysis found no evidence it will. | Reserve high-impact, low-reach ideas (e.g., birthday discounts) for targeted campaigns rather than platform-wide rollout. | Re-run the AOV test on a longer post-launch window; a null result now doesn't rule out a smaller effect this sample was underpowered to detect. |
| Correct any internal reporting that still cites the +27.83% AOV figure as a proven result. | | |

### 📊 Target Business KPIs & Expected Impact

| Strategic Initiative | Primary Target KPI | Statistical Basis |
|---|---|---|
| Group B Full Rollout | Platform-wide conversion rate | +18.95% conversion lift, P = 0.0070 (Mann-Whitney U, outlier-filtered) |
| Subscription Form (RICE Winner) | Reach-adjusted ROI on next roadmap cycle | Highest RICE score (112.0) among 9 scored hypotheses |
| AOV Claim Retraction | Accuracy of internal reporting | P = 0.8220 on revenue per order — not statistically significant; filtered effect reverses to −3.19% |

### 🗂 Project Repository Details
- **Repository Slug:** `showz-ab-optimization-analysis`
- **Primary Goal:** Prioritize Showz's product hypothesis backlog and formally validate whether a tested product variant should ship, on both conversion and revenue grounds.
- **Key Achievements:**
  - **Experiment Integrity:** Cleaned a contaminated A/B sample by removing 58 cross-group users before any metric was calculated.
  - **Dual-Framework Prioritization:** Scored and re-ranked 9 hypotheses via ICE and RICE, isolating how the Reach factor changes engineering priority.
  - **Corrected Statistical Rigor:** Identified and corrected an unvalidated revenue/AOV claim the original analysis carried without testing — validated conversion (P = 0.0070) while rejecting the untested AOV claim (P = 0.8220) via Mann-Whitney U at 95% confidence.

## 💻 Tech Stack & Environment Settings
- **Language:** Python 3.12
- **Data Processing:** pandas, numpy
- **Statistical Inference:** scipy.stats (Mann-Whitney U test)
- **Prioritization Frameworks:** ICE (Impact × Confidence / Effort), RICE (Reach × Impact × Confidence / Effort)
- **Data Visualization:** matplotlib, seaborn
- **Environment:** Jupyter Notebook

## 📁 Repository Structure
```
showz-ab-optimization-analysis/
├── Showz_AB_Optimization_Analysis.ipynb   # Full analysis pipeline (executed, outputs included)
├── hypotheses_us.csv                       # Hypothesis backlog (Reach, Impact, Confidence, Effort)
├── orders_us.csv                            # A/B test transaction log
├── visits_us.csv                             # A/B test visit log
├── requirements.txt                          # Reproducible environment dependencies
├── README.md
└── .gitignore                                 # Excludes venv/ and generated chart images
```

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/CarlosACrespoS/showz-ab-optimization-analysis

# Navigate to the project directory
cd showz-ab-optimization-analysis

# Create and activate a virtual environment (recommended)
python -m venv venv_showz
source venv_showz/bin/activate   # Windows: venv_showz\Scripts\activate

# Install required dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook Showz_AB_Optimization_Analysis.ipynb
```
