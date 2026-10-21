# RS (Rahul Sharma, rsbussiness01): Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | rsbussiness01@gmail.com |
| **Submission email** | rsbussiness01@gmail.com |
| **Submitted link(s)** | [RShub1105/Server_Health_Monitor](https://github.com/RShub1105/Server_Health_Monitor)<br>[RShub1105/revrag-devsecops-assignment](https://github.com/RShub1105/revrag-devsecops-assignment) |
| **Category** | Unrelated submissions |
| **Commits by the learner for this brief** | 0 for this brief |
| **Last relevant activity** | Not applicable (repos from Sep to Oct 2025 and Mar to Apr 2026) |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- Server_Health_Monitor: a Flask plus psutil dashboard from Sep to Oct 2025 with a CI workflow, a Kubernetes Deployment and a Logstash config. It is his own work but unrelated to this brief, and it commits __pycache__ and .DS_Store.
- revrag-devsecops-assignment: his take-home for a different company's DevSecOps internship (Mar to Apr 2026), a Node.js app with a Trivy-scanned workflow and a security audit write-up.
- Neither repo contains the assessment app, tests, three Deployments, ArgoCD, or the required observability stack.

## Critical assessment

Rahul has real DevOps exposure, more than several learners who did attempt the brief. But he chose to submit old work instead of doing this assessment, and one of the two links is another company's interview assignment. That reads as avoiding the task rather than being unable to do it. We cannot compare him with the cohort on the same brief, so he cannot be ranked.

## Red flags

- Re-submitted unrelated older work instead of attempting the brief.
- One link is a take-home for another employer.

## Placement impact

Decrease for this assessment. Latent skill is visible in the older repos, so if he completes the brief he could move up quickly. Until then he is not assessable.

## Everything not yet done

Every checkpoint in the brief is outstanding.

**Task 1: Docker and secure CI/CD**
- [ ] Dockerfile (minimal base, non-root user)
- [ ] Branch protection (PR-only changes to main)
- [ ] PR pipeline: build the image
- [ ] PR pipeline: lint (Flake8)
- [ ] PR pipeline: SAST (B104 ignored)
- [ ] PR pipeline: secret scanning (optional)
- [ ] PR pipeline: unit tests (pytest)
- [ ] PR pipeline: image vulnerability scan
- [ ] Release pipeline: build and push to a registry
- [ ] Release pipeline: auto-update manifest image tags

**Task 2: GitOps with ArgoCD**
- [ ] ArgoCD installed and syncing the repo
- [ ] Three Deployments behind one shared Service
- [ ] Requests set and memory limit of 400Mi
- [ ] Namespaces, ConfigMaps and Secrets
- [ ] initContainers
- [ ] RBAC (ServiceAccount, Role, RoleBinding)
- [ ] NetworkPolicies
- [ ] ResourceQuotas

**Task 3: Observability and alerting**
- [ ] Prometheus and Grafana via Helm
- [ ] Dashboard: node and per-pod CPU/memory
- [ ] Log aggregation (Loki, EFK or similar)
- [ ] Grafana alerts: health check and OOMKilled
- [ ] Alert routing to Slack or email (bonus)

**Documentation**
- [ ] Setup, architecture and reproduction steps

## Minimum bar to be reconsidered

- Within 5 days: complete Task 1 and Task 2 on the actual brief. His prior experience should make this realistic.

## Questions for the follow-up conversation

1. Why submit older projects instead of the assessment?
2. You've done Trivy and Kubernetes work before. What stops you doing this brief?
