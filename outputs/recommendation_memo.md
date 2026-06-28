# Recommendation Memo
## Onboarding & Activation Campaign — A/B Experiment

**To:** Leadership / Product Decision-Makers
**From:** Business Analyst
**Date:** June 2026
**Re:** Launch Decision — New Onboarding Campaign

---

## 1. Executive Summary

The new onboarding and activation campaign produced a **statistically significant 120.9% lift in paid conversion rate** (3.19% → 7.04%, p = 0.0005). Engagement scores also improved significantly. However, the treatment group shows a **69% increase in support ticket rate** and a **52.7% drop in average revenue per converted user**, which are serious guardrail concerns.

**Recommendation: Phased launch with conditions — do not roll out to 100% of users immediately.**

---

## 2. North Star Metric

**Metric:** Paid Conversion Rate

**Definition:** Users who convert to a paid plan within 30 days / total users in the experiment group.

This metric was selected because it directly captures the business objective of the campaign — improving revenue-generating user conversion. It is the clearest signal of whether the campaign delivers financial value. All other funnel metrics (landing page visits, trial starts, onboarding completions) are upstream inputs to this outcome.

**Risk of optimizing blindly:** If only conversion rate is tracked, the company may celebrate volume while sacrificing revenue quality. A user who converts at $770 average revenue contributes far less than one who converts at $1,630 — the gap seen between treatment and control.

---

## 3. KPI Tree Explanation

The KPI tree breaks Paid Conversion Rate into three primary drivers:

**Acquisition (top-of-funnel):**
- Landing page visit rate: +13.8% in treatment — the campaign drives stronger top-funnel reach
- Trial start rate: +15.7% — more users explore the product

**Activation (mid-funnel):**
- Onboarding completion rate: +35.0% — the single strongest improvement in the entire funnel, suggesting the new experience is significantly easier or more engaging
- Engagement score: +10.4% (statistically significant) — users are more active after the new experience

**Retention quality (post-conversion):**
- Avg revenue per converted user: -52.7% — concerning quality drop; treatment converts more but at lower individual revenue
- Days to convert: -27.8% — positive; treatment users decide faster

**Guardrail metrics** (must not deteriorate): Refund rate, support ticket rate, revenue per converted user.

---

## 4. Experiment Result Summary

| Metric | Control | Treatment | Lift | Status |
|---|---|---|---|---|
| User count | 690 | 710 | — | Balanced |
| Landing page visit rate | 63.62% | 72.39% | +13.8% | ✅ |
| Trial start rate | 25.07% | 29.01% | +15.7% | ✅ |
| Onboarding completion rate | 15.65% | 21.13% | +35.0% | ✅ |
| **Paid conversion rate** | **3.19%** | **7.04%** | **+120.9%** | **✅ Significant** |
| Avg revenue per user | $51.97 | $54.25 | +4.4% | ➡️ Neutral |
| Avg revenue per converted user | $1,630.10 | $770.41 | -52.7% | ⚠️ Risk |
| Refund rate | 0.00% | 0.42% | — | ⚠️ Watch |
| Support ticket rate | 22.03% | 37.32% | +69.4% | 🔴 High risk |
| Avg engagement score | 57.02 | 62.94 | +10.4% | ✅ |
| Avg days to convert | 8.86 | 6.40 | -27.8% | ✅ |

---

## 5. Hypothesis Test Interpretation

- **Test:** One-tailed two-proportion Z-test on paid conversion rate
- **H₀:** Treatment conversion rate ≤ Control conversion rate
- **H₁:** Treatment conversion rate > Control conversion rate
- **Z-statistic:** 3.2640
- **P-value:** 0.000549
- **Decision:** Reject H₀ at α = 0.05

The improvement in conversion rate is **statistically significant and practically large**. The probability of observing this result by chance (under the null) is 0.055%. This is not a borderline result — the campaign meaningfully increases conversion.

Supporting tests confirm engagement is also significantly higher (p < 0.001, T = 8.01), while support ticket volume is also significantly higher in treatment (p < 0.001, T = 4.20) — a real and concerning operational risk.

---

## 6. Guardrail Analysis

### Guardrail 1 — Refund Rate
- Control: 0.00% | Treatment: 0.42% (3 refunds)
- **Risk level: Moderate.** Sample is small but the directional signal is clear — the new experience may be attracting or converting users who are not a strong fit for the product.
- **Action:** Monitor closely post-launch. If refund rate exceeds 1% in the broader rollout, pause and investigate.

