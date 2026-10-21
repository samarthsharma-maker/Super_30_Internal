# Kiruthik: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** connect2kiruthik@gmail.com  
**Repo:** [github.com/Kiruthik25/DevSecOps-Assessment](https://github.com/Kiruthik25/DevSecOps-Assessment)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Best hands-on evidence in the cohort. Deployed and debugged a real stack, then let AI write docs that oversell it.

## Placement read

| | |
|---|---|
| **Placement tier** | **Strong**: Clear positive signal. Recommend for placement conversations now. |
| **Effect on placement chances** | Increase |
| **AI-generation likelihood** | Medium (confidence: Medium) |
| **Where AI likely shows up** | Documentation, likely some manifests |
| **Originality** | Clear |
| **Stage reached** | All three tasks attempted |
| **CI status** | Failing. Release workflow failed on all 15 runs; PR workflow has never run |
| **Started** | Thu 15 Oct, 22:42 IST |
| **Last commit** | Sat 17 Oct, 21:31 IST (19 commits over 3 days) |

**Recommended action:** Put forward. In the placement call, spend 10 minutes on CI fundamentals and ask them to correct the README before it goes on a CV.

### Signals that raise their chances
- Only learner to prove end to end: ArgoCD sync, dashboards, and an alert that actually fired on OOMKilled.
- Chose a mature log stack (EFK via ECK operator), not just the easiest option.
- Good pod security instincts: read-only root FS, drop ALL, seccomp RuntimeDefault, no SA token automount.
- Started early (Thursday) and sustained effort across three evenings.

### Signals that lower their chances
- Neither pipeline has ever gone green. The PR pipeline has a basic bug (pytest run where there are no tests).
- Never used a PR. Branch protection, the core DevSecOps control in Task 1, was skipped.
- Documentation claims work that isn't there. Minor in scale, but it is an honesty-in-writing signal.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| README 'What I Implemented' | `readme.md` | Claims Secrets, NetworkPolicies and init containers. None exist; networkpolicy.yaml is 0 bytes. | Supports AI |
| Docs reference phantom files | `grafana/README.md, altering/readme.md` | Mentions k8s-pod-healht.yaml, kubernetes-pod-health-alerts.yaml, alertmanager-routing-values.yaml and an alerting/ folder. None are in the repo. | Supports AI |
| Templated prose | `grafana/README.md` | Repeated 'Why this step matters' blocks and pandoc grid tables. Drafted elsewhere and pasted. | Supports AI |
| Live screenshots | `ArgoCd/, grafana/, altering/` | ArgoCD tree with v1/v2/v3 Healthy, Grafana dashboards, a real OOMKilled alert email at 20:08 on 16 Oct. | Against AI |
| Iterative commit trail | `git log` | 19 commits over three evenings, each a small step (workflow, ArgoCD, SMTP, rules, EFK). | Against AI |
| Real environment fingerprint | `first commit` | Authored from an EC2 host (ubuntu@ip-172-31-36-195), the same box the screenshots come from. | Against AI |

**Our read:** AI almost certainly helped write the documentation and possibly scaffold manifests, but the learner ran everything and got real results out of it. That is how good engineers use AI. The concern is the docs overclaiming, which in a job would mean a design doc that doesn't match production.

## Originality

**Status:** Clear

No overlap with other submissions found.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Your PR pipeline runs pytest from app/. What happens and why?
2. Your README says you implemented NetworkPolicies. Walk me through networkpolicy.yaml.
3. Your probes are tcpSocket. Would they catch the app returning 500 on /healthcheck?
4. Explain the OOMKilled PromQL rule. Why combine last_terminated_reason with restarts_total?
5. Why is ArgoCD auto-sync off, and what changes if you turn it on?

## Timeline context

Started on Thursday 15 Oct, about six days after the brief went out, and worked across three evenings (15, 16 and 17 Oct). The first commit came from an EC2 VM. Kubernetes ran on that VM rather than a local Minikube or Kind cluster, which is a small departure from the 'run locally' rule but in the same spirit.

*Expectation calibration:* Had a full working week, so it is fair to hold this submission to the complete brief.

## Requirement-by-requirement status

13 done, 8 partial and 3 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟢 Done | python:3.12-slim, UID 10001, HEALTHCHECK on /healthcheck. Alpine or distroless would be smaller. |
| Branch protection (PR-only changes to main) | 🔴 Missing | All commits went straight to main, several through GitHub's web upload. |
| PR pipeline: build the image | 🟡 Partial | Image build is in the PR workflow, but no PR was ever opened, so it has never run. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Runs on the unmodified app.py, which fails Flake8 on whitespace and blank-line rules (W291, W293, E302, E305). |
| PR pipeline: SAST (B104 ignored) | 🟢 Done | Bandit with -s B104. |
| PR pipeline: secret scanning (optional) | 🟢 Done | Gitleaks. |
| PR pipeline: unit tests (pytest) | 🟡 Partial | pytest runs inside app/, where there are no tests, so it exits with code 5 (no tests collected) and fails. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy on HIGH and CRITICAL with exit-code 1, so it blocks the merge. |
| Release pipeline: build and push to a registry | 🟡 Partial | v1/v2/v3 matrix to Docker Hub with commit-SHA tags, but every run has failed. |
| Release pipeline: auto-update manifest image tags | 🟡 Partial | yq rewrites the tags and opens a PR, but the step is never reached because the build job fails. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🟡 Partial | Screenshot shows ArgoCD v3.5.5 with the app Synced and Healthy. Auto-sync is off and the destination namespace is 'default'. |
| Three Deployments behind one shared Service | 🟢 Done | python-app-v1, v2 and v3 behind one ClusterIP Service. |
| Requests set and memory limit of 400Mi | 🟢 Done | 128Mi request, 400Mi limit. The OOMKilled alert for python-app-v2 proves the limit works. |
| Namespaces, ConfigMaps and Secrets | 🟡 Partial | Namespace and ConfigMap present. No Secret. |
| initContainers | 🔴 Missing | No initContainers. |
| RBAC (ServiceAccount, Role, RoleBinding) | 🟢 Done | ServiceAccount, read-only Role, RoleBinding, and automountServiceAccountToken: false. |
| NetworkPolicies | 🔴 Missing | networkpolicy.yaml is an empty file and is not listed in kustomization.yaml. |
| ResourceQuotas | 🟢 Done | ResourceQuota plus a LimitRange. |

**Task 3: Observability and alerting**

| Requirement | Status | Finding |
|---|---|---|
| Prometheus and Grafana via Helm | 🟢 Done | kube-prometheus-stack via Helm. |
| Dashboard: node and per-pod CPU/memory | 🟢 Done | Node Exporter, pod overview and a custom dashboard, with screenshots. |
| Log aggregation (Loki, EFK or similar) | 🟢 Done | EFK: Elasticsearch and Kibana through the ECK operator, Fluent Bit as a DaemonSet. |
| Grafana alerts: health check and OOMKilled | 🟡 Partial | Pod-not-ready and OOMKilled alerts work, but as Prometheus rules. The brief asks for Grafana-managed alerts. |
| Alert routing to Slack or email (bonus) | 🟢 Done | Alertmanager email routing over Gmail SMTP, with a screenshot of a real alert. |

**Documentation**

| Requirement | Status | Finding |
|---|---|---|
| Setup, architecture and reproduction steps | 🟢 Done | About 1,060 lines across the README and the Grafana, alerting and EFK guides. |

## Technical strengths
- Only learner with evidence of a live cluster: ArgoCD tree view, Grafana dashboards and an OOMKilled alert email for python-app-v2.
- Solid container hardening in the Deployments: readOnlyRootFilesystem, all capabilities dropped, seccomp RuntimeDefault, non-root UID.
- Went beyond the brief with a LimitRange and a full EFK stack.
- Release design is sound: matrix build, SHA-pinned tags and a PR (not a direct push) for the manifest update.

## Technical gaps to fix
- PR pipeline: run tests from the repo root (pytest test/) and either reformat app.py or add a .flake8 config. As written it can never pass.
- Release pipeline: open the failed run logs. Check that DOCKERHUB_USERNAME, DOCKERHUB_TOKEN and GH_PAT are set as repo secrets. Note that paths-ignore skips runs when only .github/ changes.
- Turn on branch protection for main and send changes through PRs so the PR pipeline actually gates something.
- Fill in networkpolicy.yaml and add it to kustomization.yaml. Add a Secret and an initContainer to meet the Task 2 list.
- ArgoCD: enable automated sync (prune, selfHeal) and set the destination namespace to memory-app.
- Switch the probes from tcpSocket to httpGet on /healthcheck so health failures are actually detected.
- Recreate the two alerts as Grafana-managed alert rules, or explain in the README why Prometheus rules were chosen.
