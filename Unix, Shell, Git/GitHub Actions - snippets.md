# GitHub Actions
## Cancel all in-progress runs on push
### Description/Scenario
This snippet is intended to garbage-collect pipeline executions whenever a newer commit becomes available in a branch.

Example using the following case:

1. Make a change, create/amend commit, push to branch
2. Pipeline fires, creating long-running job #1
3. Make a change, create/amend commit, push to branch
4. Pipeline fires, creating long-running job #2
5. Make a change, create/amend commit, push to branch
6. Pipeline fires, creating long-running job #3

If this snippet is in place, job #1 gets cancelled during step 4, and job #2 gets cancelled during step 6. This leaves job #3 running, which means that the job runner does not waste time running the pipeline for repository commits that are outdated and superseded by changes that came in after.

### Snippet
```yaml
concurrency:
  group: ${{ github.workflow }}-${{ github.event.pull_request.number || github.ref }}
  cancel-in-progress: true
```
