# Lab 02: Two A/B tests (SMS reminders and a discharge checklist)

Notebook: lab_sms_reminder_analysis.ipynb

Practice data, created in Python with a fixed seed so the results can be repeated.

## Test A: Do SMS reminders reduce missed appointments?

### Question
About 25% of patients miss their appointments. Does an SMS reminder the day before lower this?

### Method
- Patients were split by chance into two groups of 1,100: one gets the SMS, one does not.
- Group size was planned before the test: 1,092 per group is needed to catch a drop from 25% to 20% (0.05 line, power 80%).
- Outcome: missed (yes or no). This is a category, so the test is the chi-square test.

### Results

| Group  | Missed | Came | Missed (%) |
|--------|-------:|-----:|-----------:|
| No SMS |    281 |  819 |      25.5% |
| SMS    |    218 |  882 |      19.8% |

Chi-square test: p = 0.0016

### Decision
p is below 0.05, so the difference is very unlikely to be chance. The SMS lowered missed appointments by about 5.7 points (from 25.5% to 19.8%). This is bigger than the 5-point change we planned to catch. Recommendation: send SMS reminders to all patients.

## Test B: Does a discharge checklist shorten hospital stay?

### Question
The average stay is about 6 days. Does a new discharge checklist shorten it by at least 1 day?

### Method
- Patients were split by chance into two groups of 150: one ward process uses the checklist, the other does not.
- Group size was planned before the test: 142 per group is needed to catch a 1-day drop when stays usually vary by about 3 days (effect size 1/3, 0.05 line, power 80%).
- Outcome: days in hospital. This is a number, so the test is the t-test.

### Results

| Group        | Average stay (days) |
|--------------|--------------------:|
| No checklist |                5.96 |
| Checklist    |                5.10 |

t-test: p = 0.010
Cohen's d = 0.30 (small to medium effect)

### Decision
p is below 0.05, so the shorter stay is very unlikely to be chance. The checklist shortened the average stay by about 0.86 days, slightly less than the 1-day target. Recommendation: the checklist works; discuss with management whether 0.86 days is enough to adopt it everywhere.

## Files
- `ab_tests.ipynb`: the notebook with all code and results




## Project A: Does a new landing page make more visitors buy?

Notebook: `project_a_landing_page.ipynb`
Data: public A/B test dataset from an online shop (Udacity practice data), 294,478 visits.

### Question
An online shop built a new landing page (the first page visitors see). Does it make more visitors buy than the old page?

### Method
- Visitors were split by chance into two groups: control (old page) and treatment (new page).
- Outcome: did the visitor buy? (yes/no), so the main test is the chi-square test.
- Data cleaning: removed 3,893 rows where the visitor saw the wrong page for their group, and kept each visitor only once. 290,584 visitors remained.
- Sample size: 17,163 visitors per group are needed to catch a rise from 12% to 13% (0.05 line, power 80%). The test had about 145,000 per group.
- Group split: 49.99% / 50.01% (split check p = 0.95), so the split was fair.

### Results

| Group | Visitors | Bought | Bought (%) |
|-------|---------:|-------:|-----------:|
| Old page (control) | 145,274 | 17,489 | 12.04% |
| New page (treatment) | 145,310 | 17,264 | 11.88% |

Chi-square test: p = 0.19

Week by week, both pages stayed almost the same (between 11.8% and 12.3%), so there was no early effect that faded.

### Decision
The p-value (0.19) is above 0.05, so the null hypothesis stays: the new page makes no real difference to buying. The test was large enough to catch a 1-point rise, so this "no difference" can be trusted.

Recommendation: keep the old page. The new page costs money and does not bring more buyers.




## Project B: Which of two promotions sells more?

Notebook: `project_b_promotions.ipynb`
Data: public fast-food marketing test dataset (Kaggle / IBM Watson sample), promotions 1 and 2 only: 90 restaurants, 4 weeks.

### Question
A fast-food company is adding a new item to its menu. Does promotion 1 or promotion 2 sell more of it?

### Method
- Each restaurant was given one promotion by chance and kept it for 4 weeks (randomized by restaurant, because all customers of a restaurant see the same advertisement).
- Checked that no restaurant had more than one promotion.
- One result per restaurant: the average of its 4 weekly sales.
- Outcome: average weekly sales in thousands of dollars, a number, so the main test is the t-test.
- Sample size: 42 restaurants per promotion are needed to catch a gap of 10 thousand dollars (spread 16, effect size 0.625, 0.05 line, power 80%). The test had 43 and 47.
- Group split: 43 / 47 restaurants (47.8% / 52.2%, split check p = 0.67), with a similar mix of small, medium and large areas.

### Results

| Promotion | Restaurants | Average weekly sales (thousand $) |
|-----------|------------:|----------------------------------:|
| 1 | 43 | 58.1 |
| 2 | 47 | 47.3 |

t-test: p = 0.0012
Cohen's d = 0.70 (medium to large)

Week by week, the gap stayed about the same (promotion 1: 56.9 to 58.8; promotion 2: 46.3 to 47.7), so the effect did not fade.

### Decision
The p-value (0.0012) is below 0.05, so the difference is real. Promotion 1 sold about 10.8 thousand dollars more per restaurant per week, more than the 10 thousand gap the company said was worth acting on.

Recommendation: use promotion 1, not promotion 2.



## Project C: Which email brings more customers to the website?

Notebook: `project_c_emails.ipynb`
Data: real email test by a clothes shop, shared publicly by Kevin Hillstrom (MineThatData E-Mail Challenge, 2008), 64,000 customers.

### Question
The shop prepared two advertisement emails: one with men's clothes and one with women's clothes. Does either email make more customers visit the website, compared with sending no email? Which one works best?

### Method
- Customers were split by chance into three groups: Mens E-Mail, Womens E-Mail, No E-Mail (the comparison group). The email was not chosen by gender.
- Outcome: did the customer visit the website in the two weeks after the email day? (yes/no), so the main test is the chi-square test.
- Three groups, so the groups were compared two at a time (3 pairs), with the stricter line 0.05 ÷ 3 = 0.0167.
- Sample size: 5,519 customers per group are needed to catch a rise from 11% to 13% (line 0.0167, power 80%). Each group had about 21,300.
- Group split: 33.42% / 33.29% / 33.29% (split check p = 0.90), so the split was fair.

### Results

| Group | Customers | Visited | Visited (%) |
|-------|----------:|--------:|------------:|
| Mens E-Mail | 21,307 | 3,894 | 18.28% |
| Womens E-Mail | 21,387 | 3,238 | 15.14% |
| No E-Mail | 21,306 | 2,262 | 10.62% |

| Pair | Difference | p-value | Cramér's V |
|------|-----------:|--------:|-----------:|
| Mens vs No email | +7.66 points | 7.8e-112 | 0.109 |
| Womens vs No email | +4.52 points | 3.9e-44 | 0.068 |
| Mens vs Womens | +3.14 points | 4.3e-18 | 0.042 |

All three p-values are below 0.0167, so all three differences are real.

### Decision
Both emails bring more visits than no email; the men's email brings the most (about 72% more visitors than no email). Cramér's V is small because most customers do not visit in any group, but the gain is large for the business.

Recommendation: send emails. If only one can be sent, send the men's email.

Limits: the data has no dates, so the effect over time could not be checked; only visits were tested, not purchases.
