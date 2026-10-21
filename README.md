# A/B Testing — Designing the Data-Generating Process

**Author:** Abigail Ray  
**Course:** ECON 3916: Applied Machine Learning for Economists

## Objective

In this lab, I used experimental data, permutation tests, bootstrap confidence intervals, and power analysis to understand treatment effects, selection bias, and the sample sizes needed to detect meaningful effects.

## Methodology

- Loaded the LaLonde National Supported Work (NSW) randomized job-training experiment with 445 people: 185 trainees and 260 controls.
- Calculated the experimental average treatment effect (ATE) using the difference in mean 1978 earnings.
- Simulated an observational comparison group to demonstrate selection bias.
- Ran a permutation test with 9,999 resamples to test statistical significance.
- Calculated a 95% bias-corrected and accelerated (BCa) bootstrap confidence interval for the ATE.
- Used power analysis to estimate achieved power and the sample sizes needed to detect earnings effects of $500, $1,000, and $2,000.
- Analyzed the Cookie Cats A/B test, comparing Day-1 retention for players assigned to a gate at level 30 or level 40.
- Ran a permutation test and calculated a 95% BCa bootstrap confidence interval for the difference in retention rates.
- Wrote and tested the `n_needed(effect, sd)` function to calculate the sample size per group required for 80% power at a 5% significance level.

## Key Findings

### LaLonde Job-Training Experiment

- The experimental ATE was **$1,794.34**, meaning trainees earned $1,794.34 more on average than the control group.
- The permutation test returned **p = 0.0046**, providing evidence of a statistically significant difference.
- The 95% BCa confidence interval was **$575.18 to $3,262.37**, supporting a positive treatment effect.
- The simulated observational comparison produced an ATE of **−$14,784.45**, with selection bias of **−$16,578.80**. This demonstrated how selection bias can reverse the apparent effect of a program.
- The study's achieved power was **80.8%**.
- The estimated sample sizes needed for 80% power were:
  - **$500 effect:** 2,719 people per group.
  - **$1,000 effect:** 681 people per group.
  - **$2,000 effect:** 171 people per group.

### Cookie Cats A/B Test

- The dataset contained **90,189 players**: 44,700 in `gate_30` and 45,489 in `gate_40`.
- Day-1 retention was **44.82%** for `gate_30` and **44.23%** for `gate_40`.
- The observed difference (`gate_30` minus `gate_40`) was **0.59 percentage points**.
- The permutation test returned **p = 0.0752**.
- The 95% BCa confidence interval was **−0.07 to 1.23 percentage points**. Because the p-value was above 0.05 and the confidence interval included zero, I found insufficient evidence that moving the gate to level 40 improves Day-1 retention.
- My `n_needed()` function estimated that a rerun would require **111,193 players per group** to detect the observed retention difference with 80% power at a 5% significance level.

## Conclusion

This lab showed me why causal inference depends on randomized assignment, appropriate statistical tests, and sufficient sample sizes. The LaLonde experiment demonstrated how selection bias can reverse an estimated treatment effect, while Cookie Cats showed that a small observed difference does not necessarily provide statistically significant evidence for a product change. Power analysis helped me understand how much data would be needed to detect effects of different sizes.
