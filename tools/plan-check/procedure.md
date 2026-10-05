# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

1. In live mode, read `scope.md` first and confirm that the issue is in
   the allowed repository; record any Path Review house rules that
   affect the plan or comment. In eval mode, use only the supplied
   practice package.
2. Read `rubric.md` and `references/evidence-guide.md`; list every
   check, its named evidence, its weight, and the verdict rule before
   grading.
3. Read the issue context and reproduction evidence before reading the
   proposed plan. Record the observed failure, the reproduction steps,
   and the evidence that demonstrates the behavior.
4. Read the complete plan and draft comment only after the reproduced
   behavior is established, so their claims can be compared with the
   evidence rather than accepted at face value.

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

## Evidence gathering

1. Copy the reproduction fact or short quote that best identifies the
   observed failure, then record the cause the plan proposes and
   whether the plan labels it as confirmed or uncertain.
2. From the plan's scope, record every file or code location named as
   in scope. Separately record the folders, components, or related work
   identified as out of scope.
3. From the test plan, record either the exact instruction that directs
   or permits the implementing agent to create an automated test, or
   the concrete automated test script or test code already supplied.
   Keep every recorded fact traceable to its source, and do not fill a
   missing fact with an assumption or outside knowledge.

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

## Check execution

1. Grade `Evidence-grounded diagnosis`, `Explicit implementation
   scope`, and `Automated test path` independently, in that order,
   using only the evidence gathered for that check.
2. Assign each check `pass`, `fail`, or `unclear`, and attach the one
   fact or short quote that determined the grade. Use `unclear` only
   when the evidence required by the rubric is genuinely absent or
   cannot be verified after following the evidence guide.
3. Do not let strong performance on one check compensate for another
   check. In live mode, compare the draft comment with `voice-guide.md`
   after grading the required checks and note any voice-rule mismatch.

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

## Verdict assembly

1. Apply the rubric mechanically: return `accept` only when all three
   required checks pass. Return `reject` when any required check fails
   or is `unclear`; preferred checks, if later added, never change the
   verdict.
2. In the output, include every check's grade and deciding evidence.
   When the verdict is `reject`, make the failed or unclear evidence
   explicit so the author knows what must change before rechecking.

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->
