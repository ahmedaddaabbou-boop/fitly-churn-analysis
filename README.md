# Fit.ly Churn Analysis

A subscriber-churn investigation for a fictional fitness-app company, "Fit.ly Tech." Built as an end-to-end analytics exercise: three raw, messy source tables are cleaned, explored, and tested statistically to explain why churn is running at 28–29% and what to do about it — finishing with a KPI definition and a leadership-ready presentation script.

## Business context

Fit.ly Tech's subscriber churn has been rising for two quarters. Leadership wants to know *why* users are leaving and what concrete actions can bring churn down. This project pulls together account records, support-ticket history, and in-app activity logs to answer that.

## Data

Three synthetic CSVs (generated for this exercise, no real user data):

| File | Contents |
|---|---|
| `da_fitly_account_info.csv` | One row per customer: plan, list price, state, churn status |
| `da_fitly_customer_support.csv` | Support tickets: channel, topic, resolution time |
| `da_fitly_user_activity.csv` | In-app event log: event type + timestamp per user |

## Method

1. **Cleaning** — ~40% of `churn_status` was blank (treated as active/no cancellation on record), the support `channel` field used `-` for unlabeled entries, and join keys were renamed to align across tables.
2. **Exploratory analysis** — univariate and bivariate charts on plan mix, resolution-time distribution, and churn by segment.
3. **Statistical testing** — resolution times are not normally distributed (confirmed with a Shapiro-Wilk test), so all group comparisons use the non-parametric **Kruskal-Wallis** test rather than ANOVA/t-tests.
4. **Engagement features** — per-user event counts, active days, and engagement quartiles built from the activity log.
5. **KPI design** — a Monthly Churn Rate metric, segmented by plan and engagement quartile, with a baseline and Q4 target.

## Key findings

- **Engagement is the dominant churn driver.** Users in the lowest engagement quartile churn at ~40%, versus ~4–6% in the top quartiles — roughly a 10x gap, and every group difference is statistically significant.
- **The Free plan has the highest churn (41%)**, well above the 28.5% overall average; paid tiers (22–26%) retain far better.
- **Churned users waited ~3x longer for support resolution** (~18–19h median) than active users (~7h median) — the largest statistical signal in the dataset (Kruskal-Wallis H = 486).

Full writeup with numbers and interpretation is in the notebook; a leadership-facing talking-head script is in [`presentation.md`](presentation.md).

## Recommendations

1. Automated re-engagement trigger for users inactive 14+ days, focused on workout tracking.
2. Free-to-paid conversion campaign (time-limited discount).
3. Investigate and reduce support resolution times, starting with tickets that exceeded 18 hours.
4. Build a Monthly Churn Rate dashboard segmented by plan and engagement, reviewed monthly with leadership.

## Repo structure

```
churn_analysis.ipynb   # full analysis: cleaning, EDA, stats, KPI dashboard, recommendations
presentation.md        # ~10-minute talking-head script for a leadership readout
da_fitly_*.csv          # source data
requirements.txt
```

## Running it

```bash
pip install -r requirements.txt
jupyter notebook churn_analysis.ipynb
```

## Stack

pandas, numpy, matplotlib, seaborn, scipy, [pingouin](https://pingouin-stats.org/) (Kruskal-Wallis, Shapiro-Wilk)
