# Mamatha: Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | nsmamatha60@gmail.com |
| **Submission email** | nsmamatha60@gmail.com |
| **Submitted link(s)** | [mamatha-nalluri/DevOps-SRE](https://github.com/mamatha-nalluri/DevOps-SRE) |
| **Category** | Starter only |
| **Commits by the learner for this brief** | 1 (setup only) |
| **Last relevant activity** | Fri 16 Oct, 'Initial commit' |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- One 'Initial commit' on 16 Oct with the starter files only, pushed from a local machine (git identity mamatha@Sris-MacBook-Air.local).
- No Dockerfile, workflows, manifests or README changes.

## Critical assessment

Mamatha cloned and pushed the starter but did not begin any of the three tasks. Three days have passed since that push with no follow-up. A local git setup shows she has the tooling, so the gap is starting, not access.

## Red flags

- Git identity not configured (machine hostname as email).

## Placement impact

Decrease. Nothing to evidence skills yet.

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

- Within 3 days: Dockerfile and PR pipeline.
- Within 7 days: release pipeline and Task 2 manifests.

## Questions for the follow-up conversation

1. What stopped you after setting up the repo?
2. Have you built the Docker image locally yet?
