# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/16

**Verdict output**

I now have all the evidence. Today is 2026-09-20. Summary of findings:

Repo-level (applies to all three):

- Not archived; last push 2026-09-16 (4 days ago) → Repository active PASS, Recently active PASS
- Last 5 default-branch commits all by Aburke225 (Andrew Burke, non-bot human), latest 2026-09-16 → Maintainer active PASS
- docs/CONTRIBUTING.md + PR template exist; no AI ban (course repo expects AI-assisted work; silence passes) → AI contribution allowed PASS
- Sampled open issues: only student (NONE association) comments, no Owner/Member/Collaborator replies → Maintainer responsive FAIL (preferred)
- No merged non-member PRs (fresh course repo) → Established contributor community UNCLEAR (preferred)

Per-issue: none have assignees, linked PRs, cross-referenced PRs, or comments. Path Review house rule waives student claim signals anyway → Issue available PASS for all three.

---

Ranked read-out

All three accepted (every required check passes on each). Ranked by preferred-check passes, then fit:

1. #64 — Relevance scorer "partial overlap" test fixture — 2 preferred passes (Recently active + Newcomer signal: carries good first issue + tier-1). Scope-risk 1: single clear fixture fix, settled direction. Top-ranked purely on preferred passes.
2. #16 — Failed tool calls never reach review output — 1 preferred pass. Scope-risk 2: one clear outcome, names both files (agent/orchestrator.py, core/services/review_service.py), 4–6h. Beats #71 on fit: backend, feature-flavored work — the student's stated top preference.
3. #71 — Heading hierarchy test fixture is indented — 1 preferred pass. Scope-risk 1: remove indentation + xfail marker. Loses the tiebreak to #16 because it is a test fix (student's lowest work-type preference).

