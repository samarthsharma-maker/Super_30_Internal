# Deepak: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** deepakshivakumar07@gmail.com  
**Repo:** [github.com/Deepak-k-s/devops-project1](https://github.com/Deepak-k-s/devops-project1)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Only about a day of work, but the habits are senior: SHA-pinned actions, feature branches, a revert of an accidental main push.

## Placement read

| | |
|---|---|
| **Placement tier** | **Promising**: Real skill visible. Needs more progress or one quick check. |
| **Effect on placement chances** | Slight increase |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | None evident |
| **Originality** | Clear |
| **Stage reached** | Task 1 in progress |
| **CI status** | Failing. PR #1 fails on Flake8 |
| **Started** | Sun 18 Oct, 17:55 IST |
| **Last commit** | Sun 18 Oct, 23:23 IST (4 commits on two branches, 1 open PR) |

**Recommended action:** Neutral to positive. Re-check in a week; a strong candidate if progress continues at this quality.

### Signals that raise their chances
- Supply-chain awareness (actions pinned to commit SHAs) that nobody else showed.
- Correct PR workflow from the start.

### Signals that lower their chances
- Very early. Only a PR pipeline, failing on starter-file lint.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Human commit text | `git log` | 'created Dockerfile and checked the app funtionality' (typo), a revert, two parallel branches. | Against AI |
| SHA-pinned actions with version comments | `pr-checks.yml` | Common in AI output but also plain best practice. | Neutral |

**Our read:** No meaningful AI signal.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why pin actions to a SHA instead of a tag?
2. PR #1 fails on Flake8. What is the fix and where should it live?

## Timeline context

Started on Sunday 18 Oct at 17:55 IST. All work so far happened that evening, about a day before this review. Along with Nayan, the latest start in the cohort.

*Expectation calibration:* With only about one day elapsed, a solid Task 1 PR pipeline is reasonable progress. Expectations for Tasks 2 and 3 should be tempered.

## Requirement-by-requirement status

5 done, 2 partial and 17 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-slim, UID 10001, .dockerignore, env flags set. |
| Branch protection (PR-only changes to main) | 🟡 Partial | Work is on task1-docker-ci and task1-docker-pr with PR #1 open. An accidental push to main was reverted. No enforced rule visible. |
| PR pipeline: build the image | 🟢 Done | Builds the image in the PR pipeline. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Flake8 fails on the unmodified starter test file (E302). This is the only reason PR #1 is red. |
| PR pipeline: SAST (B104 ignored) | 🟢 Done | Bandit with -s B104. Passes. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | No secret scanning (optional in the brief). |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest passes. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy gating, with every action pinned to a full commit SHA. |
| Release pipeline: build and push to a registry | 🔴 Missing | Not started. |
| Release pipeline: auto-update manifest image tags | 🔴 Missing | Not started. |

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
| Setup, architecture and reproduction steps | 🔴 Missing | README is two lines. |

## Technical strengths
- Pinning actions to commit SHAs is the best supply-chain practice in the cohort.
- Correct branch-and-PR workflow from the start, and reverting a direct push to main shows awareness of the rule.

## Technical gaps to fix
- Fix the starter files' Flake8 errors (or add a .flake8 config) so PR #1 goes green, then merge it.
- Write the release pipeline: build on merge, push to GHCR or Docker Hub, update manifest tags.
- Add a short README describing the setup.
