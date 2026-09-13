# From Accepted Offers to Retained Nurses

## A Workforce Measurement Review

**Independent review of public information**  
Prepared by Yash Vekhande | Evidence reviewed September 13, 2026

A concise analytical brief reviewing Ascension's publicly reported nurse hiring, retention, and preceptor-training measures. Prepared as an independent application supplement for the Data Scientist role in Workforce Intelligence and Insights.

**[Read the PDF brief](Ascension_Workforce_Measurement_Review.pdf)** · **[Read the editable Markdown version](Ascension_Workforce_Measurement_Review.md)**

The PDF contains two pages of analysis and a one-page source appendix, with professional formatting and clickable citations.

## Business question

> What additional measurement would distinguish increased hiring activity from sustained workforce stability?

## What the review covers

| Public measure | Analytical distinction | Additional measurement proposed |
|---|---|---|
| Accepted offers | Higher volume does not establish a higher acceptance rate. | Offers-issued denominators, decision windows, and conversion to actual starts. |
| Retention at different milestones | Comparisons require consistent populations, cohorts, definitions, and follow-up. | Linked employment spells and an identical start cohort eligible for both milestones. |
| Completed preceptor training | Training activity does not establish employee exposure or program effects. | Preceptor assignments, timing and intensity of support, and subsequent onboarding and employment outcomes. |

## Proposed analytical design

**Offers issued → accepted offers → actual starts → retained at 90 days → retained at 365 days**

The specification defines five measures: offer acceptance, accepted-offer-to-start conversion, 90-day retention, 365-day retention, and internal mobility. Each includes a numerator, denominator, observation rule, and an important edge case.

The design prioritizes:

- Fixed decision and start windows, with pending and late outcomes identified separately.
- Sufficient follow-up before classifying retention, including for employees who leave early.
- Distinct employment spells for rehires and one originating offer per actual start.
- Separate treatment of internal transfers and organizational departures.
- Minimum proposed data fields and a SQL/Python validation workflow for stakeholder discussion.

These are proposed analytical requirements. The review uses public information and contains no employee-level data. The SQL/Python workflow is a specification for discussion; it has not been implemented against Ascension systems.

## Sources and interpretation limits

The brief uses three official Ascension publications:

1. [FY25 nursing results announcement](https://about.ascension.org/news/2025/06/ascension-releases-fy25-annual-nursing-report), published June 30, 2025.
2. [Nurse preceptor training announcement](https://about.ascension.org/news/2025/03/ascension-boosts-interest-in-nurse-preceptorship), published March 12, 2025.
3. [FY2026 Q3 management discussion](https://about.ascension.org/-/media/project/ascension/about/section-about/financials/2026/ascension-management-discussion-and-analysis-q3-fy26.pdf), reporting as of and for the nine months ended March 31, 2026 and 2025. The relevant nurse-retention passage is on printed page 6 (PDF page 7).

The source appendix records the evidence locations, dates, and verification limits. A linked underlying nursing report could not be opened during research, and that access limitation is documented.

Historical figures are used only in their stated reporting contexts. Public information reviewed here does not establish comparable retention cohorts or a causal effect of preceptor training. Missing public detail is not evidence of missing internal capability. Proposed fields do not describe or assert the structure of Ascension's Oracle schema.

## Repository contents

```text
.
├── README.md
├── .gitattributes
├── .gitignore
├── Ascension_Workforce_Measurement_Review.pdf
└── Ascension_Workforce_Measurement_Review.md
```

## Verification

- Checked the requested numerical claims, source dates, and relevant source passages.
- Confirmed the PDF contains three pages and includes clickable source links.
- Rendered and visually inspected each page for legibility, clipping, and layout problems.
- Preserved the same analytical content in the editable Markdown version.

This is an independent portfolio review, not an Ascension publication or an assertion of program ownership. Ascension has not endorsed this work. Referenced source materials belong to their respective owners.
