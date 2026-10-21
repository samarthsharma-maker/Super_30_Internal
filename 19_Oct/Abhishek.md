# Abhishek: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** 1ac23456789@gmail.com  
**Repo:** [github.com/abhishekchandra2522k/devsecops-sre-project](https://github.com/abhishekchandra2522k/devsecops-sre-project)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Only learner who codified branch protection (GitHub rulesets via API), a genuinely senior instinct. Stalled after that.

## Placement read

| | |
|---|---|
| **Placement tier** | **Promising**: Real skill visible. Needs more progress or one quick check. |
| **Effect on placement chances** | Slight increase |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | None evident |
| **Originality** | Clear |
| **Stage reached** | Task 1 in progress |
| **CI status** | Ruleset sync workflow only |
| **Started** | Thu 15 Oct, 12:19 IST |
| **Last commit** | Thu 15 Oct, 15:56 IST (7 commits) |

**Recommended action:** Positive signal on depth of thinking. Nudge to finish Task 1.

### Signals that raise their chances
- Policy-as-code thinking for repo governance.
- Worked through GitHub token scopes, which most juniors avoid.

### Signals that lower their chances
- No PR or release pipeline. Empty K8s/job.yaml. Nothing since Thursday.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Iterating on real permission errors | `git log` | Token permission commits, removing and re-adding workflow_dispatch, 'testing workflow'. | Against AI |
| Informal comments | `Dockerfile` | 'uncomment in case new dependencies are coming'. | Against AI |

**Our read:** No meaningful AI signal.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why a ruleset via API rather than clicking it in settings?
2. What permissions did the token need and why?

## Timeline context

Started on Thursday 15 Oct at 12:19 IST and did all the work that afternoon, mostly iterating on the ruleset workflow. No activity since.

*Expectation calibration:* Had most of the week. Progress has stalled after a strong start, so a check-in is worthwhile.

## Requirement-by-requirement status

2 done, 0 partial and 22 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.13-slim, UID 10001, with a commented placeholder for future dependencies. |
| Branch protection (PR-only changes to main) | 🟢 Done | Ruleset JSON applied through the GitHub API: PR required, 1 approval, stale reviews dismissed, no force-push or deletion. We could not confirm it is active. |
| PR pipeline: build the image | 🔴 Missing | Not started. |
| PR pipeline: lint (Flake8) | 🔴 Missing | Not started. |
| PR pipeline: SAST (B104 ignored) | 🔴 Missing | Not started. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | Not started. |
| PR pipeline: unit tests (pytest) | 🔴 Missing | Not started. |
| PR pipeline: image vulnerability scan | 🔴 Missing | Not started. |
| Release pipeline: build and push to a registry | 🔴 Missing | Not started. |
| Release pipeline: auto-update manifest image tags | 🔴 Missing | Not started. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🔴 Missing | Kind install script only. K8s/job.yaml is empty. |
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
- Branch protection as code is a mature approach, and nobody else in the cohort did it.
- Worked through the token-permission issues needed to manage rulesets.

## Technical gaps to fix
- Add the PR pipeline (Flake8, Bandit -s B104, pytest, Trivy) and the release pipeline.
- Add a HEALTHCHECK to the Dockerfile.
- Remove or fill the empty K8s/job.yaml.
