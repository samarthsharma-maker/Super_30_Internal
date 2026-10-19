# Manoj: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** manojsambana443@gmail.com  
**Repo:** [github.com/manojsambana443/devops-sre-project](https://github.com/manojsambana443/devops-sre-project)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Small scope, but tested the core failure mode (OOMKilled at 400MiB) and documented honestly.

## Placement read

| | |
|---|---|
| **Placement tier** | **Early**: Too little work to judge. Neutral for now. |
| **Effect on placement chances** | Neutral, integrity positive |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | Maybe README structure |
| **Originality** | Clear |
| **Stage reached** | Task 1: Dockerfile done |
| **CI status** | No workflows |
| **Started** | Fri 16 Oct, 13:27 IST |
| **Last commit** | Fri 16 Oct, 13:47 IST (3 commits within 20 minutes) |

**Recommended action:** Neutral. Positive on integrity; needs momentum.

### Signals that raise their chances
- Verified OOMKilled=true under a Docker memory limit before touching Kubernetes.
- Honest status reporting.

### Signals that lower their chances
- Stopped after about 20 minutes on Friday.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Accurate progress README | `readme.md` | Separates done from pending; nothing overclaimed. | Against AI |
| Structured layout | `readme.md` | Neat headings could be AI-polished. | Neutral |

**Our read:** No meaningful AI signal. The honesty of the README is a positive signal in its own right.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. How did you confirm the OOM kill?
2. What is blocking the CI step?

## Timeline context

Started on Friday 16 Oct at 13:27 IST. All three commits landed within 20 minutes, with no activity since.

*Expectation calibration:* Had three days. Progress is early but correct, and a nudge to keep going is warranted.

## Requirement-by-requirement status

2 done, 1 partial and 21 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-slim, system user, env flags set. Verified OOMKilled=true under a 400 MiB limit. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Not started. |
| PR pipeline: build the image | 🔴 Missing | Not started. |
| PR pipeline: lint (Flake8) | 🔴 Missing | Not started. |
| PR pipeline: SAST (B104 ignored) | 🔴 Missing | Not started. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | Not started. |
| PR pipeline: unit tests (pytest) | 🟡 Partial | Ran the 6 tests locally (all pass). No CI yet. |
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
| Setup, architecture and reproduction steps | 🟢 Done | A progress README that separates done from pending. |

## Technical strengths
- Tested the core failure mode (OOMKilled at 400 MiB) before touching Kubernetes.
- The README makes no claims beyond what is in the repo.

## Technical gaps to fix
- Add a HEALTHCHECK and a .dockerignore.
- Build the PR pipeline next.
