---
title: Social Network Database Modeling & SQL Analysis
subtitle: Normalizing ~100,000 tweets into a 3NF schema and mining behavior with advanced SQL
tier: engineering
year: 2025
stat: "86% of replies stayed in the same language, vs. 48% expected by chance"
order: 3
repo: https://github.com/AppaYiipYiip
source_logo: /assets/images/twitter-logo.webp
source_name: Twitter dataset
---

Took a denormalized database of roughly 100,000 tweets and turned it into a
proper relational model, then used that model to answer real behavioral
questions with SQL.

**What it does**

- Designed a normalized (3NF) relational schema from the denormalized source,
  including entity-relationship modeling and SQL migration scripts
- Wrote advanced analytical queries (CTEs, window functions, subqueries) to
  extract user behavior indicators
- Key finding: language distribution of activity and homophily between users.
  86% of replies occurred in the same language, versus 48% expected by chance

**Decisions worth naming**

- Normalized to 3NF specifically to eliminate the update anomalies that made
  the original denormalized structure unreliable for aggregate queries
- Used window functions instead of self-joins for the behavior metrics:
  cheaper to reason about and faster over ~100K rows
- Reported homophily against a random-chance baseline (48%) rather than a raw
  percentage alone, since the number only means something in contrast
