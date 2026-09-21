# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| AI contribution allowed | The contribution policy in `CONTRIBUTING.md`, `.github/` contributor documentation, dedicated AI policy files such as `AI_POLICY.md`, and any AI-use requirements in pull request or issue templates; in eval mode, use the contribution policy line in the repo-facts block. | Pass if there is no explicit ban on AI-assisted contributions. Policies requiring disclosure, personal understanding, testing, or human review pass; silence also passes. | required |
| Repository active | The repository's archived status and last push to any branch; in eval mode, use `archived:` and `last push to any branch` in the repo-facts block. | Pass if the repository is not archived and its last push was within 100 days of the bundle capture date in eval mode, or within 100 days of today in live mode. | required |
| Recently active | The last push to any branch; in eval mode, use `last push to any branch` in the repo-facts block. | Pass if the last push was within 65 days of the bundle capture date in eval mode, or within 65 days of today in live mode. | preferred |
| Issue available | The issue's assignees, linked pull requests and their states, and the comment thread for claim or work-in-progress statements; in eval mode, use `assignees:`, `linked PRs:`, and the Comments section. | Pass if the issue has no assignee, no open linked pull request, and no claim or work-in-progress comment from the last 30 days that remains active. A closed unmerged pull request or an explicitly abandoned claim does not block the issue. In Path Review live mode, follow the classroom claim exception in `scope.md`. | required |
| Bounded and actionable scope | The issue title and body, the full comment thread, and closed-unmerged pull requests that show prior attempts; in eval mode, use the Issue and Comments sections and closed PRs in `linked PRs:`. | Assign a scope-risk score from 1 to 5. Score 1 for one clear task with settled direction; 2 for minor unanswered details that do not block starting; 3 for several steps or questions with one understandable outcome; 4 for major unresolved requirements, conflicting direction, or repeated abandoned attempts whose blocker remains; and 5 for an umbrella collection or discussion too fragmented to identify one contribution. Pass for scores 1 through 3; fail for scores 4 or 5. Include the score and the evidence supporting it in the check output. | required |
| Maintainer active | The dates and authors of the last 5 default-branch commits and the maintainer first-response sample; in eval mode, use both fields in the repo-facts block. | Pass if at least one of the last 5 default-branch commits was made by a non-bot human within 100 days, or at least one sampled issue received a reply from an Owner, Member, or Collaborator within 45 days. | required |
| Maintainer responsive | The first reply from an Owner, Member, or Collaborator on up to the 10 most recently updated open issues; in eval mode, use the `maintainer first-response sample` in the repo-facts block. | Pass if at least half of the sampled issues received a maintainer reply within 14 days of opening. | preferred |
| Established contributor community | The public GitHub profiles and public contribution history of the authors of up to the 5 most recently merged pull requests from non-members. | Pass if at least 2 sampled authors show prior open-source work in at least 2 other public repositories or maintain a public repository with at least 10 stars. If the evidence is unavailable, grade this check unclear; it never changes the verdict. | preferred |
| Newcomer signal | The issue's current labels, label-event history, issue body, and maintainer comments; in eval mode, use the labels, issue body, and Comments section in the bundle. | Pass if the issue currently has a `good first issue`, `help wanted`, `beginner`, or equivalent newcomer-friendly label and no maintainer comment says the work requires advanced or core-internals expertise. | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept only if every required check passes. Reject if any required check
fails or is unclear. Preferred checks never change an accept or reject
verdict; among accepted issues, rank issues with more preferred passes
higher. Break preferred-check ties by prioritizing Recently active, then
Maintainer responsive, then Newcomer signal, then Established contributor
community, and finally the personal fit profile in `scope.md`.
