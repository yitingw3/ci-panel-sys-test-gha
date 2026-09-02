# ci-panel-sys-test-gha

Test repository for CI Panel system tests. Contains GitHub Actions workflows used to validate CI Panel's GitHub Actions integration.

**Do not modify workflows without coordinating with CI Panel test owners** — system tests depend on specific workflow names, job names, and artifact outputs.

## Workflows

| Workflow | Trigger | Jobs | Artifacts | Purpose |
|----------|---------|------|-----------|---------|
| CI | push, PR, manual | build → test, lint | build-output, test-report | Main workflow: multi-job with dependencies, multiple artifacts |
| Manual Trigger | manual only | execute | run-summary | Controllable pass/fail via `should_fail` input |
| Multi-Job Pipeline | push (main), manual | setup → job-a + job-b → finalize | pipeline-result | Fan-out/fan-in job dependency graph |

## Branches

| Branch | Purpose |
|--------|---------|
| main | Default branch, all workflows run here |
| feature-branch | Secondary branch for testing branch filtering |

## Test Coverage

This repo supports the following CI Panel test scenarios:

- **Authenticate and validate project** — repo exists, token has access
- **Fetch full pipeline tree** — 3 workflows, multiple jobs per workflow, artifacts
- **Download artifact** — build-output, test-report, run-summary, pipeline-result
- **Download logs** — any completed run has downloadable logs
- **Trigger workflow** — Manual Trigger workflow via `workflow_dispatch`
- **Branch filtering** — runs exist on both main and feature-branch
- **Status filtering** — Manual Trigger can produce both SUCCESS and FAILURE
- **Job hierarchy** — CI has 3 jobs (build→test, lint); Multi-Job has 4 jobs (setup→a+b→finalize)
