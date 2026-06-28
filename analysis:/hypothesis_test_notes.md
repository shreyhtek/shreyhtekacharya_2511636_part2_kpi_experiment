# Hypothesis Test Notes
## Campaign Experiment — Onboarding & Activation

---

## 1. Null Hypothesis (H₀)

The new onboarding and activation campaign (Treatment) does **not** improve the paid conversion rate compared to the existing experience (Control).

> H₀: p_treatment ≤ p_control  
> (Conversion rate of Treatment ≤ Conversion rate of Control)

---

## 2. Alternate Hypothesis (H₁)

The new campaign **increases** the paid conversion rate.

> H₁: p_treatment > p_control  
> (One-tailed test — we care about improvement only)

---

## 3. Test Type

**One-tailed Z-test for proportions** (right-tailed)

- Reason: We are testing whether Treatment is *better* (higher conversion), not just *different*. A one-tailed test is appropriate when the business question is directional.
- Both groups have large sample sizes (n > 30), satisfying the normal approximation assumption.

---

## 4. Significance Level

**α = 0.05** (5% significance level)

- Industry standard for A/B testing decisions
- Balances risk of false positives vs false negatives
- A p-value below 0.05 leads us to reject H₀

---

## 5. Metric Being Tested

**Primary Metric: Paid Conversion Rate**

- Defined as: Users who converted to paid / Total users in group
- This is the North Star metric — the most direct measure of campaign success
- All other metrics are supporting or guardrail metrics

---

## 6. Reason for Choosing This Metric

Paid conversion rate is the primary business objective of this experiment. The company wants to know whether the new onboarding experience converts more free/trial users into paying customers. It directly measures revenue impact and is the clearest signal of whether the campaign achieves its goal.

---

## 7. Test Results

| Parameter | Value |
|-----------|-------|
| Control conversions | 22 / 690 = 3.19% |
| Treatment conversions | 50 / 710 = 7.04% |
| Difference | +3.85 percentage points |
| Lift | +120.8% relative improvement |
| Z-statistic | 3.2640 |
| P-value | 0.000549 |
| Significant at α=0.05 | **Yes** |

---

## 8. Additional Tests (Supporting & Guardrail Metrics)

### Engagement Score (T-test, Independent Samples)
- H₀: Mean engagement score is equal between groups
- H₁: Treatment has higher mean engagement score
- T-statistic: 7.9275 | P-value: < 0.000001 | **Significant**
- Interpretation: Treatment users are significantly more engaged — supports campaign effectiveness

### Revenue Per User (T-test, Independent Samples)
- H₀: Mean revenue per user is equal between groups
- H₁: Revenue differs between groups
- T-statistic: 0.1131 | P-value: 0.9100 | **Not significant**
- Interpretation: No meaningful revenue difference per user overall — consistent with conversion being the primary driver

### Support Ticket Rate (Z-test for proportions) — GUARDRAIL
- H₀: Support ticket rate is equal between groups
- H₁: Rate differs
- Z-statistic: 4.6921 | P-value: 0.000003 | **Significant — GUARDRAIL BREACH**
- Control: 14.78% | Treatment: 24.79% | Difference: +10.01 pp
- Interpretation: ⚠️ The Treatment group generates significantly more support tickets. This is a critical guardrail concern — the new experience may be confusing users, creating operational cost and satisfaction risk.

---

## 9. Interpretation Logic & Business Decision

**The test provides strong statistical evidence to reject H₀.** The Treatment campaign significantly improves paid conversion rate (p = 0.00055, well below α = 0.05).

However, the **support ticket guardrail has been breached**: Treatment users raise support tickets at a 68% higher rate than Control users (24.79% vs 14.78%). This is a significant operational and user-experience concern.

**Business interpretation:**
- The campaign works at converting users (good)
- But it appears to confuse or overwhelm users, leading to much higher support load (bad)
- A full launch without addressing the support ticket issue would increase operational costs and risk user satisfaction

**Recommendation:** Do not launch to all users immediately. Investigate the cause of elevated support tickets, then re-test with a corrected experience.

---

## 10. Assumptions & Limitations

1. Users were randomly assigned — assumed based on dataset structure (not verified via balance test)
2. No interaction effects between segments were tested
3. 30-day revenue window may not capture full long-term value
4. Experiment duration and sample size adequacy not evaluated (power analysis not performed)
