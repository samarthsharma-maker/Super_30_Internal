# Tripurakant: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** tripurakant@gmail.com  
**Repo:** [github.com/tripura-kant/gitops-devsecops-pipeline](https://github.com/tripura-kant/gitops-devsecops-pipeline)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Earliest starter, stalled after two days, with a README that promises a full pipeline that doesn't exist.

## Placement read

| | |
|---|---|
| **Placement tier** | **Early**: Too little work to judge. Neutral for now. |
| **Effect on placement chances** | Slight decrease |
| **AI-generation likelihood** | Low (confidence: Low) |
| **Where AI likely shows up** | Possibly the README line |
| **Originality** | Clear |
| **Stage reached** | Task 1 in progress |
| **CI status** | No workflows |
| **Started** | Wed 14 Oct, 19:53 IST |
| **Last commit** | Thu 15 Oct, 22:45 IST (6 commits) |

**Recommended action:** Neutral to slightly negative on momentum. A check-in on blockers would be more useful than a judgement.

### Signals that raise their chances
- Wrote their own concise tests; Deployment uses httpGet probes.

### Signals that lower their chances
- Most time available of anyone (from Wednesday), least momentum since Thursday.
- add-ci branch has no CI in it.
- Memory limit set to 256Mi against an explicit 400Mi requirement.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Human slips | `repo root` | Misnamed .flake8.py and pytest.ini.py; committed .idea/. | Against AI |
| Tagline README | `README.md` | One sentence describing CI, ArgoCD, Prometheus and alerting, none of which exist. | Supports AI (weak) |

**Our read:** Code is human. The README line is likely generated and overclaims.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why 256Mi?
2. What stopped the CI branch?

## Timeline context

Started on Wednesday 14 Oct at 19:53 IST, the earliest in the cohort. The last activity was Thursday 15 Oct, so nothing has happened for four days.

*Expectation calibration:* Had the most time of anyone. Progress has stalled, so a check-in is worthwhile.

## Requirement-by-requirement status

1 done, 5 partial and 18 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-alpine, UID 10001, env flags set. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Not started. |
| PR pipeline: build the image | 🔴 Missing | Not started. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Lint and pytest config exist but are misnamed (.flake8.py, pytest.ini.py), so the tools ignore them. No workflow runs them. |
| PR pipeline: SAST (B104 ignored) | 🔴 Missing | Not started. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | Not started. |
| PR pipeline: unit tests (pytest) | 🟡 Partial | Wrote their own tests in tests/test_app.py (and dropped the provided ones). No CI runs them. |
| PR pipeline: image vulnerability scan | 🔴 Missing | Not started. |
| Release pipeline: build and push to a registry | 🔴 Missing | Not started. |
| Release pipeline: auto-update manifest image tags | 🔴 Missing | Not started. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🔴 Missing | Not started. |
| Three Deployments behind one shared Service | 🟡 Partial | One Deployment and no Service. |
| Requests set and memory limit of 400Mi | 🟡 Partial | Limit is 256Mi. The brief requires 400Mi. |
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
| Setup, architecture and reproduction steps | 🟡 Partial | README is a single line describing CI, ArgoCD and monitoring that don't exist yet. |

## Technical strengths
- Earliest start in the cohort.
- Wrote their own concise test suite, and the Deployment uses httpGet probes on /healthcheck.

## Technical gaps to fix
- Rename .flake8.py to .flake8 and pytest.ini.py to pytest.ini.
- Add the PR and release workflows. The add-ci branch is identical to main, so CI was never added.
- Set the memory limit to 400Mi, then add two more Deployments and a Service.
- Remove the .idea/ folder and add it to .gitignore.
- Update the README to describe what exists today.
