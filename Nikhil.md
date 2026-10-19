# Nikhil: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** nikhilmourya36@gmail.com  
**Repo:** [github.com/nikhilmourya36/Devops-memory-leak-microservice-challenge](https://github.com/nikhilmourya36/Devops-memory-leak-microservice-challenge)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Pipelines appear to be copied from a peer or a shared prompt, adapted with a bug, and never run successfully.

## Placement read

| | |
|---|---|
| **Placement tier** | **Concern**: Negative signal on originality or ownership. Lower priority. |
| **Effect on placement chances** | Decrease |
| **AI-generation likelihood** | Medium (confidence: Medium) |
| **Where AI likely shows up** | Pipelines |
| **Originality** | Flagged (matches Amit) |
| **Stage reached** | Task 1 in progress, Task 2 started |
| **CI status** | Failing. Release run failed |
| **Started** | Sat 17 Oct, 15:27 IST |
| **Last commit** | Sat 17 Oct, 20:44 IST (2 commits) |

**Recommended action:** Lower priority for now. Have a direct, non-accusatory conversation about the source of the pipeline code. Re-assess on what they build next, unaided.

### Signals that raise their chances
- The shape of both pipelines is right.

### Signals that lower their chances
- Probable copied work, introduced bugs, no successful run.
- One Deployment with no resource limits, which misses the central point of Task 2.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Near-verbatim match to Amit | `release.yml` | The inline Python tag-update block is identical apart from the SystemExit message. Amit committed his at 12:15 IST; Nikhil's landed at 20:44 IST the same day. | Copying |
| Same unusual image name | `pr-validation.yml` | Both use 'memory-leak-service:pr', which is not this learner's repo name. | Copying |
| Adaptation bug | `release.yml` | IMAGE=...:v1:${sha} is an invalid reference, the kind of error made when editing pasted code without running it. | Supports copy/AI |
| Never ran locally | `app/Dockerfile` | Workflows build from root while the Dockerfile is in app/; the first docker build would have failed. | Supports copy/AI |
| Human commit text | `git log` | 'adding k8s and worlflow pipline'. | Against AI |

**Our read:** The structure and Python block match Amit's too closely for coincidence. Either code was shared, or both used the same AI prompt and Nikhil didn't validate the result. Both readings point to low hands-on ownership.

## Originality

**Status:** Flagged (matches Amit)

Flagged against Amit (DevOps-SRE). Amit's commits are earlier. Recommend asking Nikhil directly where the workflow came from.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Where did the Python tag-update block come from?
2. Why does your image reference end in ':v1:<sha>'?
3. Your Dockerfile is in app/. What does docker build . do from the repo root?

## Timeline context

Started on Saturday 17 Oct at 15:27 IST, with the pipelines and Kubernetes manifest pushed at 20:44 the same day. This is a weekend start.

*Expectation calibration:* Given the weekend start, the scope is fine. The priority is making what exists actually run.

## Requirement-by-requirement status

1 done, 8 partial and 15 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟡 Partial | python:3.12-slim, non-root user. The file is in app/ but both workflows build from the repo root, so the build can't find it. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Commits went straight to main. |
| PR pipeline: build the image | 🟡 Partial | The build step exists but fails because there is no Dockerfile at the root. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Flake8 fails on the starter test file. |
| PR pipeline: SAST (B104 ignored) | 🟡 Partial | Bandit runs without -s B104 and fails on the 0.0.0.0 bind. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | No secret scanning (optional in the brief). |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest passes. |
| PR pipeline: image vulnerability scan | 🟡 Partial | Trivy gating is configured but never reached. |
| Release pipeline: build and push to a registry | 🟡 Partial | Pushes SHA and latest tags to Docker Hub. The only run failed. |
| Release pipeline: auto-update manifest image tags | 🟡 Partial | Writes '<user>/<repo>:v1:<sha>', which is not a valid image reference. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🔴 Missing | Not started. |
| Three Deployments behind one shared Service | 🟡 Partial | One Deployment and no Service. |
| Requests set and memory limit of 400Mi | 🔴 Missing | No resources block at all, so nothing limits the leak. |
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
- Both pipelines exist and follow the right shape: validate on PR, publish on main.

## Technical gaps to fix
- Move the Dockerfile to the repo root (and adjust COPY), or point the builds at app/.
- Add -s B104 to Bandit and fix the Flake8 errors.
- Fix the image reference to '<user>/<repo>:<sha>'.
- Add requests and a 400Mi limit, then the other two Deployments and a shared Service.
