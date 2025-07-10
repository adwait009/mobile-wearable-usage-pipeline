# Day-wise Activity Log – Mobile & Wearable Usage Data Pipeline

> This living document captures detailed actions, decisions, and artefacts for each project day. Reference alongside `Week1_Plan.md` and the main project plan.

---

## Day 1 — Project Kick-off & Repository Bootstrap  
_Target date: **Mon YYYY-MM-DD** (adjust once calendar is finalised)_

### 1  Kick-off Meeting
| Item | Details |
|------|---------|
| Participants | Lead Engineer (*you*), Mobile Dev, Analyst |
| Agenda | 1. Re-state project vision & success metrics  <br>2. Confirm roles & Week 1 deliverables  <br>3. Align on tooling (GitHub, Kotlin, dbt, Terraform)  <br>4. Discuss communication cadence (Slack channel + weekly sync) |
| Outcome | • All stakeholders aligned on scope.  <br>• Action items assigned (see below). |

### 2  GitHub Repository Creation
| Setting | Value |
|---------|-------|
| Proposed repo name | `mobile-wearable-usage-pipeline` |
| Visibility | **Public** (enables free GitHub Actions minutes) |
| Initial branch | `main` |
| Default license | **MIT License** (permissive, widely adopted) |
| .gitignore | **Custom combined** – start with `Android.gitignore` then append `Python`, `Terraform`, and `Global/JetBrains` sections (see github/gitignore repo) |

**To-do:**
1. Create repo under personal GitHub account/org.  
2. Add collaborators with write access.  
3. Enable Dependabot security updates.

### 3  Initial Repository Structure
```
/ (root)
├── android/               # Kotlin collector app
├── wearable_ingestion/         # GH-Actions script for Samsung Health
├── infrastructure/        # Terraform modules & env configs
├── dbt/                   # dbt project
├── notebooks/             # Colab & Jupyter analysis
└── docs/                  # Architecture diagrams & markdown docs
```

### 4  Bootstrap Artefacts
| File | Purpose |
|------|---------|
| `README.md` | Overview, architecture diagram link, quick-start, badges |
| `LICENSE` | MIT text |
| `CODE_OF_CONDUCT.md` | Contributor covenant v2.1 |
| `CONTRIBUTING.md` | PR process, branch naming, commit convention (Conventional Commits), code style pointers |
| `.github/workflows/ci.yml` | Initial build & lint (Android lint, ktlint; Python black; Terraform fmt) |
| `.editorconfig` | Consistent whitespace/EOF rules |

### 5  Project Board Setup
Columns: **Backlog → In Progress → Review → Done**  
Labels: `area:android`, `area:data`, `infra`, `good first issue`, `documentation`, `bug`, `enhancement`.

### 6  Action Items & Owners
| Action | Owner | Due |
|--------|-------|-----|
| Create GitHub repo & push scaffold | Lead Engineer | EOD Day 1 |
| Draft README + LICENSE | Lead Engineer | EOD Day 1 |
| Prepare kickoff meeting notes in `/docs/meetings/` | Lead Engineer | During meeting |
| Set up project board & labels | Lead Engineer | EOD Day 1 |
| Draft CONTRIBUTING & CODE_OF_CONDUCT | Lead Engineer | Day 2 AM |
| Install ktlint pre-commit hook in android/ | Mobile Dev | Day 2 |

### 7  Completion Criteria
- Repository accessible at `https://github.com/<org>/mobile-wearable-usage-pipeline` with MIT license.  
- README displays project summary & shield badges.  
- Project board visible with at least 5 seeded issues.  
- Meeting notes committed.

---

*(Update this entry with actual dates, links, and status once tasks are completed.)* 