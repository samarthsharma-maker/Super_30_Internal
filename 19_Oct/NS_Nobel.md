# Nobel: Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | csnobel2001@gmail.com |
| **Submission email** | csnobel2001@gmail.com |
| **Submitted link(s)** | [Ignatius-Nobel/Devops-SRE](https://github.com/Ignatius-Nobel/Devops-SRE) |
| **Category** | Starter only |
| **Commits by the learner for this brief** | 1 (setup only) |
| **Last relevant activity** | Sun 18 Oct, 'initial commit' |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- One 'initial commit' on 18 Oct with the starter files only.
- Repo set up nine days after the brief was published, with no work after that.

## Critical assessment

Nobel only created the repo on Sunday, so he lost most of the ten days before starting. Even allowing for a late start, nothing has been attempted, not even the Dockerfile, which is a 15-minute task. Of the starter-only group he is the most likely to still be just beginning, but the late start itself is the problem.

## Red flags

- Started nine days late.

## Placement impact

Decrease for now. Re-check later this week before concluding.

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

- Within 2 days: Dockerfile and PR pipeline.
- Within 7 days: release pipeline and Task 2 manifests.

## Questions for the follow-up conversation

1. Why the late start?
2. What is your plan for the next three days?
