# Hypothesis Test Notes — Onboarding & Activation Campaign

## Metric Being Tested

**Paid Conversion Rate** — the proportion of users who convert from free/trial to a paid subscription within 30 days.

### Reason for Choosing This Metric
Paid Conversion Rate is the North Star metric for this experiment. It is the most direct measure of whether the new onboarding campaign achieves its core business objective: turning new users into paying customers. Every other metric in the funnel (landing page visits, trial starts, onboarding completions) is an input to this outcome. If conversion rate improves significantly, the campaign is generating measurable business value.

---

## Hypotheses

**Null Hypothesis (H₀):**
> The paid conversion rate of the Treatment group is equal to or less than that of the Control group.
> H₀: p_treatment ≤ p_control

**Alternate Hypothesis (H₁):**
> The paid conversion rate of the Treatment group is greater than that of the Control group.
> H₁: p_treatment > p_control

---

## Test Configuration

| Parameter | Value |
|---|---|
| Test type | Two-proportion Z-test |
| Tail | One-tailed (right-tailed) |
| Significance level (α) | 0.05 |
| Confidence level | 95% |

**Why one-tailed?**
The business question is directional: "Is the treatment *better* than control?" We are not testing for any difference — we are testing for a specific improvement. A one-tailed test is appropriate and gives us more statistical power to detect improvement in the correct direction.

**Why a Z-test for proportions?**
Paid conversion rate is a binary outcome (converted = 1, not converted = 0). The two-proportion Z-test is the standard method for comparing binary rates between two independent groups, and sample sizes are large enough (n > 600 in each group) for the normal approximation to hold.

---

## Test Inputs

| Input | Control | Treatment |
|---|---|---|
| Group size (n) | 690 | 710 |
| Conversions | 22 | 50 |
| Conversion rate | 3.19% | 7.04% |
| Pooled proportion (p̂) | 0.0514 | — |

---

## Test Output

**Manual Z-test calculation:**

```
p1 (Treatment) = 50/710 = 0.07042
p2 (Control)   = 22/690 = 0.03188
p_pool         = (50+22)/(710+690) = 72/1400 = 0.05143

SE = sqrt(p_pool × (1 - p_pool) × (1/n1 + 1/n2))
   = sqrt(0.05143 × 0.94857 × (1/710 + 1/690))
   = sqrt(0.05143 × 0.94857 × 0.002859)
   = 0.01172

Z  = (p1 - p2) / SE
   = (0.07042 - 0.03188) / 0.01172
   = 0.03854 / 0.01172
   = 3.2640

P-value (one-tailed) = 1 - Φ(3.2640) = 0.000549
```

| Output | Value |
|---|---|
| Z-statistic | 3.2640 |
| P-value (one-tailed) | 0.000549 |
| Decision rule | Reject H₀ if p-value < 0.05 |
| Decision | **Reject H₀** |

---

## Decision Rule & Interpretation Logic

**Decision rule:**
If p-value < 0.05, reject the null hypothesis and conclude there is statistically significant evidence that the treatment improves paid conversion rate.

**Result:**
P-value = 0.000549 < 0.05 → **Reject H₀**

**Business interpretation:**
There is strong statistical evidence that the new onboarding campaign drives a meaningfully higher paid conversion rate. The probability of observing a 120.9% lift in conversion rate (from 3.19% → 7.04%) by chance alone, assuming the null hypothesis were true, is only 0.055% — well below our 5% threshold.

This finding alone supports launching the campaign. However, the statistical test only evaluates the primary metric. The final recommendation must also account for guardrail metric performance (see Task 8 and recommendation memo).

---

## Supporting Tests

| Metric | Test | Statistic | P-value | Result |
|---|---|---|---|---|
| Avg revenue per user | Welch's t-test | T = 0.1131 | 0.455 | Not significant |
| Avg engagement score | Welch's t-test | T = 8.0096 | < 0.001 | ✅ Significant improvement |
| Support ticket rate | Welch's t-test | T = 4.2005 | < 0.001 | 🔴 Significantly higher in treatment |

**Connection to business decision:**
- Engagement improvement confirms that users in treatment are more active — supporting long-term retention potential
- The significant increase in support tickets is a major guardrail concern that must be resolved before full rollout
