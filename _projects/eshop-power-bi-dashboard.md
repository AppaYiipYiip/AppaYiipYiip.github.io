---
title: E-Shop BI Dashboard
subtitle: A 4-page Power BI dashboard for a simulated e-commerce business
tier: analysis
year: 2026
stat: "4-page dashboard, 2 fact tables + 4 dimensions, tracking revenue, units sold, and customer engagement"
order: 2
repo: https://github.com/AppaYiipYiip
---

Designed a 4-page Power BI dashboard (executive summary, sales, web analytics,
and KPIs) for a simulated e-commerce business, built on a synthetic retail
dataset.

**What it does**

- Star-schema data model (2 fact tables, 4 dimensions) with DAX measures
  tracking revenue, units sold, and customer engagement
- Data cleaning and transformation in Power Query
- Interactive slicers (time period, region) surfacing insights aimed at
  business decisions, not just reporting

**Decisions worth naming**

- Chose a star schema over a flatter table to keep DAX measures fast and
  reusable across all four report pages rather than duplicating logic per view
- Segmented by period and region specifically because those were the two
  cuts that changed the executive summary's headline numbers the most
- Kept the KPI page separate from the sales page so a fast glance (KPIs) and
  a deep dive (sales) don't compete for the same screen

*A live embed is on the way as this project's walkthrough gets finished.*
