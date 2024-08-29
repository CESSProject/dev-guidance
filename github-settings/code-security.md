# Code security and analysis

For important codebases, we should enable some basic options in the 'Code security and analysis' configuration page and handle the alarms according to certain norms unless we have to turn off the code scanning due to privacy concerns.

## Settings

The following settings should be made:

- Enable `Dependabot - Dependabot alerts`
- Enable `Dependabot - Dependabot security updates`
- Configure the maintainers/groups of this repository in `Access to alerts` to ensure that reviewers of the PR can verify during manual handling.

## Handling Dependabot Alerts

[About Dependabot alerts](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)

When a project's dependency library is reported to have a security issue, dependabots will automatically trigger an alert based on the configuration and attempt to generate an `update pull request`.

At the same time, the number of unresolved events will be displayed on the project's `Security` tab.

The maintainers of the codebase must pay attention to the situation regarding `Security` and take action.The following guidelines should be followed during processing:

- Issues classified as `high` or `critical` must be addressed, while others can be handled at discretion.

- For automatically generated `update pull requests`, the maintainer checks the alert information against the update content and merges it after confirming that everything is correct.

- In cases where an `update pull request` cannot be automatically generated, maintainers should manually update it, have it reviewed by others, and merge it after confirming its accuracy.

- For this type of `pull request`, special attention should be paid during the review:

  - Do the updated dependencies and versions match the alarm description?

  - Have the dependency manifest files (go.mod, Cargo.toml) and the dependency lock files (go.sum, Cargo.lock) been changed as necessary?

  If what needs to be updated is not a direct dependency, then the graph file may not need to be updated.
