# Project Plan – Mobile & Wearable Usage Data Pipeline ("Quantified-Self Analytics") – **Reviewed & Aligned**

## 1. Project Overview
Build an end-to-end, **fully-serverless & free-tier** data pipeline that captures Android Digital Wellbeing metrics and Samsung Galaxy wearable health data, stores them in Supabase Postgres, and surfaces insights through Grafana Cloud dashboards and Google Colab notebooks. The outcome is an automated platform that reveals how screen-time correlates with physical activity and sleep quality.

## 2. Scope
* **In scope (all free tiers)**:
  * Android background collector (Kotlin, WorkManager)
  * Wearable data sync script (Samsung Health REST API)
  * Cloudflare Worker ingress layer with HMAC request signing
  * Supabase Postgres (500 MB) as the single source of truth
  * dbt Core models & tests executed via GitHub Actions CI
  * Grafana Cloud dashboards (Postgres datasource)
  * Google Colab notebooks for analysis & reporting
  * Terraform IaC modules managed in a public GitHub repo
* **Out of scope**:
  * Paid infrastructure (Droplets/VMs, RDS, Snowflake, etc.)
  * Storage or egress beyond free-tier quotas
  * Proprietary BI tools that require licences (e.g., Metabase Cloud, Tableau)

## 3. SMART Objectives
| # | Objective | Metric | Target Date |
|---|-----------|--------|-------------|
| 1 | Capture ≥95 % of daily phone & wearable events | % events successfully ingested | End Week 4 |
| 2 | Publish interactive dashboard showing screen-time vs steps & sleep | Dashboard loads in <300 ms | End Week 5 |
| 3 | Produce correlation analysis notebook with p < 0.05 | r & p values documented | End Week 6 |
| 4 | Keep **monthly cost = 0 USD** (free tiers only) | Usage monitoring | Continuous |

## 4. Roles & Responsibilities
| Team Member | Role | Key Responsibilities |
|-------------|------|-----------------------|
| *You* | Sponsor & Lead Engineer | Architecture, infrastructure, code reviews, stakeholder updates |
| Mobile Dev (freelancer) | Android Engineer | Implement collectors, secure HTTPS client |
| Data Engineer (same as Lead) | Data Platform Engineer | Build ingestion Worker, dbt models & CI |
| Analyst | Data Scientist | Exploratory analysis, statistical notebooks |
| End User | Consumer | Use dashboards, give feedback |

## 5. Deliverables & Architecture
| ID | Deliverable | Description | Owner |
|----|-------------|-------------|-------|
| D1 | Android Collector APK | Background service that batches JSON usage events hourly and sends to Cloudflare Worker | Mobile Dev |
| D2 | Wearable Sync Script | GitHub Actions workflow that pulls steps, HR & sleep via Samsung Health API and posts to Worker | Mobile Dev |
| D3 | Cloudflare Ingestion Worker | Validates HMAC-signed POST and forwards rows to Supabase REST endpoint | Data Engineer |
| D4 | Supabase Postgres Schema | `raw_*` event tables, `stg_*` staging, `fct_*` marts with appropriate indexes & row-level retention | Data Engineer |
| D5 | dbt Repo & CI | Models, tests, docs; executed daily via GitHub Actions; Artefacts rendered to Supabase | Data Engineer |
| D6 | Grafana Cloud Dashboards | Trends, correlations, anomaly alerts (free notifications) | Analyst |
| D7 | Google Colab Notebook Report | Statistical correlation & personalised recommendations | Analyst |
| D8 | Terraform IaC | One-click deploy of Workers, Supabase projects, dashboards & secrets | Data Engineer |
| D9 | Project README & Blog Post | Architecture diagram, lessons learned, how-to replicate | Lead Engineer |

## 6. Schedule / Timeline
| Week | Key Tasks / Milestones |
|------|-----------------------|
| **1** | Kick-off, repo/CI skeleton, requirements finalised; D1 prototype (local JSON capture) |
| **2** | Implement D2 sync script; deploy Cloudflare Worker (stub) & secret management |
| **3** | End-to-end ingestion path (Android → Worker → Supabase); draft dbt staging models |
| **4** | Automate hourly collector; dbt marts & tests; set up Grafana Cloud datasource |
| **5** | Build dashboards; cost & quota monitors; internal user testing |
| **6** | Correlation notebook, blog post draft, final demo & retrospective |

## 7. Budget (Target = 0 USD / month)
| Service | Tier | Monthly Cost |
|---------|------|--------------|
| Cloudflare Workers | Free | **0.00** |
| Supabase Postgres (500 MB) | Free | **0.00** |
| Grafana Cloud | Free | **0.00** |
| GitHub Actions (public repo) | Free | **0.00** |
| Google Colab | Free | **0.00** |
| **Total** | | **0.00 USD** |

## 8. Risks & Mitigations
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Battery drain from collectors | Med | Med | Transmit only on Wi-Fi & charge, adaptive sampling |
| API quota limits (Samsung Health) | Low | Med | Incremental sync, caching, retry-with-backoff |
| Free-tier quota exhaustion (Supabase storage/rows) | Med | Med | Retention policy, down-sampling, alerts |
| Cloudflare Worker daily request cap (100 k) | Low | Low | Usage monitoring, exponential back-off |
| Privacy breach / PII exposure | Low | High | TLS, row-level security, key rotation, encrypted secrets |
| Data model drift | Med | Med | dbt tests, CI alerts, versioned API contracts |

## 9. Approval & Sign-off
| Name | Title | Signature | Date |
|------|-------|-----------|------|
| *Your Name* | Sponsor / Lead Engineer |  |  |
| Mobile Dev | Android Engineer |  |  |
| Analyst | Data Scientist |  |  |

---

*Reviewed & updated — YYYY-MM-DD; maintain as living document.* 

## 10. Week 1 – Day-wise Execution Plan
Refer to the standalone `week1_plan.md` for the detailed day-wise schedule. 