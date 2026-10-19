# DevOps-SRE Cohort: Internal Placement Summary

> **INTERNAL.** AI-use and originality calls are inferences from commit history, file contents and cross-repo comparison. Confirm with the verification questions in each learner's file before they affect placement outcomes.

Reviewed 19 Oct 2026. The brief was published 9 Oct. 17 learners made progress; 9 others had nothing gradable (starter only, empty, unrelated or unidentified repos) and are not included here.

## Tiers

- **Strong**: Clear positive signal. Recommend for placement conversations now.
- **Promising**: Real skill visible. Needs more progress or one quick check.
- **Early**: Too little work to judge. Neutral for now.
- **Hold**: Do not use this submission as a positive signal until verified live.
- **Concern**: Negative signal on originality or ownership. Lower priority.

## Cohort at a glance

Sorted by placement tier, then by stage.

| Learner | Tier | Effect on chances | Stage | AI likelihood | Originality | Started | Next action |
|---|---|---|---|---|---|---|---|
| [Kiruthik](Kiruthik.md) | **Strong** | Increase | All three tasks attempted | Medium (Medium) | Clear | Thu 15 Oct | Put forward; quick CI-fundamentals check, fix README overclaims. |
| [Amit](Amit.md) | **Strong** | Increase | Tasks 1 and 2, Task 3 started | Low (Medium) | Shared code (source) | Sat 17 Oct | Put forward; ask about the Task 3 plan. |
| [Akshay](Akshay.md) | **Strong** | Increase | Task 1 complete (core) | Low (Medium) | Clear | Sat 17 Oct | Put forward for CI/CD roles; check Kubernetes depth. |
| [Deepak](Deepak.md) | **Promising** | Slight increase | Task 1 in progress | Low (Medium) | Clear | Sun 18 Oct | Re-check in a week. |
| [Nayan](Nayan.md) | **Promising** | Neutral to increase | Task 1: Dockerfile done | Low (Medium) | Clear | Sun 18 Oct | Re-check in a week. |
| [Abhishek](Abhishek.md) | **Promising** | Slight increase | Task 1 in progress | Low (Medium) | Clear | Thu 15 Oct | Nudge to finish Task 1; good depth signal. |
| [Shreya](Shreya.md) | **Early** | Neutral | Task 1 in progress | Low (Low) | Clear | Fri 16 Oct | Nudge; re-assess later. |
| [Ahmed Bilal](Ahmed_Bilal.md) | **Early** | Neutral | Task 1 in progress | Low (Medium) | Clear | Thu 15 Oct | Nudge to get CI green. |
| [Nashita](Nashita.md) | **Early** | Slight decrease | Task 1 in progress, Task 2 started | Medium (Medium) | Clear | Sat 17 Oct | Ask why the gates can't fail; fix the image. |
| [Tripurakant](Tripurakant.md) | **Early** | Slight decrease | Task 1 in progress | Low (Low) | Clear | Wed 14 Oct | Check in on blockers. |
| [Manoj](Manoj.md) | **Early** | Neutral, integrity positive | Task 1: Dockerfile done | Low (Medium) | Clear | Fri 16 Oct | Nudge; integrity positive. |
| [Shishir](Shishir.md) | **Early** | Neutral | Task 1: Dockerfile only | Low (Medium) | Source of copied file | Thu 15 Oct | Ask if he shared his Dockerfile. |
| [Vijay Kumar](Vijay_Kumar.md) | **Hold** | Decrease until verified | All three tasks attempted (unverified) | High (High) | Clear | Thu 15 Oct | 20-minute live walkthrough before any credit. |
| [Utkarsh](Utkarsh.md) | **Hold** | Decrease until verified | Tasks 1 and 2, Task 3 not started | High (Medium-High) | Clear | Sat 17 Oct | Live walkthrough; fix Bandit and tags on the spot. |
| [Nikhil](Nikhil.md) | **Concern** | Decrease | Task 1 in progress, Task 2 started | Medium (Medium) | Flagged (matches Amit) | Sat 17 Oct | Ask about the source of the pipeline code. |
| [Harshal](Harshal.md) | **Concern** | Decrease | Task 1: Dockerfile only | Low (Low) | Flagged (matches Shishir) | Fri 16 Oct | Originality conversation. |
| [Hardik](Hardik.md) | **Concern** | Decrease | Task 1: Dockerfile only | Low (Low) | Flagged (matches Shishir) | Fri 16 Oct | Originality conversation; wait for original work. |

## Originality clusters

| Cluster | Earliest (likely source) | Later matches | Confidence | Evidence |
|---|---|---|---|---|
| Alpine Dockerfile | Shishir (16 Oct, 12:39 IST) | Hardik (13:55), Harshal (14:03 to 14:09) | High for Harshal, Medium for Hardik | Identical lines incl. the wrong EXPOSE 80; Harshal's first version was a broken slim/Alpine hybrid, fixed 6 minutes later to match exactly. |
| Release tag-update Python + 'memory-leak-service' image name | Amit (17 Oct, 12:15 IST) | Nikhil (17 Oct, 20:44 IST) | Medium-High | Identical regex, lambda and count=1 logic; only the error string differs. Nikhil's adaptation introduced an invalid ':v1:<sha>' reference. |

## High AI-likelihood submissions

| Learner | Core reason | What would clear it |
|---|---|---|
| Vijay Kumar | Whole three-task solution (1,604 lines) in one commit, docs 80 minutes later, a foreign workspace path in the docs, placeholders never filled, no run evidence. | Live demo on their own machine: deploy, show OOMKilled, explain the Trivy and tag gaps. |
| Utkarsh | 814-line single commit; README claims branch protection blocks pushes (it doesn't) and that Helm monitoring is installed (no files); a never-ran Bandit flag. | Explain and fix the Bandit and tag-update issues live. |

## How to read the AI calls

- **AI use is not the problem by itself.** Most strong engineers use assistants. The placement question is whether the learner can run, debug and explain what they submitted.
- **Strongest indicators** used here: whole-project single commits with no iteration; docs that describe things not in the repo; mistakes that any first run would expose; placeholder values left in; environment fingerprints from another workspace.
- **Strongest counter-indicators**: incremental debugging commits, screenshots or logs from a live system, decisions tied to real tool output (for example 'switched to Alpine after Trivy flagged HIGH CVEs').
- **Weekend starters** (17 to 18 Oct: Amit, Akshay, Utkarsh, Nikhil, Nashita, Deepak, Nayan) had about two days. Judge them on quality per hour, not coverage.
