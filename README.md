# shared-workflows
workflows available to lsd-consulting repositories

## Releases

`release.yml` only releases when the calling workflow was started by hand
(`workflow_dispatch`) or by a schedule. On `push` and `pull_request` the release
job is skipped, so merging to main never publishes to Maven Central. Maven
Central limits the io.github.lsd-consulting namespace to 7 releases a month.

Each library has its own `.github/workflows/release.yml` caller. Release one by hand:

```
gh workflow run release.yml -R lsd-consulting/<repo> -f reason="why this release is needed"
```

A library can opt in to a weekly release (Tuesday 07:00 UTC, only if there are
releasable feat/fix commits) by setting a repository variable:

```
gh variable set WEEKLY_RELEASE --body true -R lsd-consulting/<repo>
```
