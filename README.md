# Megaline Prepaid Plan Analysis

Statistical analysis comparing the revenue performance of two prepaid mobile plans (**Surf** and **Ultimate**) for a telecom company, using call, message, and internet usage data from 500 customers over one year.

## Business Question

Megaline's commercial department needs to know which of its two prepaid plans generates more revenue per user, in order to allocate the advertising budget more effectively.

## Data

Five source tables (500 users, ~137K call records, plus messages and internet sessions):
- `users` — demographics, plan, registration/churn dates
- `calls`, `messages`, `internet` — monthly usage events
- `plans` — pricing rules for each plan (monthly fee, included minutes/texts/data, overage rates)

*(Raw CSV files are proprietary course data and are not included in this repo; the notebook outputs below are saved with real results.)*

## Approach

1. **Data cleaning** — fixed data types, handled missing values, removed inconsistencies across the five tables
2. **Feature engineering** — computed monthly minutes, messages, and data usage per user; calculated monthly revenue per user based on each plan's pricing rules
3. **Exploratory analysis** — compared usage distributions (mean, variance, standard deviation) between plans with histograms and box plots
4. **Hypothesis testing** — used Welch's t-test to test two hypotheses:
   - H1: Average revenue differs between Surf and Ultimate users
   - H2: Average revenue differs between users in the NY-NJ region and the rest of the country

## Key Findings

- **Ultimate generates more revenue on average** ($72.28/month vs. $60.13 for Surf), and the difference is statistically significant (p ≈ 0)
- **Revenue predictability differs sharply between plans.** Ultimate's revenue is tightly clustered around its $70 monthly fee (std. dev. $11.35) — few users exceed plan limits. Surf's revenue is far more volatile (std. dev. $53.53), driven by a long tail of users who exceed their data allowance and get charged extra
- **NY-NJ users generate less revenue per user** than the rest of the country ($58.87 vs. $64.96, p = 0.013) — despite being the largest customer base by volume, suggesting plan mix or usage behavior differs regionally

## Tools

Python · pandas · NumPy · Matplotlib · SciPy (`scipy.stats`) — hypothesis testing via Welch's t-test

## Files

- `megaline_plan_analysis.ipynb` — full analysis with code, charts, and interpretation of results

---
*Coursework project completed as part of the Data Science MBA program.*
