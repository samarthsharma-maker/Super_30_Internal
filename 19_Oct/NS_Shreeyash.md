# Shreeyash: Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | shreeyashntl@gmail.com |
| **Submission email** | shreeyashntl@gmail.com |
| **Submitted link(s)** | [github.com/shrey38 (profile)](https://github.com/shrey38) |
| **Category** | No repo identified |
| **Commits by the learner for this brief** | Unknown |
| **Last relevant activity** | Unknown. Per the reviewer's manual check, the most recent public repo is from Sept 17 and unrelated (Python Celery). |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- Submitted a GitHub profile, not a repository.
- We checked the visible repos and likely names (DevOps-SRE, devops-sre-project, DevSecOps-SRE-Project and similar) and found no repo for this assessment.
- The pinned repos are older and unrelated (sentiment analysis, Java CRUD apps, a diabetes predictor).

## Critical assessment

Shreeyash gave us a profile and left us to find the work, and there is no work to find. Sharing a whole profile instead of a repo link is either a misunderstanding of the brief or a way to look like a submission without having one. Either way the result is the same: nothing to assess.

## Red flags

- Profile link instead of a repo.
- No matching repo found.

## Placement impact

Decrease. Not assessable.

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

- Within 2 days: send the exact repo link, or create one from the starter with a Dockerfile and PR pipeline.

## Questions for the follow-up conversation

1. Which repo is your assessment in?
2. If you haven't started, what is your plan for this week?