Rejected: none.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/64",
    "checks": [
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template state no AI ban; course repo expects AI-assisted work, silence passes"},
      {"name": "Repository active", "grade": "pass", "evidence": "isArchived=false; last push 2026-09-16, 4 days before today (within 100)"},
      {"name": "Recently active", "grade": "pass", "evidence": "last push 2026-09-16, 4 days before today (within 65)"},
      {"name": "Issue available", "grade": "pass", "evidence": "no assignee, no linked/cross-referenced PR, 0 comments; house rule waives student claims"},
      {"name": "Bounded and actionable scope", "grade": "pass", "evidence": "scope-risk 1: single fixture fix with settled direction and reproduce command"},
      {"name": "Maintainer active", "grade": "pass", "evidence": "last 5 default-branch commits by non-bot Aburke225, latest 2026-09-16 (within 100 days)"},
      {"name": "Maintainer responsive", "grade": "fail", "evidence": "sampled open issues show only NONE-association student comments, no maintainer replies"},
      {"name": "Established contributor community", "grade": "unclear", "evidence": "no merged non-member PRs in fresh course repo; evidence unavailable"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "labels include 'good first issue' and 'tier-1' (Starter difficulty)"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/16",
    "checks": [
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template state no AI ban; silence passes"},
      {"name": "Repository active", "grade": "pass", "evidence": "isArchived=false; last push 2026-09-16, 4 days before today (within 100)"},
      {"name": "Recently active", "grade": "pass", "evidence": "last push 2026-09-16, 4 days before today (within 65)"},
      {"name": "Issue available", "grade": "pass", "evidence": "no assignee, no linked/cross-referenced PR, 0 comments; house rule waives student claims"},
      {"name": "Bounded and actionable scope", "grade": "pass", "evidence": "scope-risk 2: one clear outcome, names both relevant files, 4-6h estimate, no blocking questions"},
      {"name": "Maintainer active", "grade": "pass", "evidence": "last 5 default-branch commits by non-bot Aburke225, latest 2026-09-16 (within 100 days)"},
      {"name": "Maintainer responsive", "grade": "fail", "evidence": "sampled open issues show only NONE-association student comments, no maintainer replies"},
      {"name": "Established contributor community", "grade": "unclear", "evidence": "no merged non-member PRs in fresh course repo; evidence unavailable"},
      {"name": "Newcomer signal", "grade": "fail", "evidence": "labels are bug/agent/tier-2 (Intermediate); no good-first-issue or equivalent"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71",
    "checks": [
      {"name": "AI contribution allowed", "grade": "pass", "evidence": "docs/CONTRIBUTING.md and PR template state no AI ban; silence passes"},
      {"name": "Repository active", "grade": "pass", "evidence": "isArchived=false; last push 2026-09-16, 4 days before today (within 100)"},
      {"name": "Recently active", "grade": "pass", "evidence": "last push 2026-09-16, 4 days before today (within 65)"},
      {"name": "Issue available", "grade": "pass", "evidence": "no assignee, no linked/cross-referenced PR, 0 comments; house rule waives student claims"},
      {"name": "Bounded and actionable scope", "grade": "pass", "evidence": "scope-risk 1: remove fixture indentation and xfail marker, settled direction, names both files"},
      {"name": "Maintainer active", "grade": "pass", "evidence": "last 5 default-branch commits by non-bot Aburke225, latest 2026-09-16 (within 100 days)"},
      {"name": "Maintainer responsive", "grade": "fail", "evidence": "sampled open issues show only NONE-association student comments, no maintainer replies"},
      {"name": "Established contributor community", "grade": "unclear", "evidence": "no merged non-member PRs in fresh course repo; evidence unavailable"},
      {"name": "Newcomer signal", "grade": "fail", "evidence": "labels are bug/ingestion/tier-2 (Intermediate); no good-first-issue or equivalent"}
    ],
    "verdict": "accept"
  }
]
```

## Eval iterations

**Run history**

1. `agreement: 2/3 scored items` — Initial smoke test. Issue #1 was incorrectly rejected by the required Maintainer responsive check.
2. `agreement: 3/3 scored items` — Smoke test after separating relaxed maintainer activity from preferred responsiveness.
3. `agreement: 17/20 scored items` — First full run. The three misses were all in the scope category.
4. `agreement: 3/3 scored items` — Targeted scope rerun after adding the first Bounded and actionable scope check.
5. `agreement: 17/20 scored items` — Full regression run. The first scope wording fixed the original misses but falsely rejected three clear accepts.
6. `agreement: 5/6 scored items` — Six-case scope regression after replacing the long rule with a 1–5 scope-risk scale.
7. `agreement: 19/20 scored items  (bar: 18/20: PASS)` — Full run with the final rubric.
8. `agreement: 19/20 scored items  (bar: 18/20: PASS)` — Final saved run recorded in `eval-run.txt`.

**Issue analysis**

For `issue-19`, the saved run says: `issue-19  accept  reject   NO     failed: Bounded and actionable scope, Maintainer responsive (preferred), Established contributor community (preferred), Newcomer signal (preferred)`. My rubric therefore decided `reject`, while the gold label was `accept`. The scope check's evidence was: `Scope-risk 4: body lists two unresolved causes 'which should be fixed' plus three separate additional architectural suggestions (multiprocessing, selective matching, threaded rewrite application), with no comment thread narrowing what is actually required`. The other failed checks were preferred and could not cause rejection. The instructor treated the named performance outcome as clear enough even though the implementation path remained open; my rubric treated that open path as higher first-contribution risk.

**Check rationale**

Current wording from my uploaded `rubric.md`:

> **Check:** Bounded and actionable scope  
> **Evidence:** The issue title and body, the full comment thread, and closed-unmerged pull requests that show prior attempts; in eval mode, use the Issue and Comments sections and closed PRs in `linked PRs:`.  
> Assign a scope-risk score from 1 to 5. Score 1 for one clear task with settled direction; 2 for minor unanswered details that do not block starting; 3 for several steps or questions with one understandable outcome; 4 for major unresolved requirements, conflicting direction, or repeated abandoned attempts whose blocker remains; and 5 for an umbrella collection or discussion too fragmented to identify one contribution. Pass for scores 1 through 3; fail for scores 4 or 5. Include the score and the evidence supporting it in the check output.
> **Weight:** required

I chose an anchored scale because my earlier wording was too granular and overfit to individual evaluation examples. The scale lets the model make a natural-language judgment while still explaining what each score means and where the pass boundary is. It also reflects what I need from a first contribution: I want the expected outcome and direction to be straightforward enough that I can focus on implementation instead of first sorting through competing possibilities. A higher scope-risk score does not mean an issue is objectively bad; it means the issue carries more ambiguity than I personally want for this first project.

**Trade-offs**

This check gives up some recall for issues with a clear goal but several unresolved implementation paths. The six-case canary rerun scored `5/6`: it preserved the original three scope rejections and two clear accepts, but still rejected `issue-19`. I understand why the instructor accepted that issue: it has a clear performance goal even though several possible causes and approaches remain open. My rubric filters it out because I prefer something more direct and mentally manageable for a first contribution, where I can make implementation decisions without first untangling several possible directions. I accepted that trade-off rather than continuing to tune the wording to the answer key because the final rubric still passed at `19/20` and matched every category.

## Selection rationale

**Selection rationale**

1. Issue #16 fits my interests because it is backend, agent-related work rather than a test-only task. It traces failed tool-call data between `agent/orchestrator.py` and `core/services/review_service.py`, and the four-to-six-hour estimate feels manageable for the available time.
2. The verdict correctly identified that the issue is unclaimed, the repository is active, AI-assisted contribution is allowed, and the work has one clear outcome with a scope-risk score of 2. The rubric could not fully weigh my preference for backend feature-like work: issue #64 ranked higher on preferred checks, but issue #16 is a better personal learning fit.
3. Claiming may be moderately difficult because the issue is tier 2 and lacks a good-first-issue label, so I expect more code tracing than the two fixture fixes. However, it has no assignee, linked pull request, or blocking discussion, and the Path Review house rules mean other student claim comments would not prevent me from choosing it.
