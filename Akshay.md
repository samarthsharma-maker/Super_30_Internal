# Akshay: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** moreakshay.2013@gmail.com  
**Repo:** [github.com/akshay228437/DevOps-SRE](https://github.com/akshay228437/DevOps-SRE)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Did Task 1 the way a real team would: branches, PRs, green gates, and decisions backed by scan results.

## Placement read

| | |
|---|---|
| **Placement tier** | **Strong**: Clear positive signal. Recommend for placement conversations now. |
| **Effect on placement chances** | Increase |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | Docs possibly polished |
| **Originality** | Clear |
| **Stage reached** | Task 1 complete (core) |
| **CI status** | Green. PR checks and release both pass on real PRs |
| **Started** | Sat 17 Oct, 13:36 IST |
| **Last commit** | Sat 17 Oct, 19:00 IST (12 commits and 4 merged PRs in one afternoon) |

**Recommended action:** Put forward for CI/CD-leaning roles now. Check Kubernetes depth before any SRE-heavy placement.

### Signals that raise their chances
- Only learner with both pipelines green on real PRs.
- Picked CodeQL (security-extended) for SAST; scoped permissions, timeouts and concurrency on jobs.
- Stricter Trivy than most (does not ignore unfixed CVEs).

### Signals that lower their chances
- Nothing for Kubernetes or observability yet.
- Local git identity not set (akshay@example.com).

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| PR-driven history | `git log` | 4 PRs (#4 to #7), merge-back commits, a 'Mrge branch' typo, 'linting issue fixed'. | Against AI |
| Evidence-driven decision | `Docs/Task 1/Dockerize.md` | Moved to Alpine after Trivy flagged HIGH CVEs on Debian, and documented why. | Against AI |
| Polished docs | `Docs/Task 1/*.md` | Typographic apostrophes and tidy tables suggest some AI or editor polish. | Supports AI (weak) |

**Our read:** Hands-on. If AI was used, it was for wording, not for the engineering.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why CodeQL over Bandit here? What does each catch?
2. Trade-off of not using ignore-unfixed in Trivy?
3. How would you extend release.yml to update manifests for three Deployments?

## Timeline context

Started on Saturday 17 Oct at 13:36 IST and finished Task 1 by 19:00 the same day, across four PRs. This is a weekend start.

*Expectation calibration:* Task 1 complete in one afternoon is a good pace. Tasks 2 and 3 not being started is expected given the start date.

## Requirement-by-requirement status

7 done, 2 partial and 15 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-alpine, UID 10001. Switched from Debian after Trivy flagged HIGH CVEs, and documented why. No HEALTHCHECK. |
| Branch protection (PR-only changes to main) | 🟡 Partial | All work merged through PRs #4, #6 and #7, and the docs describe the protection settings. One README edit went straight to main through the web UI. |
| PR pipeline: build the image | 🟢 Done | Builds the image in the PR pipeline. |
| PR pipeline: lint (Flake8) | 🟢 Done | app.py tidied. Flake8 passes. |
| PR pipeline: SAST (B104 ignored) | 🟢 Done | CodeQL with the security-extended query suite. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | No secret scanning (optional in the brief). |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest passes. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy on HIGH and CRITICAL with exit-code 1. Stricter than most, because unfixed CVEs aren't ignored. |
| Release pipeline: build and push to a registry | 🟢 Done | On a merged PR, pushes a sha-<commit> image to GHCR. Both runs green. |
| Release pipeline: auto-update manifest image tags | 🔴 Missing | Not implemented yet, since there are no manifests. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🔴 Missing | Not started. |
| Three Deployments behind one shared Service | 🔴 Missing | Not started. |
| Requests set and memory limit of 400Mi | 🔴 Missing | Not started. |
| Namespaces, ConfigMaps and Secrets | 🔴 Missing | Not started. |
| initContainers | 🔴 Missing | Not started. |
| RBAC (ServiceAccount, Role, RoleBinding) | 🔴 Missing | Not started. |
| NetworkPolicies | 🔴 Missing | Not started. |
| ResourceQuotas | 🔴 Missing | Not started. |

**Task 3: Observability and alerting**

| Requirement | Status | Finding |
|---|---|---|
| Prometheus and Grafana via Helm | 🔴 Missing | Not started. |
| Dashboard: node and per-pod CPU/memory | 🔴 Missing | Not started. |
| Log aggregation (Loki, EFK or similar) | 🔴 Missing | Not started. |
| Grafana alerts: health check and OOMKilled | 🔴 Missing | Not started. |
| Alert routing to Slack or email (bonus) | 🔴 Missing | Not started. |

**Documentation**

| Requirement | Status | Finding |
|---|---|---|
| Setup, architecture and reproduction steps | 🟡 Partial | Task 1 docs (Dockerize.md, CICD.md) with design reasoning. |

## Technical strengths
- Only learner whose PR and release pipelines both run green on real PRs.
- CodeQL as SAST, scoped job permissions, concurrency control and timeouts on every job.
- Made a data-driven base-image decision from an actual Trivy result.

## Technical gaps to fix
- Add a HEALTHCHECK to the Dockerfile.
- Add the manifest tag-update step to the release workflow once Kubernetes manifests exist.
- Set your local git identity. Commits are authored as akshay@example.com.
