# Branch Protection Rules

`Branch protection rules` are a crucial feature provided by GitHub to prevent important branches from being easily polluted or deleted. They are located in the `Settings\Branches` panel.
For repositories where protection rules can be set (currently known that private repositories in non-paying teams cannot set them), we must configure these to reduce the likelihood of accidental operations on important branches.

## Protected Branches

When a branch fits the definition of a "long-term maintained collaborative branch," it should be designated as a protected branch. Specifically:

- The maintenance period is relatively long (spanning several Sprints, a version, or a Milestone).
- It accepts merge requests from developers at different times.
In practice, we typically list the following branches as protected:
- The general main branches, such as `master`, `develop`, etc. Most changes converge to these branches.
- Branches for specific versions, such as `stable2408`, `release/v1.15.x`, etc. All changes during the lifecycle of the version, from pre-release to end of maintenance, converge to these branches.
- Other branches that meet the definition.

## List of Protection Rules

The following rules must be enabled:

- `Require a pull request before merging`
  This means changes must be submitted to the target branch via a `pull request`.
  - `Require approvals` & `Required number of approvals before merging: 1`
  This means at least one reviewer's approval is required.
  - `Dismiss stale pull request approvals when new commits are pushed`
  This means new commits will reset the review status.

- `Require status checks to pass before merging`
  This means all set checks must pass before merging.

- `Require conversation resolution before merging`
  This means all conversations must be marked as "resolved" before merging.

The following rules must be disabled:

- Under `Rules applied to everyone including administrators`:
  - `Allow force pushes`
    This means all users with `push` permissions are allowed to force push to the protected branch.
  - `Allow deletions`
    This means all users with `push` permissions are allowed to delete the protected branch.
