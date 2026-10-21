# Janmejaya (Panda): Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | pandajanmejaya2000@gmail.com |
| **Submission email** | pandajanmejaya2000@gmail.com |
| **Submitted link(s)** | [panda-1092/Devops-SRE](https://github.com/panda-1092/Devops-SRE) |
| **Category** | Someone else's repo, no own work |
| **Commits by the learner for this brief** | 0 |
| **Last relevant activity** | Sun 24 Aug (not by the learner) |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- All 12 commits are authored by 'Harshith Varma' (Harshith-Varma-2727 and a local MacBook identity), dated 11 to 24 Aug. None are by the learner.
- The commit history shows the brief itself being drafted ('question chnages', 'added note for argocd image updater', 'Rename app.js to app.py'). The repo looks like a copy of the brief-authoring repo or an earlier cohort's version, not a learner workspace.
- No Dockerfile, CI, manifests or observability work exists.

## Critical assessment

Janmejaya has submitted a repository that he did not write a single line of. The files are the starter, and the history belongs to someone else. At best he pushed a mirror of the wrong repo. At worst he submitted another person's repo to fill the slot. Either way there is no work of his to assess, and it raises a question about how he got hold of the brief's drafting history.

## Red flags

- Every commit is authored by another person.
- Repo appears to come from the brief-authoring history, which learners would not normally have.

## Placement impact

Decrease, with an originality concern. Treat as not submitted, and clarify the repo's origin before any placement consideration.

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

- Submit his own repo, created from the current starter, within 3 days.
- Dockerfile and PR pipeline authored by him as the first commits.

## Questions for the follow-up conversation

1. All the commits in this repo are by Harshith Varma. Whose repo is this, and how did you get it?
2. Have you started the assessment anywhere else?
