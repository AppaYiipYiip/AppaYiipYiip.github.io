---
title: Large-Scale Communication Network Analysis
subtitle: Reconstructing an organization's email network from 500,000+ messages with Apache Spark
tier: engineering
year: 2025
stat: "20% of employees accounted for 90%+ of all communication"
order: 4
repo: https://github.com/AppaYiipYiip
source_logo: /assets/images/enron-logo.svg
source_name: Enron email dataset
---

Processed a corpus of 500,000+ emails with Apache Spark to reconstruct an
organization's internal communication network and reveal its structure.

**What it does**

- Built the processing pipeline in Apache Spark to handle the full 500,000+
  message volume
- Reconstructed the communication network between employees from raw message
  metadata
- Surfaced a strong concentration of activity: 20% of employees were
  responsible for more than 90% of all exchanges
- Translated the network structure into visualizations aimed at non-technical
  stakeholders, not just an analytics audience

**Decisions worth naming**

- Used Spark rather than a single-machine approach because the message volume
  made in-memory processing impractical
- Led with the 20%/90% concentration stat instead of raw network diagrams,
  since that single number is what a non-technical stakeholder actually acts on
