# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Evidence-grounded diagnosis | The plan's stated or suspected root cause, read against the reproduction evidence quoted in the plan and the observed behavior that evidence records. | Pass if the diagnosis clearly explains what the reproduction evidence shows and identifies a plausible cause that is consistent with those observations. Any uncertainty or assumption about the cause must be stated honestly rather than presented as confirmed fact. | required |
| Explicit implementation scope | The plan's in-scope and out-of-scope statements, including its list of files or code locations to be changed. | Pass if the in-scope work explicitly names the files expected to be changed or touched. The out-of-scope statement may be broader, but it must identify meaningful folders, components, or related work that the change will not cover. | required |
| Automated test path | The plan's test-plan instructions and any automated test script or test code included or referenced there. | Pass if the test plan either explicitly directs or permits the implementing agent to create an automated test for the fix, or already provides a concrete automated test script for the fix. Fail if neither an explicit instruction to create the test nor an automated test script is present. | required |

## Verdict rule

Return `accept` (ready) only when every required check passes. Return
`reject` (hold) if any required check fails or is `unclear`. Preferred
checks, if added later, may help compare plans but never change the
final verdict.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
