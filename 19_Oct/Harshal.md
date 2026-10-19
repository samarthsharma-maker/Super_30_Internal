# Harshal: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** 32harshalmachhi@gmail.com  
**Repo:** [github.com/Harshuqt/Scaler_DevSecOps_and_SRE_Lab](https://github.com/Harshuqt/Scaler_DevSecOps_and_SRE_Lab)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** The only work is a Dockerfile that appears to be copied, and the copy happened in a visibly clumsy way.

## Placement read

| | |
|---|---|
| **Placement tier** | **Concern**: Negative signal on originality or ownership. Lower priority. |
| **Effect on placement chances** | Decrease |
| **AI-generation likelihood** | Low (confidence: Low) |
| **Where AI likely shows up** | Too little to judge |
| **Originality** | Flagged (matches Shishir) |
| **Stage reached** | Task 1: Dockerfile only |
| **CI status** | No workflows |
| **Started** | Fri 16 Oct, 14:03 IST |
| **Last commit** | Fri 16 Oct, 14:09 IST (2 commits within 6 minutes) |

**Recommended action:** Lower priority. Have a direct conversation about originality. Any future work should be judged on what they produce unaided.

### Signals that raise their chances
- None beyond a working non-root image.

### Signals that lower their chances
- Probable copied work.
- No further progress in three days.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Byte-identical file | `Dockerfile` | Identical to Shishir's, including the same EXPOSE 80 mistake. | Copying |
| Hybrid first version | `commit f3f4b44` | python:3.13-slim base with Alpine-only 'addgroup -S / adduser -S' flags, which would very likely fail on Debian. | Copying |
| Six-minute fix to match | `commit aba1d1d` | Switched to Alpine six minutes later, producing an exact match with Shishir's file. | Copying |
| Timing | `git log` | Shishir's version at 12:39 IST; Harshal's at 14:03 to 14:09 IST the same day. | Copying |

**Our read:** Not an AI case. The concern is peer copying.

## Originality

**Status:** Flagged (matches Shishir)

High-confidence copy of Shishir's Dockerfile. A six-line file can converge by chance, but an identical mistake plus a broken intermediate version is hard to explain otherwise.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Walk me through each line of your Dockerfile.
2. Why did your first version use slim with addgroup -S?
3. Why port 80?

## Timeline context

Started on Friday 16 Oct at 14:03 IST. Both commits landed within six minutes, with no activity since.

*Expectation calibration:* Had three days. Very little progress, so a check-in is warranted.

## Requirement-by-requirement status

0 done, 1 partial and 23 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟡 Partial | python:3.13-alpine, non-root. EXPOSE 80, but the app listens on 8080. No HEALTHCHECK. |
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
| Setup, architecture and reproduction steps | 🔴 Missing | README is still the original assignment brief. |

## Technical strengths
- Runs as a non-root user on a small Alpine base.

## Technical gaps to fix
- Change EXPOSE 80 to EXPOSE 8080 and add a HEALTHCHECK.
- Start the PR pipeline.
