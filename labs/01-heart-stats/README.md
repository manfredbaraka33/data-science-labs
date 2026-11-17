# Lab 01: Heart disease statistics

## Questions
1. Do patients with heart disease reach a different maximum heart rate during an exercise test?
2. Is heart disease more common in men or in women?

## Data
UCI Heart Disease dataset (Cleveland), 303 patients:
https://archive.ics.uci.edu/dataset/45/heart+disease

Columns used: `thalach` (renamed `max_heart_rate`, beats per minute), `sex` (male / female), `num` (turned into `disease` = yes / no), `age`.

## Test 1: Maximum heart rate vs heart disease (t-test)
- **Why a t-test:** two groups (disease yes / no) and a number outcome.
- **H₀:** both groups have the same average maximum heart rate. **H₁:** the averages differ.
- **Result:** 139.3 bpm (disease) vs 158.4 bpm (no disease), 19 bpm lower.
- **p-value:** p < 0.001, so we reject H₀.
- **Effect size:** Cohen's d = 0.91, a large difference.
- **Age check:** the gap remained within age groups: 21 bpm lower in patients under 55, and 12 bpm lower in patients 55 and over. Age does not explain the result, although older patients have lower heart rates in general.

## Test 2: Sex vs heart disease (chi-square test)
- **Why chi-square:** sex and disease are both categories.
- **H₀:** heart disease is equally common in men and women. **H₁:** it differs.

| Sex | No disease | Disease | % with disease |
|---|---|---|---|
| Female | 72 | 25 | 26% |
| Male | 92 | 114 | 55% |

- **p-value:** p < 0.001, so we reject H₀.

## What it means
Patients with heart disease reached a maximum heart rate about 19 beats per minute lower during the exercise test. This is a large difference that holds even among patients of similar age, so a low maximum heart rate is a useful warning sign for further heart checks. Heart disease was about twice as common in men as in women, which supports screening men first.

## Limitations
- This shows a link, not a cause.
- The data comes from one hospital in the USA; results may differ in other populations, such as Tanzania.
- Other factors (such as smoking) were not checked.

## How to run
pip install pandas scipy ucimlrepo
Then open analysis.ipynb and click Run All.
