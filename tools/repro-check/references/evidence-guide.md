# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

**Where it lives:** In eval mode, read the repro report's environment
record against the issue context and repo-facts block. In live mode,
read the environment section of the student's draft against the issue,
the repository's setup documentation, and the checked-out revision
named in the report.

**What good looks like:** The record identifies the operating system,
relevant runtime and tool versions, dependency state, and configuration
needed to interpret the attempt. It names a branch, tag, or commit when
the revision matters. VM, container, architecture, package-manager, and
cloud details are included when they affect the result. The conditions
match the issue's target, or meaningful differences are disclosed.
Secrets and credentials are never evidence and must not be included.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

**Where it lives:** In eval mode, use the prerequisites, starting state,
commands, inputs, and trigger sequence in the repro report. In live
mode, use the same parts of the student's draft together with the
repository's setup instructions when the draft relies on them.

**What good looks like:** A stranger can start from the stated revision
and environment, perform every material setup and trigger action in
order, and reach the attempted behavior without inventing a command,
input, configuration choice, or transition. Exact repetition counts
are included when frequency or intermittency affects the result;
irrelevant actions do not need to be narrated.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

**Where it lives:** In eval mode, inspect the output excerpts, logs,
screenshots, test results, error messages, and other artifacts included
in or referenced by the repro report, and compare them with the issue
context. In live mode, inspect the corresponding evidence deliberately
included with the student's draft and compare it with the live issue's
expected and observed behavior.

**What good looks like:** The evidence comes from the stated attempt
and directly supports its reported outcome. For a reproduction, it
shows the issue's specific behavior rather than merely some error or a
setup failure. For a cannot-reproduce result, it shows that the intended
trigger ran under the recorded conditions without producing the reported
behavior. The report explains expected versus observed behavior, and
identifying details in the artifact agree with the environment and steps.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

**Where it lives:** In both modes, compare the report's outcome and
explanation with its environment, steps, artifacts, errors, deviations,
and stated limitations. Also compare the repro comment with the full
report so the shorter public summary does not strengthen the claim.

**What good looks like:** The conclusion uses reproduced only when the
target behavior appears, cannot reproduce when the intended trigger
runs without it, and blocked when setup or another failure prevents a
valid attempt. Uncertainty, changed conditions, skipped steps, partial
results, and alternative explanations are disclosed. The wording never
claims more certainty, scope, or causation than the evidence establishes.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

**Where it lives:** In eval mode, read the claim comment and repro
comment against the issue context, repo-facts block, contribution
policy, and any included templates. In live mode, read the student's
drafts against the live issue thread, repository contribution guide,
comment or pull-request templates, and AI-use or disclosure policy.

**What good looks like:** The claim names the chosen issue and the
specific investigation the student will attempt, promises a report,
and does not promise a fix or completion date. The repro comment states
the actual outcome and points to concrete evidence without copying
another contributor's conclusion. Both comments follow repository
conventions and include any required AI-use disclosure. They are
specific enough to be useful without hiding limitations or presenting
boilerplate as evidence.
