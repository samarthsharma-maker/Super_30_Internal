# Nashita: Internal Assessment

> **INTERNAL. Do not share with the learner.** Includes AI-use and originality judgements and placement guidance. Judgements are inferred from repository evidence and should be confirmed in conversation before they affect outcomes.

**Email:** nashitakerfeldt@gmail.com  
**Repo:** [github.com/cloudnash/DevSecOps-and-Site-Reliability-Engineering-SRE-Project](https://github.com/cloudnash/DevSecOps-and-Site-Reliability-Engineering-SRE-Project)  
**Reviewed:** 19 Oct 2026, against [scaler2101/DevOps-SRE](https://github.com/scaler2101/DevOps-SRE)

**Bottom line:** Got the release loop working, but the PR gates are set so they can never fail. That is a DevSecOps red flag.

## Placement read

| | |
|---|---|
| **Placement tier** | **Early**: Too little work to judge. Neutral for now. |
| **Effect on placement chances** | Slight decrease |
| **AI-generation likelihood** | Medium (confidence: Medium) |
| **Where AI likely shows up** | CI workflows |
| **Originality** | Clear |
| **Stage reached** | Task 1 in progress, Task 2 started |
| **CI status** | Release passed |
| **Started** | Sat 17 Oct, 20:53 IST |
| **Last commit** | Sat 17 Oct, 22:46 IST (2 commits, plus 1 automated commit) |

**Recommended action:** Neutral to slightly negative until the gate question is answered. The release loop is a good sign if the understanding is there.

### Signals that raise their chances
- Only learner whose release loop pushed an image and auto-committed the tag successfully.

### Signals that lower their chances
- The container cannot start (COPY path bug), so everything downstream is shipping a broken image.
- Disabled gates in a security-focused assessment.
- One Deployment, no limits.

## AI usage and originality evidence

| Signal | Where | What we saw | Points to |
|---|---|---|---|
| Tutorial-style comments | `workflows` | A comment on almost every step: '# Fails the pipeline if vulnerabilities are found', '# Convert repository owner to lowercase (Docker requirement)'. | Supports AI |
| Boilerplate for a missing file | `pr-pipeline.yaml` | pip install -r requirements.txt \|\| true, but there is no requirements.txt. | Supports AI |
| Gates neutralised | `pr-pipeline.yaml` | pytest \|\| true, and Flake8 limited to fatal error classes. | Supports AI |
| Default git identity | `git log` | Author 'cloudnash <you@example.com>'. | Neutral |
| Release actually ran | `Actions` | Image pushed and the bot commit updated the manifest. | Against AI |

**Our read:** CI looks lifted from a generated template and not adapted. The '|| true' choices are the important part: whether AI wrote them or not, they show the learner was optimising for a green check rather than a working gate.

## Originality

**Status:** Clear

No overlap with other learners.

## Verification questions for a placement or screening call

Use these to separate 'built it' from 'generated or copied it'. Someone who did the work answers them quickly and concretely.

1. Why pytest || true? What happens if a test fails?
2. Run your image locally. What happens?
3. Flake8 --select=E9,F63,F7,F82: what does that actually check?

## Timeline context

Started on Saturday 17 Oct at 20:53 IST and finished the current state within two hours that evening. This is a weekend start.

*Expectation calibration:* For a single evening, getting the release loop working is good. The broken image and soft gates are the priority.

## Requirement-by-requirement status

4 done, 5 partial and 15 missing, out of 24 checkpoints.

**Task 1: Docker and secure CI/CD**

| Requirement | Status | Finding |
|---|---|---|
| Dockerfile (minimal base, non-root user) | 🟡 Partial | python:3.11-slim, non-root. COPY . /app/ copies the whole repo, so app.py lands at /app/app/app.py while CMD runs app.py from /app. The container exits on start. No .dockerignore. |
| Branch protection (PR-only changes to main) | 🔴 Missing | Commits went straight to main. |
| PR pipeline: build the image | 🟢 Done | Builds the image in the PR pipeline. |
| PR pipeline: lint (Flake8) | 🟡 Partial | Flake8 only checks fatal error classes (E9, F63, F7, F82), so it isn't really linting. |
| PR pipeline: SAST (B104 ignored) | 🟡 Partial | bandit -r . scans the tests too and fails on assert (B101). |
| PR pipeline: secret scanning (optional) | 🔴 Missing | No secret scanning (optional in the brief). |
| PR pipeline: unit tests (pytest) | 🟡 Partial | pytest \|\| true, so test failures never block a merge. |
| PR pipeline: image vulnerability scan | 🟢 Done | Trivy gating. |
| Release pipeline: build and push to a registry | 🟢 Done | Pushes a SHA-tagged image to GHCR. The run passed. |
| Release pipeline: auto-update manifest image tags | 🟢 Done | sed updates the manifest and commits back. The bot commit shows it worked. |

**Task 2: GitOps with ArgoCD**

| Requirement | Status | Finding |
|---|---|---|
| ArgoCD installed and syncing the repo | 🔴 Missing | Not started. |
| Three Deployments behind one shared Service | 🟡 Partial | One Deployment (leaky-app-v1) and no Service. |
| Requests set and memory limit of 400Mi | 🔴 Missing | No resources block. |
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
- The only learner whose release pipeline pushed an image and auto-committed the new tag to the manifest successfully.

## Technical gaps to fix
- Fix the Dockerfile: COPY app/app.py . (or set CMD to app/app.py) and add a .dockerignore.
- Remove '|| true' from pytest, lint properly, and scope Bandit to app/.
- Add requests and a 400Mi limit, two more Deployments and a shared Service.
- Set your git identity. Commits are authored as you@example.com.