### Guardrail 2 — Support Ticket Rate
- Control: 22.03% | Treatment: 37.32% (p < 0.001)
- **Risk level: HIGH.** This is statistically significant and practically material. Treatment users generate ~70% more support tickets per user. At scale, this creates serious customer success costs and may indicate the new onboarding is confusing in parts.
- **Action:** Do not launch 100% until the root cause is identified. Conduct UX research to find friction points in the new experience that drive ticket volume.

### Guardrail 3 — Avg Revenue per Converted User
- Control: $1,630.10 | Treatment: $770.41 (-52.7%)
- **Risk level: HIGH.** Treatment converts more users but those users generate significantly less revenue on average. This could indicate a plan-type shift (more Free users converting to lower-tier plans) or discounting effects.
- **Action:** Analyze conversion distribution by plan type. If treatment is converting lower-tier plans preferentially, revenue per user won't improve despite more conversions. Investigate pricing or upsell strategy.

**Note:** Control has 5 revenue outliers above $2,000, which inflates its average. Even adjusting for this, there is a meaningful quality gap to investigate.

---

## 7. Segment-Level Insight

**Regions:**
- All regions show positive lift; North (+155%) and East (+154%) respond strongest
- West shows the weakest lift (+50.5%) — may warrant separate analysis

**Device type:**
- Mobile shows strongest lift (+186.9%) — the new onboarding may be particularly well-optimized for mobile
- Tablet also strong (+292.9%), though small sample
- Unknown device type (n=9 each) shows negative treatment result — exclude from analysis

**Traffic source:**
- Paid Search (+384%) and Referral (+345%) show exceptional lift — campaign excels for high-intent acquisition channels
- Organic also strong (+211%)
- **Social traffic shows negative lift (-21.8%)** — the new campaign does not work for socially-acquired users; this segment should remain on the current experience or receive a separate variant

**Plan type:**
- Free plan users drive almost all the lift (+204%) — the campaign is most effective for converting free users to paid
- Basic plan users show minimal lift (+7.2%) — investigate whether the new experience is poorly suited to this segment

---

## 8. Final Recommendation

**Recommendation: LAUNCH — phased rollout with segment exclusions**

**Rationale:**
The 120.9% improvement in paid conversion rate is statistically significant (p = 0.0005) and represents a material business opportunity. The engagement improvement is also significant and positive. However, the operational risk from support ticket volume and revenue quality dilution prevents a full immediate rollout.

**Recommended rollout plan:**

| Phase | Scope | Goal |
|---|---|---|
| Phase 1 (Now) | 30-40% of users, excluding Social traffic | Monitor support load and revenue quality at scale |
| Phase 2 (2–4 weeks) | Expand to 70%, fix support friction points | Reduce ticket rate to ≤25% before full launch |
| Phase 3 (4–8 weeks) | Full launch to all eligible users | With social traffic receiving a dedicated optimized variant |

**Do not launch to:** Social traffic (negative lift) until a new variant is tested for this segment.

---

## 9. Risks and Limitations

- **Revenue quality risk:** Lower avg revenue per converted user could reduce LTV over time. Must be monitored monthly.
- **Support cost risk:** 69% more tickets per user at scale could overwhelm CS capacity and increase cost per conversion significantly.
- **Refund exposure:** Small but present — 3 refunds in treatment vs 0 in control.
- **Outlier sensitivity:** Control's avg revenue is inflated by 5 users with >$2,000 revenue. This makes the quality gap appear larger — real gap may be ~30-40% rather than 52.7%.
- **Observation window:** 30-day window may not capture long-term retention or churn differences.
- **Randomization assumption:** Groups are roughly equal in size; no formal randomization checks (e.g. SRM test) were performed.
- **Missing data:** 18 device_type and 24 traffic_source records were imputed as "Unknown" — segment analysis for these is unreliable.

---

## 10. Next Steps

1. **Immediate:** Begin Phase 1 rollout (30-40%) excluding Social traffic; instrument support ticket tracking by onboarding step
2. **Week 1-2:** UX review of new onboarding flow — identify the specific steps causing support volume spike
3. **Week 2-4:** Analyze plan-type conversion distribution in treatment to understand revenue quality gap
4. **Week 4:** Evaluate Phase 2 readiness — has support ticket rate begun to decline with UX fixes?
5. **Ongoing:** Track 60-day and 90-day retention for both cohorts; conversion lift must be durable to justify full launch
6. **New experiment:** Design a Social-traffic-specific onboarding variant to capture this segment
