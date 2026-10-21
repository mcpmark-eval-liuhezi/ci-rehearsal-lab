# CI Rehearsal Drill Log

> **Note:** This log was intended to be a secret gist named `rehearsal-log.md` with description
> "CI rehearsal log - ci-rehearsal-lab", but the API token in use does not have permission to
> create gists (403 Resource not accessible). As a fallback, it is committed to the repository
> instead so it remains a shareable record.

## Summary

A full CI release-drill rehearsal was staged in a throwaway repository, exercising the
manual-dispatch → cancel → re-run loop that our weekly release drills require.

## Repository

- **Repository full name:** `mcpmark-eval-liuhezi/ci-rehearsal-lab`
- **Visibility:** public
- **Default branch:** `main`
- **Workflow file path:** `.github/workflows/rehearse.yml`
- **Workflow name:** CI Rehearsal
- **Trigger:** `workflow_dispatch` only (manual)
- **Job:** single job (`rehearse`) that sleeps ~90 seconds and then prints a completion line
- **Runbook:** `RUNBOOK.md` at the repository root

## Commit that added the workflow file

- **SHA:** `a7a65a04c88d3ef0a3d80326f709e82dc38da6b9`
- **Message:** `Add CI Rehearsal workflow and drill runbook`
- Both paths were confirmed present in that commit:
  - `.github/workflows/rehearse.yml` (added, 13 lines)
  - `RUNBOOK.md` (added, 19 lines)

## Dispatched run

- **Run id:** `39553163556`
- **Run number:** `1`
- **Event:** `workflow_dispatch` on `main`
- **Workflow id:** `391356669`

### State after the cancellation attempt

The run was cancelled while it was in progress:

- Cancellation request returned HTTP `202 Accepted` ("Workflow run has been cancelled").
- Immediately after, the run briefly still reported `in_progress` while the
  cancellation propagated.
- Final observed state: **status `completed`, conclusion `cancelled`**
  (the `sleep 90` idle step was interrupted at ~87s; the completion echo step
  was marked `skipped`).

## Re-run

- The entire run was re-run (**run attempt 2**, same run id `39553163556`, run number `1`).
- Final state of the re-run: **status `completed`, conclusion `success`**
- Re-run start: `2026-10-21T06:26:09Z`, completed: `2026-10-21T06:27:47Z` (~98s wall clock).

## Notes

- Note on placement: the token in use was not permitted to create the repository under
  the personal account (`HeziLiu`), so the lab was created in the accessible
  organization `mcpmark-eval-liuhezi` instead.
- Repository: https://github.com/mcpmark-eval-liuhezi/ci-rehearsal-lab
- Run: https://github.com/mcpmark-eval-liuhezi/ci-rehearsal-lab/actions/runs/39553163556
- Commit: https://github.com/mcpmark-eval-liuhezi/ci-rehearsal-lab/commit/a7a65a04c88d3ef0a3d80326f709e82dc38da6b9
