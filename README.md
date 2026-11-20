# Data science labs — Manfred Baraka

Data analysis in Python, from statistics to machine learning.
Each lab answers a real question, mostly from health, with real or practice data.

## Labs

| Lab | Question | Methods | Key result |
|-----|----------|---------|------------|
| 01 | [Heart rate and sex vs heart disease](labs/01-heart-stats/) | t-test, chi-square | Disease: 19 bpm lower heart rate; 2x more common in men |
| 02 | [Do SMS reminders and a discharge checklist work? (practice data)](labs/02-ab-tests/lab_sms_reminder_analysis.ipynb) | A/B test, chi-square, t-test, Cohen's d | SMS: missed visits 25.5% → 19.8% (p = 0.0016); checklist: stay 5.96 → 5.10 days (p = 0.010) |
| 02A | [Does a new landing page make more visitors buy?](labs/02-ab-tests/project_a_landing_page.ipynb) | A/B test, chi-square | 12.04% vs 11.88%, p = 0.19: no real difference, keep the old page |
| 02B | [Which of two promotions sells more?](labs/02-ab-tests/project_b_promotions.ipynb) | A/B test, t-test, Cohen's d | 58.1 vs 47.3 thousand $ per week, p = 0.0012, d = 0.70: use promotion 1 |
| 02C | [Which email brings more customers to the website?](labs/02-ab-tests/project_c_emails.ipynb) | A/B/C test, chi-square (3 pairs), Cramér's V | Visits: men's email 18.28%, women's 15.14%, none 10.62% (all p < 0.0167): send the men's email |
| 02D | [Which of three promotions sells the most?](labs/02-ab-tests/project_d_three_promotions.ipynb) | A/B/C test, t-test (3 pairs), Cohen's d | Promotions 1 (58.1) and 3 (55.4) beat promotion 2 (47.3), p < 0.0167; 1 vs 3 no real difference: stop promotion 2 |



## Tools

Python, pandas, NumPy, SciPy, statsmodels, Jupyter

## How to run

    pip install -r requirements.txt

Then open any notebook and click **Run All**.
