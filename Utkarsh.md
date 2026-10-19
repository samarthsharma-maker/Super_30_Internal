# Utkarsh: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** utkarsh.popli26@gmail.com  
**Repo:** [github.com/utkarshpopli26/DevOps-SRE](https://github.com/utkarshpopli26/DevOps-SRE)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Clean-looking Tasks 1 and 2 in a single drop, with docs that state things which are not true about the repo.

## Placement read

| | |
|---|---|
| **Placement tier** | **Hold**: Do not use this submission as a positive signal until verified live. |
| **Effect on placement chances** | Decrease until verified |
| **AI-generation likelihood** | High (confidence: Medium-High) |
| **Where AI likely shows up** | Tasks 1 and 2, code and docs |
| **Originality** | Clear |
| **Stage reached** | Tasks 1 and 2, Task 3 not started |
| **CI status** | Release passed. PR pipeline has never run |
| **Started** | Sat 17 Oct, 18:20 IST |
| **Last commit** | Sat 17 Oct, 18:26 IST (bot tag update) (1 commit, plus 1 automated commit) |

**Recommended action:** Hold. Same walkthrough format as for high-AI submissions. If they can explain and fix the Bandit and tag issues on the spot, move to Promising and treat the docs as a coaching point.

### Signals that raise their chances
- All Task 2 objects present and wired into the containers properly.
- httpGet probes on /healthcheck, which is correct.

### Signals that lower their chances
- PR pipeline cannot pass as written and was never tried.
- README asserts controls that are not in place.
- Weekend start, so limited time, but the time was not spent validating.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Single 814-line commit | `commit a6d8fe2` | Dockerfile, both workflows, all Kubernetes manifests, docs and a Python helper in one commit titled 'Containerize, CICD, Kubernetes setup'. | Supports AI |
| False claim about controls | `readme.md` | 'Direct pushes to main are blocked by branch protection rules.' The commit itself was a direct push to main. | Supports AI |
| Claims tooling that isn't there | `docs/architecture.md` | 'Prometheus and Grafana are installed locally through Helm.' No Helm values, scripts or manifests exist. | Supports AI |
| A never-ran mistake | `pr-ci.yml` | bandit -x B104 (exclude path) instead of -s B104 (skip test). Fails on first run; never fixed because the pipeline never ran. | Supports AI |
| Generic polish | `readme.md` | 'intentionally structured to remain fully local-first and open-source friendly'. | Supports AI |
| Release ran | `Actions` | The release pipeline ran green and the bot committed tags, so something was pushed and executed. | Against AI (weak) |

**Our read:** Very likely generated in one session and committed without running the PR path. The false statements in the README are the bigger issue: they describe a state that never existed, which in a work setting is a reliability-of-reporting problem.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. What is the difference between bandit -x and bandit -s?
2. Your README says pushes to main are blocked. Show me the rule.
3. Run the tag-update script a second time. What changes?
4. Your NetworkPolicy allows ingress only from app pods. Can Prometheus scrape them?

## Timeline context

Started on Saturday 17 Oct at 18:20 IST and pushed Tasks 1 and 2 in a single commit (16 files, 814 lines). The release bot updated the tags six minutes later. This is a weekend start with about two days of elapsed time.

*Expectation calibration:* Given the weekend start, Task 3 not being started is understandable. The focus should be on getting Tasks 1 and 2 actually working.

## Requirement-by-requirement status

12 done, 7 partial and 5 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12.4-slim, system user, HEALTHCHECK, .dockerignore. |
| Branch protection (PR-only changes to main) | 🟡 Partial | branch-protection.md lists the right settings, but the work was pushed straight to main, so they aren't enforced. |
| PR pipeline: build the image | 🟡 Partial | Image build in the container-security job. Has never run because no PR was opened. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Flake8 on the unmodified app.py fails (E305 and trailing whitespace). |
| PR pipeline: SAST (B104 ignored) | 🟡 Partial | bandit -x B104 excludes a path called B104, not the test. B104 is still reported and the step fails. It should be -s B104. |
| PR pipeline: secret scanning (optional) | 🟢 Done | TruffleHog filesystem scan with --fail. |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest, 6 of 6 pass. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy on HIGH and CRITICAL with exit-code 1. |
| Release pipeline: build and push to a registry | 🟢 Done | Pushes v1, v2, v3, the SHA and latest to GHCR. The release run passed. |
| Release pipeline: auto-update manifest image tags | 🟡 Partial | The script replaces __IMAGE_TAG__ placeholders, so it only works once. After that the tags stay v1/v2/v3 and nothing changes. All three tags also point at the same image. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🟡 Partial | Application with automated prune and selfHeal. No evidence it was applied. |
| Three Deployments behind one shared Service | 🟢 Done | memory-app-v1, v2 and v3 behind memory-app-service. |
| Requests set and memory limit of 400Mi | 🟢 Done | 128Mi request, 400Mi limit, httpGet probes on /healthcheck. |
| Namespaces, ConfigMaps and Secrets | 🟢 Done | Namespaces for app, monitoring and argocd. ConfigMap and Secret wired in as env vars. |
| initContainers | 🟢 Done | busybox init container writing a READY file into a shared emptyDir. |
| RBAC (ServiceAccount, Role, RoleBinding) | 🟢 Done | ServiceAccount, Role and RoleBinding. |
| NetworkPolicies | 🟡 Partial | Ingress is allowed only from the app's own pods. That blocks Prometheus and any client in another namespace. |
| ResourceQuotas | 🟢 Done | ResourceQuota. |

**Task 3: Observability and alerting**

| Requirement | Status | Finding |
|---|---|---|
| Prometheus and Grafana via Helm | 🔴 Missing | Described in docs only. No values files or install steps. |
| Dashboard: node and per-pod CPU/memory | 🔴 Missing | Not started. |
| Log aggregation (Loki, EFK or similar) | 🔴 Missing | Docs say Loki 'can also be installed'. |
| Grafana alerts: health check and OOMKilled | 🔴 Missing | Not started. |
| Alert routing to Slack or email (bonus) | 🔴 Missing | Not started. |

**Documentation**

| Requirement | Status | Finding |
|---|---|---|
| Setup, architecture and reproduction steps | 🟢 Done | README plus architecture and local Kubernetes setup guides. |

## Technical strengths
- Complete set of Task 2 objects, with config actually wired into the containers rather than just created.
- Health probes use httpGet on /healthcheck, which is what the alerting in Task 3 will rely on.
- Release pipeline runs green and pushes to GHCR.

## Technical gaps to fix
- Change bandit -x B104 to bandit -s B104, and fix the Flake8 errors (reformat app.py or add a .flake8). Then open a PR to prove the pipeline passes.
- Rework the tag update to write the commit SHA into each Deployment every run, instead of one-time placeholders.
- Relax the NetworkPolicy ingress so the Service's clients and the monitoring namespace can reach port 8080.
- Actually enable branch protection. The README currently says direct pushes are blocked, and they are not.
- Start Task 3: kube-prometheus-stack, a dashboard, Loki and the two Grafana alerts.
