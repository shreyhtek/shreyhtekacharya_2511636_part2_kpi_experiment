Part 2: KPI Framework & Experiment Analysis

Campaign: New Onboarding & Activation Experience


1. Business Context

A subscription-based digital product company ran an A/B experiment to evaluate a new onboarding and activation campaign. Users were randomly assigned to:


Control group: Existing onboarding experience (690 users)
Treatment group: New campaign experience (710 users)


Leadership wants to know whether to launch the new experience to all users.


2. Dataset Description

AttributeDetailSource filedata/campaign_experiment_data.xlsxTotal rows1,408 (1,400 after deduplication)Columns16Key fieldsuser_id, experiment_group, region, device_type, traffic_source, plan_type, binary funnel steps, revenue_30d, support_tickets_30d, engagement_scoreDate rangeFeb – May 2025


3. North Star Metric Selected

Paid Conversion Rate — Users who converted to paid / Total users in group

This metric was chosen because:


It directly measures the business goal of the campaign (converting users to paying customers)
It connects all activation and onboarding efforts to revenue generation
It is unambiguous and measurable from the dataset
Other metrics (trial start, onboarding completion, engagement) are supporting drivers of this outcome


What could go wrong if optimized blindly: the campaign could inflate conversions by attracting low-quality users who churn quickly, or by pressuring users into paid plans they don't need — damaging long-term retention.


4. KPI Tree Summary

The North Star (Paid Conversion Rate) is driven by three pillars:

★ Paid Conversion Rate (North Star)
├── ACQUISITION
│   ├── Landing Page Visit Rate
│   └── Traffic Source Quality
├── ACTIVATION
│   ├── Trial Start Rate
│   └── Onboarding Completion Rate
├── RETENTION
│   ├── Engagement Score
│   └── Feature Adoption / Session Frequency
└── GUARDRAILS
    ├── Support Ticket Rate (must not increase)
    ├── Refund Rate (must not increase)
    ├── Revenue Per Converted User (must not drop significantly)
    └── Days to Convert (faster is better)

See outputs/kpi_tree.png for the visual KPI tree diagram.


5. Experiment Analysis Approach

Data Preparation (Task 4):


Removed 8 duplicate user_ids (kept first occurrence)
Noted missing values: device_type (18), traffic_source (24), engagement_score (14)
Validated all binary columns — no invalid values found
Identified revenue outliers (max $8,610) — retained as legitimate converted users
Groups were well-balanced (~50/50 split)


Metrics Computed (Task 5):
All 11 required metrics computed for Control vs Treatment:
landing page visit rate, trial start rate, onboarding completion rate, paid conversion rate, avg revenue per user, avg revenue per converted user, refund rate, support ticket rate, avg engagement score, avg days to convert.

Segment analysis conducted for: Region, Device Type, Plan Type, Traffic Source.


6. Hypothesis Test Summary

Primary Test: Paid Conversion Rate (Z-test for proportions, one-tailed)

ValueH₀Treatment conversion ≤ Control conversionH₁Treatment conversion > Control conversionTest typeOne-tailed Z-test for proportionsα (significance level)0.05Z-statistic3.264P-value0.000549DecisionReject H₀ — Treatment significantly outperforms

Guardrail Test: Support Ticket Rate (Z-test)


Z = 4.69, P = 0.000003 — Significant breach: Treatment users raise 68% more support tickets


Engagement Score (T-test)


T = 7.93, P < 0.000001 — Significant: Treatment users significantly more engaged



7. Guardrail Metrics Considered

GuardrailControlTreatmentStatusSupport Ticket Rate14.78%24.79%⚠️ BREACHEDRefund Rate0.00%0.42%✓ OK (not significant)Avg Revenue Per Converted User$1,630$770⚠️ Worth investigatingAvg Days to Convert8.96.4✓ Improved


8. Final Recommendation

Recommendation: Do Not Launch to All Users — Investigate Support Issues First

The campaign successfully improves paid conversion (+120.8% lift, statistically significant). However, the support ticket guardrail has been critically breached (+68% increase in Treatment, p < 0.001). Launching without resolving this would increase operational costs and risk user satisfaction.

Suggested path: Fix the top onboarding UX friction points identified through support ticket analysis, then re-run the experiment. Consider a limited launch to Mobile + Free plan users (highest benefit segment) in the interim.


9. Assumptions and Limitations


Users were assumed to be randomly assigned to groups (not independently verified)
30-day revenue window may not capture full long-term customer value
No formal power analysis was performed before or after the experiment
Segment-level effects may be driven by sample variance rather than true differential impact
Missing values in device_type and traffic_source were retained; their exclusion from some segment rows is acknowledged
The higher average revenue per converted user in Control ($1,630 vs $770) may reflect plan-mix differences rather than value destruction



10. Screenshots Included

FileContentscreenshots/summary_metrics.pngControl vs Treatment summary metrics tablescreenshots/hypothesis_test_output.pngHypothesis test results and statistical outputscreenshots/kpi_tree_preview.pngKPI tree diagram preview
