# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment matches the target | The repro report's environment record, read against the issue's explicit environment requirements, repository setup documentation, and the repo-facts block in eval mode. | Pass when the report identifies the environment details needed to interpret the attempt. When the issue explicitly limits the reported behavior to a version, operating system, architecture, dependency, or configuration, the tested conditions must match that limit or clearly disclose the deviation. | required |
| Steps are independently followable | The repro report's prerequisites, starting state, setup actions, commands or interactions, and trigger sequence. | Pass when a stranger can begin from the stated starting state and reach the attempted trigger without guessing a material command, input, configuration choice, or transition. | required |
| Evidence shows the reported behavior | The report's output excerpts, logs, screenshots, test results, or other artifacts, read against the behavior described in the issue. | Pass when the artifacts directly support the outcome the report states: either they show the issue's specific behavior, or they show that the stated trigger was attempted without producing it. Evidence of only a setup failure or an adjacent problem does not pass. | required |
| Conclusion is honest | The report's stated outcome and explanation, read against its steps, artifacts, errors, and limitations. | Pass when the conclusion says exactly what the evidence supports, distinguishes reproduced from not reproduced, and clearly discloses uncertainty, deviations, or blockers instead of claiming more than the attempt established. | required |
| Repository conventions are followed | The draft claim comment and repro comment, read against the issue thread, contribution documentation, comment templates, and AI-use or disclosure policy in the repo-facts block or live repository. | Pass when the comments are specific to the chosen issue, follow the repository's stated contribution and disclosure rules, and do not make unsupported claims or promises about a fix or completion date. In eval mode only, treat the candidate comments as AI-assisted solely when applying an explicit AI-use disclosure requirement. When the package's repository policy explicitly requires disclosure for that use, the required disclosure must appear in the comments; do not infer a violation of other AI policies from this eval assumption alone. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept only when every required check passes. Reject when any required
check fails or is unclear. If a check is not yet applicable to a
claim-only draft, report it as not applicable rather than using it to
reject the claim. Preferred checks, if added later, may inform feedback
but never change the verdict.
