# Amit: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** amit199222@gmail.com  
**Repo:** [github.com/amit199222/DevOps-SRE](https://github.com/amit199222/DevOps-SRE)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** The clearest evidence of real engineering per hour in the cohort. Most of Tasks 1 and 2 in one afternoon, with visible debugging.

## Placement read

| | |
|---|---|
| **Placement tier** | **Strong**: Clear positive signal. Recommend for placement conversations now. |
| **Effect on placement chances** | Increase |
| **AI-generation likelihood** | Low (confidence: Medium) |
| **Where AI likely shows up** | Possibly snippets |
| **Originality** | Shared code (source) |
| **Stage reached** | Tasks 1 and 2, Task 3 started |
| **CI status** | PR checks green after fixes. Release run failed |
| **Started** | Sat 17 Oct, 12:15 IST |
| **Last commit** | Sat 17 Oct, 15:39 IST (10 commits and 1 merged PR in about 3.5 hours) |

**Recommended action:** Put forward. Strong process signal. A short follow-up to see Task 3 would make this an easy recommendation.

### Signals that raise their chances
- Release triggers on a merged PR and re-scans before pushing, the strictest reading of the brief.
- Meaningful hardened initContainer (validates mounted config), deny-by-default NetworkPolicy.
- Debugged Trivy, non-root and quota issues in real time.
- About 3.5 hours of work on a Saturday produced most of two tasks.

### Signals that lower their chances
- The GitOps tag update targets the wrong image line (the initContainer).
- ArgoCD points at a feature branch.
- Committed __pycache__ and a junk file ('tatus --short'), which is sloppy hygiene.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Debugging trail | `git log` | 'fix trivy' three times, 'k8s non root issue fix', 'increase memory quota'. Each matches a real failure mode. | Against AI |
| Human leftovers | `Dockerfile` | Commented-out earlier attempts (#COPY --chown=appuser:appgroup, #USER appuser). | Against AI |
| Followed the brief literally | `release.yml` | Release on pull_request closed + merged, exactly the trigger the brief describes. | Against AI |
| Clean inline Python | `release.yml` | Tag-update heredoc is tidy and could be AI-assisted. | Supports AI (weak) |

**Our read:** Hands-on work. At most an assistant helped with snippets, which were then run and fixed against real failures.

## Originality

**Status:** Shared code (source)

Amit's release.yml tag-update block and the 'memory-leak-service' image name were reproduced almost verbatim by Nikhil later the same day (Amit at 12:15 IST, Nikhil at 20:44 IST). Amit appears to be the source. Worth a light question about whether he shared code, but there is no negative signal against Amit himself.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Your tag-update replaced the initContainer image. Why, and how would you target the app container?
2. Why trigger release on PR closed rather than push to main?
3. What does your initContainer guarantee before the app starts?
4. Did you share your workflow with anyone in the cohort?

## Timeline context

Started on Saturday 17 Oct at 12:15 IST and worked continuously until 15:39 the same day, finishing Task 1, most of Task 2 and a Helm values file in about 3.5 hours. This is a weekend start.

*Expectation calibration:* For roughly one afternoon of work this is strong progress. Task 3 should be judged with the weekend start in mind.

## Requirement-by-requirement status

13 done, 6 partial and 5 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-slim, UID 65532, env flags set. No HEALTHCHECK. |
| Branch protection (PR-only changes to main) | 🟡 Partial | Work went through PR #1 from feature/my-work. No enforced rule is visible, and the later 'helm' commit went straight to main. |
| PR pipeline: build the image | 🟢 Done | Builds the image with --pull in the PR pipeline. |
| PR pipeline: lint (Flake8) | 🟢 Done | .flake8 ignores the starter's whitespace codes. Passes. |
| PR pipeline: SAST (B104 ignored) | 🟢 Done | Bandit with -s B104 -ll. |
| PR pipeline: secret scanning (optional) | 🔴 Missing | No secret scanning (optional in the brief). |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest, 6 of 6 pass. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy gating. It took three 'fix trivy' commits to get it green, which shows real iteration. |
| Release pipeline: build and push to a registry | 🟡 Partial | Triggers on a merged PR exactly as the brief asks, re-scans, and pushes a SHA tag to GHCR. The one release run failed. |
| Release pipeline: auto-update manifest image tags | 🟡 Partial | Opens a GitOps PR, but the regex replaces the first image: line in the file. That is the initContainer, not the app, as the automation branch shows. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🟡 Partial | Application with auto-sync, but targetRevision is feature/my-work instead of main. |
| Three Deployments behind one shared Service | 🟢 Done | Three Deployments and one Service. |
| Requests set and memory limit of 400Mi | 🟢 Done | 128Mi request, 400Mi limit. |
| Namespaces, ConfigMaps and Secrets | 🟢 Done | Namespace devsecops, ConfigMap and Secret. |
| initContainers | 🟢 Done | The init container checks that the mounted config exists and isn't empty, and runs fully hardened. A real use, not a placeholder. |
| RBAC (ServiceAccount, Role, RoleBinding) | 🟢 Done | ServiceAccount, Role and RoleBinding, with automountServiceAccountToken: false. |
| NetworkPolicies | 🟢 Done | Ingress only from the same namespace on 8080, egress denied. |
| ResourceQuotas | 🟢 Done | ResourceQuota (limits raised to 4Gi after hitting the quota). |

**Task 3: Observability and alerting**

| Requirement | Status | Finding |
|---|---|---|
| Prometheus and Grafana via Helm | 🟡 Partial | Resource-tuned kube-prometheus-stack values file only. No install steps or evidence. |
| Dashboard: node and per-pod CPU/memory | 🔴 Missing | Not started. |
| Log aggregation (Loki, EFK or similar) | 🔴 Missing | Not started. |
| Grafana alerts: health check and OOMKilled | 🔴 Missing | Not started. |
| Alert routing to Slack or email (bonus) | 🔴 Missing | Not started. |

**Documentation**

| Requirement | Status | Finding |
|---|---|---|
| Setup, architecture and reproduction steps | 🟡 Partial | README is still the original assignment brief. |

## Technical strengths
- Release triggers on a merged PR and re-scans before pushing, which is the strictest reading of the brief.
- A meaningful, hardened initContainer and a deny-by-default NetworkPolicy.
- The history shows real debugging: Trivy fixes, a non-root fix for Kubernetes, a quota increase.

## Technical gaps to fix
- Update the tag-update step to target the app container by name (yq is easiest) and write a tag into all three Deployments.
- Point the ArgoCD Application at main.
- Add a HEALTHCHECK to the Dockerfile and a secret-scanning step to the PR pipeline.
- Remove committed artifacts: app/__pycache__, test/__pycache__ and the stray file named 'tatus --short'.
- Replace the README with your own setup and architecture notes.
- Install the monitoring stack, add a log stack, and build the dashboard and two Grafana alerts.
