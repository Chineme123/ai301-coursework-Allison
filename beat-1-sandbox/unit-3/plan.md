# Plan: surface failed tool calls in review output

## Diagnosis

The failure is in the handoff from orchestration to review generation,
not in the tool executor. `Orchestrator.run` already records a failed
tool call in `agent_output["tool_results"]` as a dictionary containing
the error text and `success: false`. The reproduction confirmed that
with:

> `"failed_tool_result": {"error": "forced tool failure for issue 16 reproduction", "success": false}`

The same run showed:

> `"review_output_contains_failure": false`

`process_review` passes `agent_output` to
`_run_rag_retrieval_generation`, but that function currently returns a
hardcoded review dictionary without reading `agent_output`. I therefore
believe the failed result is lost when the review output is assembled.
The intended wording and grouping of multiple failures are not defined
by the issue, so those presentation details remain an implementation
choice.

## Scope

### In scope

- `core/services/review_service.py`: inspect `agent_output["tool_results"]`
  during review generation and add user-visible review content for tool
  results whose recorded value has `success: false` and an error.
- `tests/unit/test_review_service.py`: add automated coverage that
  forces a failed tool result through the review-generation function
  and verifies that the review output contains the tool name and error.

### Out of scope

- Changes to tool execution, retries, caching, or failure capture in
  `agent/orchestrator.py`; that layer already records the failure.
- Implementing the unfinished RAG retrieval or LLM generation pipeline.
- Changing database models, API response schemas, frontend rendering,
  successful tool-result presentation, or unrelated review sections.

## Approach

1. Read `tool_results` from the `agent_output` already passed into
   `_run_rag_retrieval_generation`, treating a missing or non-dictionary
   value as having no reportable failures.
2. Select only entries explicitly recorded as unsuccessful and carrying
   an error. Preserve the existing tool name and recorded error, without
   exposing a traceback or inventing diagnostic details.
3. Convert the collected failures into a user-visible review section and
   append it to the existing generated sections. Keep the existing
   sections and overall score unchanged.
4. Keep the no-failure path behaviorally unchanged so successful reviews
   do not gain an empty failure section.
5. Add focused unit tests for the failed-result and no-failure paths.

## Test plan

The implementation agent is explicitly permitted and expected to create
automated pytest tests in `tests/unit/test_review_service.py` for this
fix.

1. Add an asynchronous unit test that passes an `agent_output` containing
   a failed `github_tool` result into `_run_rag_retrieval_generation`.
   Assert that the returned review sections include the tool name and the
   exact forced error message.
2. Add a control test with only a successful tool result. Assert that the
   existing review sections and overall score remain and that no tool
   failure section is added.
3. Run the focused tests with:

   ```bash
   .venv/bin/pytest tests/unit/test_review_service.py -q
   ```

4. Re-run the Unit 2 reproduction script. Before the fix it reports
   `review_output_contains_failure: false`; after the fix it must report
   `review_output_contains_failure: true`. The successful control is not
   expected to appear because successful-result presentation is outside
   this issue's scope.
5. Run the complete unit suite with:

   ```bash
   .venv/bin/pytest tests/unit -q
   ```

## Risks and unknowns

- Multiple tools may fail in one run. The output must retain each failed
  tool's identity without overwriting another failure.
- Tool error strings may contain internal details. This change should
  expose only the error value already recorded by the orchestrator, not a
  traceback or additional runtime context.
- The review generator is currently a placeholder. The failure-section
  assembly should stay isolated enough to survive later replacement of
  the hardcoded review content.
- The issue does not specify exact user-facing copy, so tests should
  verify the failure information rather than brittle prose formatting.

## Deviations

None in scope or approach. The build changed only the two files listed
under "In scope" and followed the five approach steps as written.
Nothing in `agent/orchestrator.py`, the RAG pipeline, schemas, or
successful-result presentation was changed.

Details the plan left open, recorded here for the reviewer:

- Failures are grouped into a single section named "Tool Failures",
  appended after the existing three sections. Its content opens with
  one sentence noting the review may be incomplete, followed by one
  `tool_name: error` line per failed tool, so multiple failures are all
  retained.
- The section uses `confidence: 1.0` (the failure is a recorded fact,
  not an inference) and an empty `suggestions` list, so no advice is
  invented.
- The assembly lives in a separate helper, `_build_tool_failure_section`,
  so it can survive replacement of the placeholder review content. In
  addition to a missing or non-dictionary `tool_results`, it also treats
  a non-dictionary `agent_output` as having no reportable failures.

Verification beyond the test plan (no code impact):

- The new failure test was run against the pre-fix `review_service.py`
  and failed as expected; the control test passed both before and after.
- A two-failure `agent_output` was checked end to end: the output passes
  `_run_safety_checks`, the new section validates as `FeedbackSection`,
  and `overall_score` stays at 0.81.
- `ruff check` and `ruff format --check` pass on both changed files.

Results: focused tests 8 passed, 13 xfailed (was 6 passed, 13 xfailed);
`tests/unit` 377 passed, 53 xfailed, 0 failed; the Unit 2 reproduction
now reports `review_output_contains_failure: true` (was `false`) and
`review_output_contains_control: false`, as expected.
