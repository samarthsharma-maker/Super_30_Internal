# Hardik: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** hardiksharmaofficial07@gmail.com  
**Repo:** [github.com/Hardik-sh-devops/DevOps-SRE-Scaler-lab](https://github.com/Hardik-sh-devops/DevOps-SRE-Scaler-lab)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** A Dockerfile that matches a peer's and an empty workflow file. Very little original output.

## Placement read

| | |
|---|---|
| **Placement tier** | **Concern**: Negative signal on originality or ownership. Lower priority. |
| **Effect on placement chances** | Decrease |
| **AI-generation likelihood** | Low (confidence: Low) |
| **Where AI likely shows up** | Too little to judge |
| **Originality** | Flagged (matches Shishir) |
| **Stage reached** | Task 1: Dockerfile only |
| **CI status** | None (workflow file is empty) |
| **Started** | Fri 16 Oct, 13:55 IST |
| **Last commit** | Sat 17 Oct, 15:28 IST (4 commits) |

**Recommended action:** Lower priority until there is original work to assess.

### Signals that raise their chances
- None yet beyond a working non-root image.

### Signals that lower their chances
- Probable copied file and almost no other output.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Near-identical file | `Dockerfile` | Same as Shishir's Alpine version, including the appgroup and appuser names, minus the EXPOSE line. | Copying |
| Timing | `git log` | Hardik 13:55 IST on 16 Oct, 76 minutes after Shishir's 12:39 version. | Copying |
| Empty workflow | `pr-checks.yaml` | A one-line empty file after creating and deleting .github. | Neutral |

**Our read:** Not an AI case. Low output overall.

## Originality

**Status:** Flagged (matches Shishir)

Medium-confidence copy of Shishir's Dockerfile. The match is exact, but a six-line Alpine Dockerfile is a common pattern, so it is less conclusive than Harshal's case.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Walk me through your Dockerfile.
2. What should go in pr-checks.yaml?

## Timeline context

Started on Friday 16 Oct at 13:55 IST. The Saturday 17 Oct commits created and deleted .github and then added an empty workflow file.

*Expectation calibration:* Had three days. Very little progress, so a check-in is warranted.

## Requirement-by-requirement status

0 done, 1 partial and 23 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟡 Partial | python:3.13-alpine, non-root. No EXPOSE and no HEALTHCHECK. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Not started. |
| PR pipeline: build the image | 🔴 Missing | .github/workflows/pr-checks.yaml exists but is empty (one blank line). |
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
- Runs as a non-root user on a small Alpine base.

## Technical gaps to fix
- Fill in pr-checks.yaml: Flake8, Bandit (-s B104), pytest, docker build and Trivy.
- Add EXPOSE 8080 and a HEALTHCHECK.
