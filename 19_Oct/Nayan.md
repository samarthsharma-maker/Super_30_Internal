# Nayan: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** nayanjyotikalita170@gmail.com  
**Repo:** [github.com/NayanJyotiKalita/DevSecOps-SRE-Project](https://github.com/NayanJyotiKalita/DevSecOps-SRE-Project)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Latest starter, but did the one thing they did properly and proved it with real terminal output.

## Placement read

| | |
|---|---|
| **Placement tier** | **Promising**: Real skill visible. Needs more progress or one quick check. |
| **Effect on placement chances** | Neutral to increase |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | README wording |
| **Originality** | Clear |
| **Stage reached** | Task 1: Dockerfile done |
| **CI status** | No workflows |
| **Started** | Sun 18 Oct, 23:13 IST |
| **Last commit** | Mon 19 Oct, 00:37 IST (6 commits) |

**Recommended action:** Neutral to positive. Re-check in a week.

### Signals that raise their chances
- Verified the container under a read-only root filesystem without being asked.

### Signals that lower their chances
- Only the Dockerfile so far (started Sunday night).

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Stock security phrasing | `README.md, Dockerfile` | 'hardened single-stage Alpine', 'living-off-the-land attacks', 'dramatically reducing pull times'. | Supports AI (writing) |
| Real terminal output | `README.md` | Build log with image hash, docker ps with container ID, curl to /healthcheck. | Against AI |
| Read-only run | `README.md` | docker run --read-only --tmpfs /tmp, a deliberate security test. | Against AI |

**Our read:** AI-polished writing over genuine hands-on work.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why fixed UID/GID 10001?
2. What breaks if the root filesystem is read-only?

## Timeline context

Started on Sunday 18 Oct at 23:13 IST. The last commit was 00:37 on Monday 19 Oct, less than a day before this review.

*Expectation calibration:* The latest start in the cohort. A solid Dockerfile is a reasonable outcome for that window.

## Requirement-by-requirement status

1 done, 1 partial and 22 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-alpine, fixed UID/GID 10001, COPY --chown, .dockerignore. Tested with --read-only and a tmpfs. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Not started. |
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
| Setup, architecture and reproduction steps | 🟡 Partial | Detailed Dockerfile write-up with real build output, docker ps and a healthcheck curl. |

## Technical strengths
- Tested the container with a read-only root filesystem, which shows security thinking beyond the brief.
- Pasted real terminal output as proof of the build and the health check.

## Technical gaps to fix
- Add a HEALTHCHECK to the Dockerfile.
- Move on to the PR pipeline: Flake8, Bandit (-s B104), pytest and Trivy.
