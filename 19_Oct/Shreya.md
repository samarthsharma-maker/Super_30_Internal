# Shreya: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** khareshreya1302@gmail.com  
**Repo:** [github.com/shreya1302/DevOps-SRE](https://github.com/shreya1302/DevOps-SRE)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Small but correct start: a green PR pipeline with a well-scoped SAST exception. Then stopped.

## Placement read

| | |
|---|---|
| **Placement tier** | **Early**: Too little work to judge. Neutral for now. |
| **Effect on placement chances** | Neutral |
| **AI-generation likelihood** | Low (confidence: Low) |
| **Where AI likely shows up** | Too little to judge |
| **Originality** | Clear |
| **Stage reached** | Task 1 in progress |
| **CI status** | Green. PR #1 passes |
| **Started** | Fri 16 Oct, 17:08 IST |
| **Last commit** | Fri 16 Oct, 17:25 IST (1 commit and 1 merged PR) |

**Recommended action:** Neutral. Needs a nudge; re-assess after more work.

### Signals that raise their chances
- Understood how to scope a SAST exception instead of disabling the check.

### Signals that lower their chances
- No image build or scan, no release pipeline, no activity since Friday.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Inline nosec | `app/app.py` | # nosec B104 on the bind line, a precise way to handle the finding. | Against AI (weak) |
| Small volume | `repo` | One commit and a merge. Not enough to judge either way. | Neutral |

**Our read:** Not enough work to assess AI use.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why # nosec B104 inline rather than -s B104?
2. What would you add to make this pipeline match the brief?

## Timeline context

Started on Friday 16 Oct at 17:08 IST. PR #1 was merged 17 minutes later, and there has been no activity since.

*Expectation calibration:* Had three days. Progress is light for that window, so a nudge to keep going is warranted.

## Requirement-by-requirement status

4 done, 1 partial and 19 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-slim, system user, .dockerignore, env flags set. |
| Branch protection (PR-only changes to main) | 🟡 Partial | Work merged through PR #1. No enforced rule visible. |
| PR pipeline: build the image | 🔴 Missing | The PR pipeline doesn't build the image. |
| PR pipeline: lint (Flake8) | 🟢 Done | app.py reformatted. Flake8 passes. |
| PR pipeline: SAST (B104 ignored) | 🟢 Done | Bandit, with # nosec B104 on the bind line. A clean way to scope the exception. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | No secret scanning (optional in the brief). |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest passes. |
| PR pipeline: image vulnerability scan | 🔴 Missing | No image scan. |
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
- Handled the 0.0.0.0 finding with an inline nosec rather than disabling the check globally.
- Used a feature branch and a PR from the start.

## Technical gaps to fix
- Add a docker build step and a Trivy scan (exit-code 1) to the PR pipeline.
- Add a release workflow that pushes the image on merge to main and updates manifest tags.
- Turn on branch protection so the checks are required.
