# Run GitHub Actions from Command Line with gh

Prerequisites:
1. [gh auth](gh-auth.md#gh%20auth)
2. The workflow must support `workflow_dispatch`[^1].


```
gh workflow run
```

When no parameters are passed, it will let me select a workflow to run from the default branch from a list of all workflows in the GitHub repository.
Then if the workflow has any inputs, it will prompt for it. Though the `description` is not displayed, so hopefully the input name was meaningful.

Here's an example running this in the root of [https://github.com/lydavid/MusicSearch](https://github.com/lydavid/MusicSearch):

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

```
? Select a workflow Update compose compiler report (update-compose-compiler-report.yml)
✓ Created workflow_dispatch event for update-compose-compiler-report.yml at beta
```

Then to find the run:

```
gh run list
```

```
STATUS  TITLE                                                                   WORKFLOW                        BRANCH                        EVENT              ID          ELAPSED  AGE
*       Update compose compiler report                                          Update compose compiler report  beta                          workflow_dispatch  8127058133  10s      0m 
X       chore(deps): update androidgradleplugin to v8.3.0                       Checks                          renovate/androidgradleplugin  push               8121357639  2m16s    18h
```

To monitor the run:

```
gh run watch 8127058133
```

```
* update-compose-compiler-report (ID 22211469825)
  ✓ Set up job
  ✓ Checkout
  ✓ Setup gradle
  ✓ Setup Node.js
  ✓ Run npm install -g compose-report2html
  ✓ Write to keystore.properties
  ✓ Convert base64 to files
  * Assemble apk with compose compiler reports enabled
  * Generate HTML from compose reports
  * Move the compose reports and HTML file to each module's root
  * Commit version code bump
  * Post Setup Node.js
  * Post Setup gradle
  * Post Checkout
```


[^1]: https://cli.github.com/manual/gh_workflow_run