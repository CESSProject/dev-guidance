# GitHub-actions

In official terms, GitHub-actions is a CI (Continuous Integration) and CD (Continuous Delivery) platform.

More information can be found through the [official documentation](https://docs.github.com/en/actions).

## Why Use It

The benefits of using GitHub-actions include:

1. Nearly seamless integration with code and various workflows, especially in stages that require immediate blocking of subsequent actions.
2. There are a large number of reusable actions pre-packaged by other users.

These benefits lead to a development experience that:

1. Is similar to the CI/CD + pipelines/jobs system provided by self-hosted code hosting platforms like GitLab, primarily reflected in comprehensive workflow/event support;
2. Is slightly better than deeply integrated development toolsets such as GitHub + CircleCI, GitHub + TravisCI, mainly reflected in the additional management of webhooks & GitHub applications;
3. Far exceeds the combination of simple integrations like webhooks + event trigger + jobs/scripts.

It also has some limitations:

1. Quota restrictions.
2. GitHub provides fixed and relatively low-standard hardware for its runner containers.

These limitations mainly manifest in "resource usage," which can be mitigated by using [self-hosted runners](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners).

## How to Use

To enable a new GitHub Action, add a `.yml` configuration file that meets the format requirements to the `.github/workflows` directory at the root of your repository.

The format of the configuration file is referenced in the [GitHub-actions workflow syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions).

### Important Configuration Items

Taking this configuration file as an example:

```yaml
# This is a basic workflow to help you get started with Actions
name: check-rust-on-pr

# Controls when the workflow will run
on:
  pull_request:
    branches: [ main, release/** ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "check"
  check:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2

      - name: dependencies
        run: sudo apt update && sudo apt install --reinstall protobuf-compiler -y

      - name: setup rust
        uses: actions-rs/toolchain@v1
        with:
          profile: minimal
          toolchain: stable
          override: true

      - name: install components
        run: rustup component add --toolchain $(cat rust-toolchain) clippy rustfmt      
```

- `name: check-rust-on-pr`

  The content of this item will determine the name of the action displayed in the GitHub workflow;

  Contrary to intuition, the filename of the configuration file is not used as the action name.

- ```yaml
  on:
    pull_request:
      branches: [ main, release/** ]
  ```

  This item will determine the trigger conditions for the action;

  Here, the sample action will be triggered when a `pull request` is made to the specified branches;

  Common trigger conditions also include `push`, refer to [on](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#on), [triggering workflow events](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows).

- ```yaml
  # A workflow run is made up of one or more jobs that can run sequentially or in parallel
  jobs:
    # This workflow contains a single job called "check"
    check:
  ```

  A sub-task named `check` is defined here, and all configuration items indented deeper are for the `check` sub-task;

  According to the comments, an action can contain multiple sub-tasks, which can be sequential or concurrent.

#### Comparison with Previous Code Platforms + CI Platforms

Comparing with previous CI/CD execution methods, we can see:

1. The `name` is used to describe the purpose of a set of tasks.
2. The `on` is similar to a "trigger mechanism based on webhooks and specific events."
3. The `jobs` are the collection of actions to be executed, which can be further divided into sub-tasks or steps within sub-tasks based on granularity.

In fact, the three-layer structure of `actions - jobs - steps` can often be flexibly divided according to actual situations.

### The important aspects where actions should be enabled include

We believe the following aspects should be focused on:

- For pull requests targeting important branches,

  The following actions should be enabled:

  - Successful compilation
  - Passing tests
  - Code style checks

- For pushes targeting important branches,

  The following actions should be enabled:

  - Successful compilation
  - Compilation result publication

- For creating tags, especially version tags,

  The following actions should be enabled:

  - Successful compilation
  - Compilation result publication

### Tips

- On GitHub, if two jobs are both time-consuming and there are no obvious dependencies between them, such as: the subsequent task depends on the result of the previous task, or the previous task can save a significant amount of time for the subsequent task, then they should be split into two actions to run in parallel.

- In the orchestration of `github-actions`, using `actions/cache` can reduce execution time under certain conditions, which is meaningful both in terms of saving time quotas and shortening the wait for review checks.

  Note:

  1. Caches are generally bound to the dependency list of compilations, such as the `go.sum` for Go projects, the `Cargo.lock` for Rust projects.
  2. In the case of using `actions/cache`, it is generally preferred to merge jobs rather than split them as suggested in the previous tip, to maximize cache reuse and avoid cache misses causing repeated builds.
  3. In Go projects, since the compilation time is already relatively short, the time saved is not significant.

  For further reading:

  - [actions/cache](https://github.com/actions/cache)
  - [Caching Dependencies to Speed Up Workflows](https://docs.github.com/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows)
  - [How I speeded up my Rust builds on GitHub ~30 times](https://ectobit.com/blog/speed-up-github-actions-rust-pipelines/)