# Ganesh: Internal Assessment (Not Submitted)

> **INTERNAL. Do not share with the learner.** Candid assessment for placement decisions. Based on the submitted link(s) as of 19 Oct 2026.

## Snapshot

| | |
|---|---|
| **Registered email** | ganeshnarapareddi@gmail.com |
| **Submission email** | ganeshnarapareddi@gmail.com |
| **Submitted link(s)** | [Ganeshnarapareddy/two-tier-flask-app](https://github.com/Ganeshnarapareddy/two-tier-flask-app)<br>[Projects/Python Project](https://github.com/Ganeshnarapareddy/Projects/tree/main/Python%20Project)<br>[Projects/Jenkins CI](https://github.com/Ganeshnarapareddy/Projects/tree/main/Jenkins%20CI) |
| **Category** | Unrelated, partly not his own |
| **Commits by the learner for this brief** | 0 for this brief |
| **Last relevant activity** | Not applicable |
| **Time available** | 10 days (brief published 9 Oct, reviewed 19 Oct), including a full weekend |
| **Checkpoints met** | **0 of 24** |
| **Placement tier** | **Not submitted** |

## What we found

- two-tier-flask-app is a copy of a widely used YouTube tutorial project. Of 92 commits, 53 are by Shubham Londhe (TrainWithShubham), with others by community contributors. Ganesh authored 12, mostly README and Dockerfile tweaks in May 2026.
- The Projects repo holds old personal practice material: a single Python script (FinalpythonProject.py), a Jenkinsfile saved as Jenkinsfile.groovy.txt, plus Ansible, Terraform and Kubernetes snippets, a folder named 'Ansible-gibrish' and a file named 'justgibbrish'.
- None of the three links contains the assessment app, tests or any of the required pipeline, GitOps or observability work.

## Critical assessment

Ganesh did not do the assessment. Instead he submitted three links to unrelated, older material, the main one of which is mostly someone else's tutorial code. Presenting a cloned tutorial as a project is a credibility problem: a hiring partner who checks the commit history will see the same thing. The scattered 'gibberish' folder and file also suggest the repos are not curated for a professional audience.

## Red flags

- Main link is a tutorial repo with most commits by the original author.
- Did not engage with the brief at all.
- Portfolio repos contain uncurated scratch files.

## Placement impact

Decrease. Nothing assessable for this brief, and the substitute links weaken rather than strengthen his profile.

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

- Within 3 days: a new repo from the starter with a Dockerfile and PR pipeline.
- Advise him to label the flask app as tutorial-based (or remove it), and to clean up the Projects repo before it goes on a CV.

## Questions for the follow-up conversation

1. None of these links is the DevOps-SRE assessment. Have you started it?
2. How much of two-tier-flask-app did you write yourself?
