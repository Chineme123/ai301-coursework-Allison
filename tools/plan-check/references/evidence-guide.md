# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

**Where it lives:** In eval mode, read the candidate plan's cause or
diagnosis against the package's Issue, Thread highlights, and Repro
evidence sections. In live mode, compare the diagnosis in `plan.md`
with the issue thread and the student's posted Unit 2 reproduction
comment. Use the reproduction artifacts quoted in the plan as the
evidence available to the grader.

**What good looks like:** The proposed cause explains the behavior the
reproduction actually demonstrated and does not contradict it. Facts,
inferences, and unresolved assumptions are distinguishable; a
plausible but unproven cause is acceptable when its uncertainty is
stated honestly.

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

## Scope

**Where it lives:** In eval mode, inspect the Candidate plan's change,
in-scope and out-of-scope statements, and named files or code areas.
Use the Issue and Repro evidence to confirm that the proposed boundary
addresses the reproduced problem. In live mode, use the matching parts
of `plan.md` and verify named paths against the fork's repository tree.

**What good looks like:** The in-scope statement explicitly names the
files expected to be changed or touched. The out-of-scope statement
may be broader, but it identifies meaningful folders, components, or
related behavior excluded from the change.

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

## Executability

**Where it lives:** In eval mode, read the Candidate plan's named files,
approach, and order of work, with Repo facts for relevant repository
constraints. In live mode, read `plan.md`, the fork's current source,
and repository setup or contribution documentation.

**What good looks like:** A developer can identify where to begin and
what change to attempt without inventing the plan's central approach.
Open implementation choices may remain, but missing information must
not prevent the first meaningful development step.

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

## Test plan

**Where it lives:** In eval mode, inspect the Candidate plan's Test
statement and any supplied or referenced test code, then compare it
with the Repro evidence's trigger and observed result. In live mode,
read the test-plan portion of `plan.md`, any referenced local test
file, and the posted Unit 2 reproduction steps.

**What good looks like:** The test plan either explicitly directs or
permits the implementing agent to create an automated test for the
fix, or supplies a concrete automated test script. The proposed test
uses the reproduced trigger or equivalent real-code path and names an
observable result that distinguishes the fixed behavior from the bug.

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

## Honesty

**Where it lives:** In eval mode, compare the Candidate plan's cause,
risks, unknowns, and Deviations statements with the Repro evidence and
Thread highlights. In live mode, inspect the same claims in `plan.md`
against the issue thread, reproduction comment, and later build facts.

**What good looks like:** Confirmed observations are not overstated as
proof of an unverified cause. Important unknowns and risks are named,
and the final Deviations section truthfully records what changed from
the posted plan—or states in the author's own words that nothing
changed.

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

## Comms

**Where it lives:** In eval mode, read the Candidate plan comment
against Thread highlights and the Repo facts covering templates,
contribution instructions, and AI-use disclosure rules. In live mode,
read `comment.md` against the current issue thread, repository
documentation and templates, and `voice-guide.md`.

**What good looks like:** The comment communicates the plan's actual
diagnosis, bounded change, and test approach without claiming more than
the evidence supports. It responds to relevant maintainer direction,
follows stated repository conventions and disclosure requirements,
and uses the student's direct, concise, conversational voice.

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->
