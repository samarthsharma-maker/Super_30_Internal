# Shivam Singh: Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | shivamsingh.200107@gmail.com |
| **Submission email** | shivamsingh.work@proton.me |
| **Submitted link(s)** | [Abstergo-47/DevOps-SRE](https://github.com/Abstergo-47/DevOps-SRE) |
| **Category** | Starter only, untouched |
| **Commits by the learner for this brief** | 0 |
| **Last relevant activity** | None. The only commit is the template's own 'Final commit' (9 Oct, authored by the brief's author). |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- The repo is a byte-for-byte copy of the starter: app/app.py, test/test_case.py and the brief's readme.md.
- Zero commits authored by the learner. Not even a Dockerfile or an edited README.
- The submission email (proton.me) differs from the registered one (gmail), so confirm we are talking to the right person.

## Critical assessment

Shivam submitted a link to a repo he has not touched. Ten days after the brief went out there is nothing of his to read, run or grade. Submitting an untouched template as if it were a submission is worse than not submitting at all: it suggests he wanted the row filled in the sheet rather than the work done.

## Red flags

- Submitted the untouched starter as a project link.
- Email mismatch between registered and submission columns.

## Placement impact

Decrease. There is no evidence of DevOps, CI/CD or Kubernetes skill to put in front of a hiring partner. Should not be prioritised for DevOps or SRE placement drives until this changes.

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

- Within 3 days: a Dockerfile and a PR pipeline (Flake8, Bandit with -s B104, pytest, Trivy) committed by him.
- Within 7 days: release pipeline and the Task 2 manifests (three Deployments, shared Service, 400Mi limit).

## Questions for the follow-up conversation

1. You submitted this link but have no commits. What happened?
2. What is blocking you on Task 1: Docker, GitHub Actions, or time?
3. Which email should we use for you?
