# Vikash Mishra: Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | mishra.vikash081@gmail.com |
| **Submission email** | mishra.vikash081@gmail.com |
| **Submitted link(s)** | [devopswithmishraji/DevOps-SRE](https://github.com/devopswithmishraji/DevOps-SRE) |
| **Category** | Starter only |
| **Commits by the learner for this brief** | 1 (setup only) |
| **Last relevant activity** | Fri 16 Oct, 'project setup' |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- One commit on 16 Oct that adds the three starter files. Nothing beyond the template.
- The same empty link was submitted twice in the sheet.
- The GitHub handle is 'devopswithmishraji', a public DevOps-branded account, yet it has no DevOps work in the repo.

## Critical assessment

Vikash set the repo up and stopped. Submitting the same empty link twice suggests he cared more about the submission being recorded than about the content. For someone presenting publicly as a DevOps profile, an empty assessment repo is a reputational risk if a recruiter looks at it.

## Red flags

- Duplicate submission of an empty repo.
- Public 'DevOps' handle with no DevOps work visible.

## Placement impact

Decrease. Nothing to evidence skills. Do not put forward until there is real work in this repo.

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

- Within 3 days: Dockerfile plus a passing PR pipeline on a real pull request.
- Within 7 days: release pipeline, Kubernetes manifests and ArgoCD.

## Questions for the follow-up conversation

1. The repo has only the starter files. What have you tried so far, even locally?
2. Why was the link submitted twice?
