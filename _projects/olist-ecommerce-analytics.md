---
title: Olist E-Commerce Analytics
subtitle: A 10-page Power BI report analyzing $16M+ in real Brazilian e-commerce orders, from data model to AI-driven insights
tier: flagship
year: 2026
stat: "$16.01M in revenue across ~99K orders, with a 3.12% repeat customer rate as the central open question"
order: 1
image: /assets/images/projects/olist/overview.png
repo: https://github.com/AppaYiipYiip/olist-ecommerce-analytics
source_logo: /assets/images/olist.png
source_name: Olist dataset
---

A 10-page Power BI report built on Olist's public Brazilian e-commerce dataset
(2016 to 2018): Overview, Sales Performance, Sellers & Marketplace, Product
Catalog & Listing Quality, Customers & Geography, Payments, Delivery &
Logistics, Reviews & Customer Experience, AI Insights, and Key Influencers.
A star-schema data model, DAX measures across every page, and a written
findings report that tracks not just the results but the methodology
mistakes that had to be caught and fixed along the way.

**Headline numbers**

- $16.01M total revenue across ~99K orders, growing steadily from late 2016
  through 2018, but carried almost entirely by new customers: repeat
  customer rate sits at just 3.12%
- Top 5 product categories account for 39.74% of revenue; the top 10
  sellers account for only 13.15%, so concentration risk sits on the
  category side, not the seller side
- 93.23% on-time delivery, and transit time (the carrier's own leg after
  pickup) is the single strongest driver of review score, confirmed
  independently by both a hand-built comparison and Power BI's Key
  Influencers AI visual
- 78.34% of revenue runs through a single payment rail (credit card)

![Sellers & Marketplace page: revenue by seller, item revenue by seller tier, late delivery and review score by tier](/assets/images/projects/olist/sellers-marketplace.png)

**Decisions worth naming**

- Fixed a relationship deadlock in the data model: `fact_orders` and
  `fact_order_items` needed to filter in both directions for the seller and
  product pages to work, but making that join bidirectional created a
  cyclic reference through the Date table. Built TREATAS-based bridge
  measures instead of forcing a relationship that would have silently
  broken time intelligence elsewhere.
- Removed `payment_type` from the AI visuals rather than patching around
  it, after it broke Key Influencers outright (an ambiguous multi-hop path
  to the fact table) and silently corrupted the Decomposition Tree (a
  revenue figure that looked fine but wasn't actually bridged to
  product-level data).
- Rebuilt the "new vs. returning customers" chart from scratch after
  discovering it had been reported as finished in an earlier draft of this
  same report when only the DAX had actually been written. Shipping that
  chart was also what fixed an unrelated month-axis bug, because the
  version that was actually live had never been able to handle months
  cleanly in the first place.
- Scoped the payment installment analysis to credit-card orders only,
  since every other payment type structurally sits at one installment with
  no real choice involved. Pooling all payment types together, the
  original approach, was quietly distorting the comparison.
- Declined to report Power BI's own top answer for what predicts a repeat
  customer. Key Influencers pointed to "Customer Value Tier", but that
  field is partly built from total spend, which is mechanically higher for
  repeat buyers by definition. Flagged it as circular instead of reporting
  it as a finding.

![AI Insights decomposition tree and Key Influencers pages, used to cross-check findings from the hand-built report pages](/assets/images/projects/olist/key-influencers.png)

**Where it's still open**

Two results in the report are marked explicitly as not fully resolved: the
"days vs. estimate" delivery trend chart needs a manual axis fix, and the
real question this whole project was built to answer, what actually
predicts a customer coming back, still doesn't have a confirmed answer.
The closest attempt turned out to be circular. That gap is the next thing
this project will go after.

Full data model documentation, every DAX measure, and the complete
findings write-up (including the parts that didn't work on the first
attempt) are in the GitHub repo.
