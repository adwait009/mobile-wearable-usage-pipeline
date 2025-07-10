# Week 1 – Day-wise Execution Plan
> Companion file to `MobileUsagePipeline_ProjectPlan_Reviewed.md` (Section 10). Keep this in sync with the main plan.

| Day | Focus & Key Outcomes | Detailed Tasks | Owner(s) |
|-----|----------------------|----------------|----------|
| **Monday (Day 1)** | Project Kick-off & Repo Bootstrap | • 30-min kickoff call: confirm scope, roles, success metrics  <br>• Create public GitHub repo, add README + license  <br>• Set up project board and labels for backlog tracking  <br>• Draft CONTRIBUTING guidelines & code-style doc | Lead Engineer |
| **Tuesday (Day 2)** | Android Collector Scaffold & CI Skeleton | • Scaffold Kotlin project with UsageStats + WorkManager permissions  <br>• Implement basic foreground service capturing package usage  <br>• Commit initial code; configure GitHub Actions workflow (lint, build) | Mobile Dev, Lead Engineer |
| **Wednesday (Day 3)** | Prototype Data Capture & Schema Definition | • Complete JSON serialisation & local write of usage events  <br>• Capture 4-hr sample, inspect battery impact  <br>• Draft event schema (`raw_phone_usage`) markdown  <br>• Open design discussion issue for data model feedback | Mobile Dev, Data/Lead Engineer |
| **Thursday (Day 4)** | Validation & Requirements Freeze | • Review sample data; refine schema fields (e.g., `app_category`)  <br>• Document retention & sampling policy  <br>• Finalise functional/non-functional requirements doc  <br>• Prepare Cloudflare Worker dev environment (stub endpoint) | Lead Engineer, Data Engineer |
| **Friday (Day 5)** | Prototype Demo & Next-Week Planning | • Demo D1 prototype to team; gather feedback  <br>• Update project board with Week 2 tasks and dependencies  <br>• Risk log update; confirm no new blockers  <br>• End-of-week summary sent to stakeholders | Lead Engineer, All |

> Dates: Align Day 1 with the first working day of Week 1 (e.g., Mon YYYY-MM-DD). Adjust if local holidays apply. 