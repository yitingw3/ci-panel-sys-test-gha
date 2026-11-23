# ci-panel-sys-test-gha

A test repository for CI Panel. It contains sample GitHub Actions workflows that exercise common CI scenarios.

## Workflows

| Workflow | Trigger | Description |
|----------|---------|-------------|
| CI | push, pull request, manual | Build, test, and lint jobs with artifacts |
| Manual Trigger | manual | Single job that can be set to pass or fail through an input |
| Multi-Job Pipeline | push, manual | Fan-out/fan-in job dependencies |
| Weekly Refresh | weekly schedule, manual | Produces a fresh artifact each week |
| Failing Pipeline | manual | Intentionally fails; includes passing, failing, and skipped jobs |

## Branches

- `main`: default branch
- `feature`: secondary branch
