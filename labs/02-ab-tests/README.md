# Lab 02: Two A/B tests (SMS reminders and a discharge checklist)

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
