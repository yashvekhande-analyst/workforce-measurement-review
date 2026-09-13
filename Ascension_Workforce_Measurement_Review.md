# From Accepted Offers to Retained Nurses: A Workforce Measurement Review

**Independent review of public information**

Independent application supplement | September 13, 2026

## Page 1: Evidence and interpretation

> **What additional measurement would distinguish increased hiring activity from sustained workforce stability?**

Link offers to employment spells and observe the same hires over time. The public figures below inform that design; they do not alone establish end-to-end workforce stability.

### Accepted-offer growth measures volume

**Public evidence.** The June 30, 2025 announcement reports an 18% increase in accepted offers during the direct-care RN hiring sprint, October 2024-February 2025, versus the preceding five months. [[1]](https://about.ascension.org/news/2025/06/ascension-releases-fy25-annual-nursing-report)

**Interpretation.** This supports higher accepted-offer volume. An improved acceptance rate would also require the number of offers issued to a comparable population.

**Unknown publicly.** Offers-issued counts, decision timing, offer revisions, and the mix of internal and external candidates are not specified for that comparison.

**Decision enabled.** Separate a change in recruiting volume from a change in offer conversion, then assess how many acceptances become starts.

### Retention comparisons require aligned cohorts

**Public evidence.** The June 30, 2025 release reports 88.31% 90-day retention and 65.56% one-year retention in its April 2024-March 2025 improvement discussion. [[1]](https://about.ascension.org/news/2025/06/ascension-releases-fy25-annual-nursing-report) The FY2026 Q3 discussion, covering the nine months ended March 31, 2026, reports approximately 88% 90-day nurse retention (printed p. 6). [[3]](https://about.ascension.org/-/media/project/ascension/about/section-about/financials/2026/ascension-management-discussion-and-analysis-q3-fy26.pdf)

**Interpretation.** These are reported retention levels for their stated contexts. Neither a common survival curve nor a precise trend across publications is established.

**Unknown publicly.** Hire cohorts, denominator counts, eligible nurse populations, observation cutoffs, and treatment of transfers and leaves are not defined in the cited passages.

**Decision enabled.** Use an identical cohort with sufficient follow-up to distinguish early retention from later departures. Subtracting the published percentages cannot establish post-onboarding attrition.

### Preceptor training measures program activity

**Public evidence.** The March 12, 2025 announcement reports that more than 3,200 nurses had completed preceptor training as of January; the sentence does not specify the year. [[2]](https://about.ascension.org/news/2025/03/ascension-boosts-interest-in-nurse-preceptorship)

**Interpretation.** The count demonstrates training completion, without establishing how much support new nurses received or its effect on retention.

**Unknown publicly.** Preceptor-to-hire assignments, timing, duration or intensity of support, and linked onboarding and employment outcomes are not reported.

**Decision enabled.** Assess whether trained preceptors reach incoming nurses and whether exposure is associated with onboarding completion or retention, accounting for role, facility and hire timing before considering causal evaluation.

Scope: Independent application supplement for the Workforce Intelligence and Insights Data Scientist role. Gaps here concern public detail, not internal capability, metric accuracy, or program ownership. Historical figures are not presented as current performance.


---

## Page 2: Proposed measurement specification

**Proposed analytical design**

Offers issued → accepted offers → actual starts → retained at 90 days → retained at 365 days

Define nurses at entry and the organizational boundary; separate external hires from internal moves. Set fixed windows A (issue to acceptance) and S (acceptance to start) before analysis. Use one offer-issue cohort with full A + S + 365 days of follow-up for the complete funnel; preserve offer-to-person-to-employment-spell links. Track late decisions and starts separately.

For newer cohorts, show each stage’s eligible denominator and pending count; do not multiply rates from different samples. Compare 90- and 365-day retention within the identical actual-start cohort already eligible for 365 days. Freeze the reporting cutoff and show counts alongside percentages.

| Measure | Numerator and denominator | Observation rule and edge case |
|---|---|---|
| Offer acceptance rate | Numerator: valid offers accepted within A days of issue. Denominator: all valid offers in the issue cohort with issue date + A ≤ cutoff. | Read outcomes through day A. Pending offers before maturity remain pending; unresolved offers at day A are nonacceptances within A and flagged. Retain rescinded offers in the denominator, with reason reported. |
| Accepted-offer-to-start conversion | Numerator: eligible acceptances linked to an actual start within S days. Denominator: offers accepted within A, with acceptance date + S ≤ cutoff. | Start the clock at acceptance. A delayed start beyond S misses the window; report later starts separately. Do not extend S retrospectively to accommodate delays. |
| 90-day retention | Numerator: eligible start spells continuously employed in the organization through day 90. Denominator: starts with start date + 90 ≤ cutoff. | Use calendar days from actual start. Approved leave counts as employed if the employment relationship continues; flag leave separately. Recent hires are ineligible, not failures. |
| 365-day retention | Numerator: eligible start spells continuously employed in the organization through day 365. Denominator: starts with start date + 365 ≤ cutoff. | A departure effective on or before the milestone fails retention. A rehire begins a new spell and cannot reverse the prior spell’s departure; report rehires separately. |
| Internal mobility | Numerator: eligible starters with at least one internal unit, facility or role move within h days. Denominator: starts with start date + h ≤ cutoff; h is 90 or 365. | Count each spell once at each level. Moves preserve organizational retention but can end origin-unit or facility continuity. A mover who later leaves is also a departure; the outcomes can overlap. |

### Minimum proposed data fields

Pseudonymous person, offer and employment-spell IDs; offer issue/decision dates and outcomes; expected and actual start dates; role, unit and facility histories; employment events with effective dates and reasons; transfer dates; reporting cutoff. Add offer revision links for deduplication and preceptor assignment IDs, training dates and exposure dates/hours for onboarding analysis. These are proposed requirements, not assertions about Ascension’s Oracle schema.

### Three priority validation checks

1. Resolve duplicate/revised offers; link each unique start spell to one originating offer and identify rehires. 2. Enforce follow-up eligibility before classifying retention, including early leavers. 3. Reconcile transfers and departures at unit, facility and organization levels, flagging boundary changes.

A proposed SQL event-to-spell pipeline with Python validation would produce versioned cohort counts and exception records for stakeholder review.

### Stakeholder discussion

1. Which nurse groups and organizational boundary should govern the funnel, and how should internal offers be separated?
2. Which A and S windows, leave rules and reporting cutoff should be fixed before comparing cohorts?
3. Can preceptor assignments and exposure be linked to hires, and which onboarding outcome would guide the first review?


---

## Source appendix

### [1] FY25 nursing results announcement

[Ascension Releases FY25 Annual Nursing Report](https://about.ascension.org/news/2025/06/ascension-releases-fy25-annual-nursing-report)

Published June 30, 2025.

Relevant passages: nurse-retention bullets and the workforce-investment hiring-sprint bullet. Retention discussion references April 2024-March 2025; sprint comparison is October 2024-February 2025 versus the preceding five months.

Verified the accepted-offer increase and both retention percentages against the announcement. Underlying counts and cohort definitions are not provided in those passages.

URL: <https://about.ascension.org/news/2025/06/ascension-releases-fy25-annual-nursing-report>

### [2] Nurse preceptor training announcement

[Ascension boosts interest in nurse preceptorship through revamped training program](https://about.ascension.org/news/2025/03/ascension-boosts-interest-in-nurse-preceptorship)

Published March 12, 2025.

Relevant passage: final factual paragraph before the read-more link, reporting completed preceptor training as of January.

Verified the count of more than 3,200. January 2025 is suggested by publication timing, but the source sentence does not name the year; the analysis retains “January.”

URL: <https://about.ascension.org/news/2025/03/ascension-boosts-interest-in-nurse-preceptorship>

### [3] FY2026 Q3 management discussion

[Management’s Discussion and Analysis of Financial Condition and Results of Operations for Ascension](https://about.ascension.org/-/media/project/ascension/about/section-about/financials/2026/ascension-management-discussion-and-analysis-q3-fy26.pdf)

Reporting period: as of and for the nine months ended March 31, 2026 and 2025. No separate publication date is shown in the reviewed PDF.

Relevant locations: cover (PDF page 1) for reporting dates; “Total Operating Expenses,” printed page 6 (PDF page 7), first labor-efficiency bullet for nurse retention.

Verified approximately 88% 90-day nurse retention. The document’s reporting period does not establish the hire cohort or measurement window for this particular statistic.

URL: <https://about.ascension.org/-/media/project/ascension/about/section-about/financials/2026/ascension-management-discussion-and-analysis-q3-fy26.pdf>

### [4] Linked underlying nursing report: access limit

[FY25 Annual Nursing Report (Issuu link from source 1)](https://issuu.com/ascensionorg/docs/ascension_nursing_fy2025_annual_report)

Attempted September 13, 2026.

The linked report could not be opened by the research browser, which returned a non-retryable access error. Its definitions and page locations were not verified.

This limits the review to the accessible announcements and management discussion; it is not evidence that internal definitions are absent.

URL: <https://issuu.com/ascensionorg/docs/ascension_nursing_fy2025_annual_report>

Verification note: Sources were accessed September 13, 2026. All requested figures were checked against the accessible source text. No derived performance calculation is presented; in particular, no subtraction of the retention percentages or causal estimate is made. Proposed windows and definitions are analytical choices for discussion.
