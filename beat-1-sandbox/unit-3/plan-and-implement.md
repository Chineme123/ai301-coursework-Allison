# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

## Posted upstream

**GitHub username**

Chineme123

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/16#issuecomment-6001850748

Hi, I reproduced the missing failure handoff and traced it to review
generation. `Orchestrator.run` records the failed tool result correctly,
but `_run_rag_retrieval_generation` does not read `agent_output`, so the
failure never reaches the returned review sections.

I plan to update `core/services/review_service.py` to add a user-visible
review section for tool results explicitly recorded as failed, while
leaving successful-result presentation and the broader RAG implementation
out of scope. I will add focused pytest coverage in
`tests/unit/test_review_service.py`, then rerun the Unit 2 reproduction to
confirm the failure changes from absent to present in the review output.

I haven't heard back on which handoff you intend, so I'm starting with
the smallest change in `review_service.py`. I'm happy to redirect if a
later generation step should own this instead.

## Your branch

**Branch**

`fix/16-tool-failure-review-output`

**Evidence**

The same reproduction command was run before and after the change:

```bash
.venv/bin/python - <<'PY'
import asyncio
import json
from types import SimpleNamespace

from agent.orchestrator import Orchestrator
from agent.tools.base import ToolResult
from core.services.review_service import _run_rag_retrieval_generation

class FailingGitHubTool:
    name = "github_tool"

    def execute(self, input_data):
        raise RuntimeError("forced tool failure for issue 16 reproduction")

class SuccessfulMarketAnalyzer:
    name = "market_analyzer"

    def execute(self, input_data):
        return ToolResult(success=True, data={"status": "control succeeded"})

tools = {
    "github_tool": FailingGitHubTool(),
    "market_analyzer": SuccessfulMarketAnalyzer(),
}
profile_data = {
    "github_username": "repro-user",
    "projects": [{"github_repo": "example/repo"}],
}

agent_output = Orchestrator(tools).run("issue-16-repro", profile_data)
review_output = asyncio.run(
    _run_rag_retrieval_generation(SimpleNamespace(), [], agent_output)
)
encoded_review = json.dumps(review_output)

print(json.dumps({
    "failed_tool_result": agent_output["tool_results"]["github_tool"],
    "control_tool_result": agent_output["tool_results"]["market_analyzer"],
    "review_output_contains_failure": (
        "forced tool failure for issue 16 reproduction" in encoded_review
    ),
    "review_output_contains_control": "control succeeded" in encoded_review,
    "review_output_keys": sorted(review_output.keys()),
}, indent=2))
PY
```

Before the fix:

```json
{
  "failed_tool_result": {
    "error": "forced tool failure for issue 16 reproduction",
    "success": false
  },
  "control_tool_result": {
    "status": "control succeeded"
  },
  "review_output_contains_failure": false,
  "review_output_contains_control": false,
  "review_output_keys": [
    "overall_score",
    "sections"
  ]
}
```

After the fix:

```json
{
  "failed_tool_result": {
    "error": "forced tool failure for issue 16 reproduction",
    "success": false
  },
  "control_tool_result": {
    "status": "control succeeded"
  },
  "review_output_contains_failure": true,
  "review_output_contains_control": false,
  "review_output_keys": [
    "overall_score",
    "sections"
  ]
}
```

Focused verification: `8 passed, 13 xfailed`. Full unit suite:
`377 passed, 53 xfailed, 0 failed`. Ruff lint and format checks passed.

## Eval iterations

**Run history**

1. Full saved run: 19/20 agreement. Every category had at least one
   match, and this score matches the submitted `eval-run.txt`.

**Package analysis**

I analyzed `pkg-14`. The gold label was `accept`, while my rubric
returned `reject`. Its diagnosis was well grounded, but it named only
the `zellij-server` and `zellij-client` areas and said the exact files
and functions would be identified later. That failed my required
explicit-scope check. It also proposed a manual five-cycle reproduction
loop without either supplying an automated test script or explicitly
authorizing the implementing agent to create an automated test, so it
failed my required automated-test-path check.

**Check rationale**

> | Automated test path | The plan's test-plan instructions and any automated test script or test code included or referenced there. | Pass if the test plan either explicitly directs or permits the implementing agent to create an automated test for the fix, or already provides a concrete automated test script for the fix. Fail if neither an explicit instruction to create the test nor an automated test script is present. | required |

I made this check required because I wanted every accepted plan to give
the implementation agent an unambiguous automated verification path.
A plan may provide the test directly or leave its exact implementation
to the agent, but it cannot rely only on an unstated assumption that a
test will be created.

**Trade-offs**

This strict rule rejected `pkg-14` even though the instructor accepted
it. Its repeated manual reproduction loop could provide useful evidence,
but my rubric gives up that flexibility in exchange for requiring an
automated regression check. I accept that disagreement because the final
run still reached 19/20 and matched every category, and the stricter rule
fits how I want a plan to guide implementation.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; the
skill's files are in `tools/plan-check/`.
