# Ahmed Bilal: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** ahmed.bilal7191@gmail.com  
**Repo:** [github.com/ahmedbilal-7191/devops-project](https://github.com/ahmedbilal-7191/devops-project)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Good pipeline design, never got it working, and the release file is empty.

## Placement read

| | |
|---|---|
| **Placement tier** | **Early**: Too little work to judge. Neutral for now. |
| **Effect on placement chances** | Neutral |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | None evident |
| **Originality** | Clear |
| **Stage reached** | Task 1 in progress |
| **CI status** | Failing. All 3 runs failed |
| **Started** | Thu 15 Oct, 11:14 IST |
| **Last commit** | Sat 17 Oct, 13:25 IST (3 commits) |

**Recommended action:** Neutral. Encourage follow-through; the design shows understanding.

### Signals that raise their chances
- All PR gates present, including the optional secret scan; sensible job ordering and draft skip.

### Signals that lower their chances
- Every CI run failed, and the failures weren't followed up.
- Pushed to main, no PR.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Own-words comments | `ci.yml` | 'This workflow will it will build an dtest the image...' Typos and pasted brief text. | Against AI |
| Empty cd.yml | `.github/workflows/cd.yml` | Trigger with no jobs, left failing on every push. | Neutral |

**Our read:** No meaningful AI signal.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Bandit fails on B310 in test/. Why, and what is the right fix?
2. What should cd.yml contain?

## Timeline context

Started on Thursday 15 Oct at 11:14 IST and added the Dockerfile that afternoon. The CI workflow followed on Saturday 17 Oct.

*Expectation calibration:* Had most of the week. Progress is modest, but the pipeline design is good and close to passing.

## Requirement-by-requirement status

4 done, 4 partial and 16 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.13-slim-bookworm, UID 10001, .dockerignore, env flags set. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Commits went straight to main. No PR. |
| PR pipeline: build the image | 🟡 Partial | Builds the image after the other jobs, but CI has failed on every run. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Flake8 fails on the starter test file (E302). |
| PR pipeline: SAST (B104 ignored) | 🟡 Partial | Bandit also scans test/ and fails on urlopen (B310). |
| PR pipeline: secret scanning (optional) | 🟢 Done | Gitleaks. |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest passes. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy gating. |
| Release pipeline: build and push to a registry | 🟡 Partial | cd.yml has a trigger but no jobs, so GitHub rejects it on every push. |
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
| Setup, architecture and reproduction steps | 🔴 Missing | README is still the original assignment brief. |

## Technical strengths
- All the requested PR gates are present, including the optional secret scan.
- Sensible job ordering: the image is only built after tests and scans pass, and draft PRs are skipped.

## Technical gaps to fix
- Limit Bandit to app/ (or skip B310 for tests), and fix or configure Flake8 for the starter files.
- Write the release jobs in cd.yml: build, push, update manifest tags.
- Work on a branch and open a PR so the pipeline runs where it is meant to.
