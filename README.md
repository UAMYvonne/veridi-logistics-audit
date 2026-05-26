# Veridi Logistics — Delivery Performance Audit

## A. Executive Summary
Veridi Logistics delivers 91.9% of its 96,470 orders on time. However,
8.1% of customers (7,826 orders) experience late deliveries, and when
delays occur they are severe — super late orders (5+ days) outnumber
mildly late ones. The data confirms the CEO's hypothesis: late deliveries
directly cause negative reviews, with super late orders averaging just
1.78 out of 5 stars compared to 4.29 for on-time orders. The state of
AL has the highest late rate at 23.9%, nearly 3x the national average,
confirming this is a regional last-mile problem, not a nationwide one.

## B. Project Links
- **Notebook:** [https://colab.research.google.com/drive/1HpgI6eX_O_ECLYNTuhnJ8PFoe1lFlv8q?usp=sharing]
- **Dashboard:** [https://datastudio.google.com/reporting/bd8f6ca4-7a70-4e6d-b328-3114ac221072]
- **Presentation:** [https://docs.google.com/presentation/d/1sa2Hg9ofoTd8MVB5-ZOFAjjtpCcopMRB3mfv63OkCMY/edit?usp=sharing]

## C. Technical Explanation

### Data Cleaning
-  I Removed canceled and unavailable orders before delay calculations
-  I Deduplicated reviews by keeping the most recent review per order_id
  to avoid row inflation on the 1-to-many join
- I Converted all date columns from string to datetime before calculating
  Days_Difference = estimated_delivery_date - actual_delivery_date
- I Excluded orders missing either delivery date

### Candidate's Choice — Monthly Late Rate Trend
I added a monthly time-series analysis of late delivery volume over time.
This matters to the business because a static snapshot does not reveal
whether performance is improving or deteriorating. The spike visible in
late 2017 and early 2018 exposes a seasonal pressure point that operations
teams can investigate and plan for. This turns the audit from a one-time
diagnosis into an ongoing monitoring tool.
