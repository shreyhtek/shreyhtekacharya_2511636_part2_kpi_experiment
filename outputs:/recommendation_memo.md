# Recommendation Memo
## Campaign Experiment: New Onboarding & Activation Experience

**To:** Leadership / Product Team  
**From:** Business Analyst  
**Date:** June 2026  
**Re:** Launch Decision — New Onboarding Campaign

---

## 1. Executive Summary

The new onboarding and activation campaign (Treatment) **significantly improves paid conversion rate** — the primary North Star metric — increasing it from **3.19% to 7.04% (+120.8% lift)**. However, a **critical guardrail metric has been breached**: Treatment users generate support tickets at a **68% higher rate** (24.79% vs 14.78%). 

**Recommendation: Do not launch to all users yet. Run a revised experiment addressing the support experience, then re-evaluate.**

---

## 2. North Star Metric

**North Star: Paid Conversion Rate**

This metric was selected because it directly measures the business outcome of the campaign — converting users from free/trial to paying. It connects all onboarding and activation efforts to revenue generation, which is the ultimate company objective.

Supporting metrics include: trial start rate, onboarding completion rate, engagement score, and landing page visit rate.

Guardrail metrics (must not worsen): support ticket rate, refund rate, revenue per converted user.

---

## 3. KPI Tree Explanation

The KPI tree breaks the North Star (Paid Conversion Rate) into three primary driver pillars:

1. **Acquisition** — Getting users to the product (Landing Page Visit Rate, Traffic Source Quality)
2. **Activation** — Getting users started and onboarded (Trial Start Rate, Onboarding Completion)
3. **Retention** — Keeping users engaged (Engagement Score, Session Frequency, Feature Adoption)

Guardrail metrics sit outside this hierarchy and protect business health: support ticket rate, refund rate, days to convert, and revenue per converted user.

---

## 4. Experiment Result Summary

| Metric | Control | Treatment | Difference | Significant? |
|--------|---------|-----------|------------|-------------|
| User Count | 690 | 710 | +20 | — |
| Landing Page Visit Rate | 63.62% | 72.39% | +8.77pp | — |
| Trial Start Rate | 25.07% | 29.01% | +3.94pp | — |
| Onboarding Completion Rate | 15.65% | 21.13% | +5.48pp | — |
| **Paid Conversion Rate ★** | **3.19%** | **7.04%** | **+3.85pp** | **Yes (p=0.0006)** |
| Avg Revenue Per User | $51.97 | $54.25 | +$2.28 | No (p=0.91) |
| Avg Engagement Score | 57.03 | 62.94 | +5.91 | Yes (p<0.001) |
| **Support Ticket Rate ⚠️** | **14.78%** | **24.79%** | **+10.01pp** | **Yes — BREACH** |
| Refund Rate | 0.00% | 0.42% | +0.42pp | Low concern |
| Avg Days to Convert | 8.9 | 6.4 | -2.5 days | Positive trend |

---

## 5. Hypothesis Test Interpretation

- **Primary test (Z-test for proportions, one-tailed):**
  - Z = 3.264, P = 0.00055
  - **Result: Reject H₀** — Treatment conversion rate is significantly higher
  
- **Engagement T-test:**
  - T = 7.93, P < 0.000001
  - Treatment users are meaningfully more engaged

- **Support ticket Z-test (Guardrail):**
  - Z = 4.69, P = 0.000003
  - Treatment triggers significantly more support requests — **guardrail breached**

---

## 6. Guardrail Analysis

The **support ticket rate** is the key concern:

- Control: 14.78% of users raised support tickets
- Treatment: 24.79% — a **68% relative increase**, statistically significant
- Possible causes: The new onboarding experience may be more complex, introduce UI confusion, or set unclear expectations about the product
- Business risk: Higher support volume increases operational cost and may signal poor user experience that damages long-term retention

The refund rate increase (0% → 0.42%) is small and not statistically significant, but worth monitoring.

---

## 7. Segment-Level Insights

**By Region:**
- Treatment outperforms Control in all regions
- North shows highest Treatment lift (+8.89% vs +3.48% Control)

**By Device Type:**
- Mobile users in Treatment show largest conversion gains (7.41% vs 2.58%)
- Desktop and Tablet also improve
- Mobile is both the largest segment and the biggest beneficiary

**By Plan Type:**
- Free plan users show dramatic lift in Treatment (9.29% vs 3.06%)
- Basic and Premium plans also improve
- Free → Paid conversion is where the campaign has the most impact

**By Traffic Source:**
- Referral traffic in Treatment has the highest conversion (10.99%)
- All traffic sources improve in Treatment

---

## 8. Final Recommendation

**Do not launch to all users at this time.**

The conversion improvement is real and significant, but the support ticket surge cannot be ignored. A full launch would:
- Increase paid conversions (positive)
- Significantly increase support volume and cost (negative)
- Risk user satisfaction if the onboarding experience is causing confusion

**Recommended next steps:**

1. **Investigate the support tickets** — What are Treatment users asking for? Identify the top 3 failure points in the new onboarding flow.
2. **Fix the UX issues** causing confusion — likely in the onboarding steps between trial start and conversion.
3. **Consider a limited launch** to Mobile + Free plan users (highest benefit, clearest segment) while the issues are investigated.
4. **Re-run the experiment** after fixing the onboarding friction points, monitoring both conversion AND support ticket rate.
5. **Power analysis** — Run a formal sample size calculation before the next experiment to ensure statistical power.

---

## 9. Risks and Limitations

- **Support ticket risk is material**: A 68% increase in support demand has operational and satisfaction implications
- **Short observation window**: 30-day revenue may understate long-term value of converted users
- **Avg revenue per converted user is lower in Treatment** ($770 vs $1,630) — possibly driven by mix of plan types; needs deeper investigation
- **No power analysis performed** — the experiment may not have been adequately powered for all metrics
- **Causal attribution**: Segment differences may be driven by randomization variance, not segment-specific effects

---

## 10. Next Steps

| Priority | Action | Owner | Timeline |
|----------|--------|-------|----------|
| 1 | Analyze support ticket categories from Treatment group | Support + Product | 1 week |
| 2 | Fix top 3 onboarding friction points | Engineering | 2–3 weeks |
| 3 | Launch limited test to Mobile + Free segment | Product | After fix |
| 4 | Re-run experiment with monitoring dashboard | Analytics | 4 weeks |
| 5 | Run power analysis for next experiment | Analytics | Before next test |
