# Run GitHub Actions from Command Line with gh

Prerequisites:
1. [gh auth](gh-auth.md#gh%20auth)
2. The workflow must support `workflow_dispatch`[^1].


```
gh workflow run
```

When no parameters are passed, it will let me select a workflow to run from the default branch from a list of all workflows in the GitHub repository.
Then if the workflow has any inputs, it will prompt for it. Though the `description` is not displayed, so hopefully the input name was meaningful.

```
? Select a workflow  [Use arrows to move, type to filter]
> Unit Tests (unit_tests.yml)
  pages-build-deployment (pages-build-deployment)
  Deploy Jekyll with GitHub Pages dependencies preinstalled (jekyll-gh-pages.yml)
  Checks (checks.yml)
  .github/workflows/record_screenshots.yml (record_screenshots.yml)
  record-snapshot-command (record-snapshot-command.yml)
  Slash Command Dispatch (slash-command-dispatch.yml)
  Publish beta build (publish-beta.yml)
  Publish production build (publish-production.yml)
  Create issue from TODO comments (create-issue-from-todo.yml)
  Update compose compiler report (update-compose-compiler-report.yml)
  Nightly chores (nightly-chores.yml)
```


[^1]: https://cli.github.com/manual/gh_workflow_run