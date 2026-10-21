# CI Rehearsal Drill Runbook

This is the runbook for the weekly release drill, staged in the throwaway repository **`mcpmark-eval-liuhezi/ci-rehearsal-lab`**.

The drill workflow lives at **`.github/workflows/rehearse.yml`** in this repository. It is named `CI Rehearsal` and is triggerable only manually (`workflow_dispatch`). When run, it idles for roughly ninety seconds and then prints a completion line.

## Drill steps

1. Confirm the workflow file is present on the default branch (`main`) at `.github/workflows/rehearse.yml`.
2. Verify the commit that added the workflow file also contains the runbook at the repository root.
3. Dispatch a manual run of the `CI Rehearsal` workflow on `main` and note the run id and run number.
4. While the run is still queued or in progress, cancel it. If it completes before cancellation, that is acceptable — record the outcome.
5. Re-run the entire cancelled run and poll until it reaches a final state.
6. Record the observed status and conclusion, and archive the drill log in a shareable gist.

## Notes

- Expected runtime of the workflow is about 90 seconds (the `sleep 90` idle step).
- The drill is repeatable: re-dispatch or re-run at any time from the Actions tab of this repository.
