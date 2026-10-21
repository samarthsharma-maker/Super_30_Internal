# Vijay Kumar: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** vijaykumarm20@gmail.com  
**Repo:** [github.com/vijaykumarcm1991/devops-sre-p1](https://github.com/vijaykumarcm1991/devops-sre-p1)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Most complete repo on paper, almost no evidence a human built or ran it. Treat as unverified.

## Placement read

| | |
|---|---|
| **Placement tier** | **Hold**: Do not use this submission as a positive signal until verified live. |
| **Effect on placement chances** | Decrease until verified |
| **AI-generation likelihood** | High (confidence: High) |
| **Where AI likely shows up** | Entire submission, code and docs |
| **Originality** | Clear |
| **Stage reached** | All three tasks attempted (unverified) |
| **CI status** | Release passed on its one run. PR pipeline has never run |
| **Started** | Thu 15 Oct, 12:05 IST |
| **Last commit** | Thu 15 Oct, 13:25 IST (2 commits within 80 minutes) |

**Recommended action:** Do not use this submission as a positive placement signal yet. Book a 20-minute live walkthrough on their own machine. Pass: move to Promising or Strong. Can't run or explain it: mark as AI-generated and lower priority.

### Signals that raise their chances
- If they can explain and run it live, the breadth is impressive.
- Started early (Thursday).

### Signals that lower their chances
- Zero process evidence: no debugging, no PRs, no screenshots.
- Two 'looks right, doesn't work' gaps (non-gating Trivy, static tags) that a hands-on engineer would have hit.
- No activity since the single afternoon on 15 Oct.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Single drop of the whole project | `commit 932d10f` | 27 files, 1,604 lines, all three tasks, one commit at 12:05 IST on 15 Oct. No fix-up commits at all. | Supports AI |
| Docs 80 minutes later | `commit 1735560` | 525 lines across four guides, with 'working hyperlinks' in the commit message. | Supports AI |
| Foreign workspace path | `IMPLEMENTATION_GUIDE.md` | Says the project is 'located in /home/ubuntu/DevOps-SRE'. The repo is devops-sre-p1. Points to an agent or a session working in another directory. | Supports AI |
| Generator fingerprints | `k8s/deployments.yaml, *.sh` | Box-drawing banners, 'Crucial requirement' inline comments, headings like 'Crucial Memory Limit & OOMKilled Engineering'. | Supports AI |
| Placeholders never filled | `alertmanager-config.yaml` | Slack webhook https://example.com/slack-webhook-placeholder and sre-team@example.com. | Supports AI |
| Confident technical error | `TASK2_GITOPS_ARGOCD.md` | States kube-proxy and CoreDNS distribute traffic across pods. CoreDNS does not load-balance. | Supports AI |
| Unvalidated design gaps | `pr-ci.yaml, release.yaml` | Trivy exit-code 0 (gate never fails), fixed tags (GitOps update is a no-op after run 1). Both would surface on first real use. | Supports AI |
| Lint and tests pass | `app/, test/` | Replayed locally: Flake8, Bandit, pytest all pass. Reformatting app.py shows someone ran Flake8 at least once. | Against AI (weak) |

**Our read:** This reads as an AI agent or long chat session producing the whole assessment in one go, followed by generated docs. There is no screenshot, log, failed run, or second pass anywhere. The engineering choices are fine, but none of them can be credited to the learner without a live demo.

## Originality

**Status:** Clear

No overlap with other learners. The originality question here is human versus AI, not peer copying.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Run the release pipeline twice. What does the manifest-update step change the second time?
2. Your Trivy step uses exit-code 0. What does that mean for a PR with a CRITICAL CVE?
3. Which component actually load-balances a ClusterIP Service: CoreDNS or kube-proxy?
4. Show kubectl describe on a pod that got OOMKilled at 400Mi. Where do you see it?
5. What does your initContainer do, and what would a useful one do here?
6. Where is /home/ubuntu/DevOps-SRE, and how was this repo produced?

## Timeline context

The whole solution was committed on Thursday 15 Oct at 12:05 IST: 27 files and 1,604 lines covering all three tasks in a single commit. A second commit 80 minutes later added 525 lines of documentation. There has been no activity since.

*Expectation calibration:* Had the full week. The issue is not how much was done but whether it was built and understood.

## Requirement-by-requirement status

13 done, 10 partial and 1 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.11-alpine, UID 10001, HEALTHCHECK, Python env flags set. |
| Branch protection (PR-only changes to main) | 🔴 Missing | No ruleset or protection evidence. Both commits went straight to main. |
| PR pipeline: build the image | 🟡 Partial | Buildx build with load: true. Correct, but has never run because no PR was opened. |
| PR pipeline: lint (Flake8) | 🟢 Done | app.py reformatted. Flake8 passes when replayed locally. |
| PR pipeline: SAST (B104 ignored) | 🟢 Done | Bandit with -s B104. Passes locally. |
| PR pipeline: secret scanning (optional) | 🟢 Done | TruffleHog on the PR diff, verified secrets only. |
| PR pipeline: unit tests (pytest) | 🟢 Done | pytest, 6 of 6 pass locally. |
| PR pipeline: image vulnerability scan | 🟡 Partial | Trivy runs with exit-code: 0, so vulnerabilities never block a PR. |
| Release pipeline: build and push to a registry | 🟢 Done | Matrix build of v1.0.0, v1.1.0 and v1.2.0 to GHCR. The one run passed. |
| Release pipeline: auto-update manifest image tags | 🟡 Partial | sed rewrites the image lines, but the tags are fixed strings. After the first run nothing changes, so ArgoCD never sees a new version. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🟡 Partial | Application with automated prune and selfHeal, plus an install script. Nothing shows it was run. |
| Three Deployments behind one shared Service | 🟢 Done | memory-app-v1, v2 and v3 behind one Service on app: memory-app. |
| Requests set and memory limit of 400Mi | 🟢 Done | 150Mi request, 400Mi limit. |
| Namespaces, ConfigMaps and Secrets | 🟢 Done | Namespace memory-app-prod, ConfigMap and Secret loaded with envFrom. |
| initContainers | 🟡 Partial | busybox init container that only echoes and sleeps. It doesn't validate or prepare anything. |
| RBAC (ServiceAccount, Role, RoleBinding) | 🟢 Done | ServiceAccount, Role and RoleBinding. |
| NetworkPolicies | 🟢 Done | Ingress on 8080 from the cluster, egress limited to DNS. |
| ResourceQuotas | 🟢 Done | ResourceQuota plus a LimitRange. |

**Task 3: Observability and alerting**

| Requirement | Status | Finding |
|---|---|---|
| Prometheus and Grafana via Helm | 🟡 Partial | Helm values and an install script. No evidence they were installed. |
| Dashboard: node and per-pod CPU/memory | 🟡 Partial | Custom dashboard JSON (memory against the 400Mi line, restarts, node CPU, memory and disk). Not shown imported. |
| Log aggregation (Loki, EFK or similar) | 🟡 Partial | Loki and Promtail values. Not shown running. |
| Grafana alerts: health check and OOMKilled | 🟡 Partial | Prometheus rules for health, OOMKilled and approaching-OOM, rather than Grafana alerts. |
| Alert routing to Slack or email (bonus) | 🟡 Partial | Alertmanager Slack and email config with placeholder targets (example.com). |

**Documentation**

| Requirement | Status | Finding |
|---|---|---|
| Setup, architecture and reproduction steps | 🟢 Done | About 610 lines across the README, an implementation guide and three task guides. |

## Technical strengths
- Widest coverage of the brief in the cohort, with a clear folder layout (k8s/, argocd/, observability/).
- Lint, SAST and unit tests all pass when replayed on the code.
- An 'approaching OOM' warning alert before the hard OOMKilled alert is a good SRE instinct.
- Hardened pod securityContext and a LimitRange alongside the quota.

## Technical gaps to fix
- Set Trivy exit-code to 1 so the image scan actually gates the PR.
- Tag images with the commit SHA (or a version derived from it) so the manifest update changes something and ArgoCD rolls out new builds.
- Give the initContainer a real job, for example checking the ConfigMap values or waiting on a dependency.
- Turn on branch protection and push work through PRs. The release job also pushes to main directly, which protection would block, so plan for that (a bot token or a PR).
- Correct TASK2_GITOPS_ARGOCD.md: kube-proxy balances Service traffic. CoreDNS only resolves the Service name.
- Replace the example.com Slack and email targets with a real webhook or address, and move alerts to Grafana.
