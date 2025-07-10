# Contributing to Mobile & Wearable Usage Pipeline

First off, thanks for taking the time to contribute! This project relies on community participation to grow and improve. The guidelines below will help streamline the contribution process and maintain a high–quality, consistent codebase.

---

## Table of Contents
1. Project Philosophy
2. Code of Conduct
3. Getting Started
   1. Prerequisites
   2. Repository Setup
4. Development Workflow
   1. Branch Naming
   2. Commit Messages (Conventional Commits)
   3. Pull Request Checklist
5. Code Style & Tooling
   1. Python (`ruff`)
   2. Kotlin / Android (`ktlint` & Android Lint)
   3. Terraform (`terraform fmt`)
   4. Pre-commit Hooks
6. Testing
7. Documentation
8. Security & Responsible Disclosure
9. Community & Support

---

## 1. Project Philosophy
We favour **clarity over cleverness**, **automation over manual steps**, and **free-tier, open-source tools**. Every change should be:

* **Fast** – Build & CI should complete in <5 min.
* **Portable** – Work on macOS, Linux, and GitHub Actions runners.
* **Zero-cost** – Avoid paid services unless strictly necessary.

## 2. Code of Conduct
All interactions in this repository are covered by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to abide by its terms.

## 3. Getting Started
### 3.1 Prerequisites
| Tool | Version | Purpose |
|------|---------|---------|
| [uv](https://github.com/astral-sh/uv) | >= 0.1.22 | Python virtual-env + package manager (blazing fast) |
| Python | 3.11+ | Core language for pipeline & dbt |
| [Ruff](https://github.com/astral-sh/ruff) | ≈ latest (installed via `uv`) | Formatter & linter |
| Kotlin | 1.9+ | Android collector app |
| JDK | 17 | Android build toolchain |
| [ktlint](https://github.com/pinterest/ktlint) | >= 1.0 | Kotlin code style |
| Terraform | 1.6+ | IaC modules |
| Node.js | 20 (optional) | Commit-linting & tooling |

> Tip: Use [asdf](https://asdf.dev/) or `brew` to manage multiple runtimes on macOS/Linux.

### 3.2 Repository Setup
Clone and initialise submodules (if any):
```bash
$ git clone https://github.com/<org>/mobile-wearable-usage-pipeline.git
$ cd mobile-wearable-usage-pipeline
```

Create a Python virtual environment and install core dependencies via **uv**:
```bash
$ uv venv     # creates .venv/ with Python matching your local interpreter
$ uv pip install -r requirements.txt -r requirements-dev.txt
```
Activate the venv (shell-dependent):
```bash
$ source .venv/bin/activate  # macOS/Linux
# OR
$ .venv\Scripts\activate    # Windows PowerShell
```

(Optional) Install pre-commit hooks:
```bash
$ pre-commit install
```

---

## 4. Development Workflow
### 4.1 Branch Naming
Follow the convention:
```
<type>/<short-kebab-case-description>
```
Where `<type>` ∈ { `feat`, `fix`, `chore`, `docs`, `refactor`, `perf`, `test`, `ci` }.
Examples:
```
feat/android-usage-capture
fix/terraform-provider-pin
```

### 4.2 Commit Messages – Conventional Commits
Use the [Conventional Commits](https://www.conventionalcommits.org/) standard. Basic format:
```
<type>(<scope>): <subject>

<body>

<footer>
```
* **type**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `ci`, `chore`.
* **scope** (optional): directory, feature, or ticket (e.g., `android`, `dbt`).
* **subject**: short imperative summary (≤ 72 chars).

Automated tools rely on these messages to generate changelogs and semantic version tags.

### 4.3 Pull Request Checklist
* ✅ Linked issue or clear description of intent.
* ✅ Descriptive title following Conventional Commit style (e.g., `feat(android): add foreground service`).
* ✅ Unit/integration tests updated or added.
* ✅ CI passes (Ruff, ktlint, terraform fmt, unit tests).
* ✅ Documentation updated (README, diagrams, dbt docs, etc.).
* ✅ At least one reviewer approved; NO self-merges unless trivial docs.

---

## 5. Code Style & Tooling
### 5.1 Python – Ruff
We use **ruff** for *both* formatting and linting. Key commands:
```bash
$ ruff check .            # static analysis
$ ruff format .           # auto-format
```
Ruff configuration lives in `pyproject.toml`.

### 5.2 Kotlin / Android – ktlint & Android Lint
Run from project root:
```bash
$ ./gradlew ktlintCheck   # style
$ ./gradlew lint          # code + XML resources
```

### 5.3 Terraform
```bash
$ terraform fmt -check -recursive
```

### 5.4 Pre-commit Hooks
A `.pre-commit-config.yaml` is provided covering Ruff, ktlint, Terraform, and commit-message linting. Install via:
```bash
$ pre-commit install
```
Hooks run automatically on `git commit`.

---

## 6. Testing
* **Python** – `pytest` with coverage ≥ 90 % for critical modules.
* **Android** – Local JVM tests (`testDebugUnitTest`) + Instrumentation tests (`connectedAndroidTest`).
* **Terraform** – `terraform validate` and `terratest` Go suites (optional).

Run all test suites locally before pushing:
```bash
$ pytest -q
$ ./gradlew testDebugUnitTest
```

## 7. Documentation
Update inline docstrings, markdown diagrams, and dbt docs as part of each change. Large features should add/update architecture diagrams in `docs/` (draw.io or Mermaid preferred).

## 8. Security & Responsible Disclosure
If you discover a vulnerability, please **DO NOT** post it publicly. Instead, use GitHub's "Report a security vulnerability" feature (under the repository **Security** tab) to start a private advisory with the maintainers.

## 9. Community & Support
For support or discussion, open a GitHub Discussion or create an issue labeled `question`.

Thank you for contributing! Together we can build an awesome, privacy-respecting quantified-self platform. 