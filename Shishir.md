# Shishir: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** shishirkrishna18@gmail.com  
**Repo:** [github.com/shishir-krishna-101/DevOps-SRE](https://github.com/shishir-krishna-101/DevOps-SRE)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Modest progress of their own. Their Dockerfile appears to have been copied by two others.

## Placement read

| | |
|---|---|
| **Placement tier** | **Early**: Too little work to judge. Neutral for now. |
| **Effect on placement chances** | Neutral |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | None evident |
| **Originality** | Source of copied file |
| **Stage reached** | Task 1: Dockerfile only |
| **CI status** | No workflows |
| **Started** | Thu 15 Oct, 21:29 IST |
| **Last commit** | Sat 17 Oct, 02:50 IST (5 commits and 1 merged PR) |

**Recommended action:** Neutral. No negative signal on originality for Shishir himself.

### Signals that raise their chances
- Thought about branch workflow early and scripted guardrails.

### Signals that lower their chances
- EXPOSE 80 while the app listens on 8080.
- No CI after several days.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Own evolution | `Dockerfile history` | Started on slim with useradd at 23:57 on 15 Oct, moved to Alpine at 12:39 on 16 Oct. | Against AI |
| Helper scripts | `scripts/` | Interactive bash with branch guards; plausible own work. | Neutral |

**Our read:** No meaningful AI signal.

## Originality

**Status:** Source of copied file

Shishir's final Dockerfile (12:39 IST on 16 Oct) reappears verbatim in Harshal's repo (14:03 to 14:09) and, minus one line, in Hardik's (13:55). Shishir is the earliest and the file evolved naturally in his history, so he looks like the source. Worth asking whether he shared it.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Did you share your Dockerfile with anyone?
2. Why EXPOSE 80?

## Timeline context

Started on Thursday 15 Oct at 21:29 IST. The last activity was early on Saturday 17 Oct.

*Expectation calibration:* Had several days. Early-stage progress, so a nudge is warranted.

## Requirement-by-requirement status

0 done, 2 partial and 22 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟡 Partial | python:3.13-alpine, non-root. EXPOSE 80, but the app listens on 8080. Evolved from slim to Alpine over two commits. |
| Branch protection (PR-only changes to main) | 🟡 Partial | Helper scripts refuse to push from main, and PR #1 was merged from a feature branch. Nothing is enforced on GitHub. |
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
| Setup, architecture and reproduction steps | 🔴 Missing | Not started. |

## Technical strengths
- Thought about the branch workflow early and scripted it.
- Iterated on the base image (slim to Alpine).

## Technical gaps to fix
- Change EXPOSE 80 to EXPOSE 8080 and add a HEALTHCHECK.
- Turn on branch protection in GitHub rather than relying on local scripts.
- Add the PR and release pipelines.
