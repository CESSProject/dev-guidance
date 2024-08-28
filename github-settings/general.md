# General

## Pull Request Merge Form

Must be enabled:

- `Allow merge commits`: merge the changes from the commits in `merge` form.

The other two types of merge form are optional:

- `Allow squash merging` which means integrating all commits from a pull request into a single new commit with a combined commit message, and then merging it into the target branch, helps maintain a clean commit history.
- `Allow rebase merging` which means merging all commits from a pull request onto the target branch in a way similar to rebase, which helps maintain a linear commit history.
The commonality between these two forms of merging is that they will no longer keep the commits in the target branch strictly consistent with those in the source branch (in terms of content, commit IDs), and therefore, they are only recommended for teams with a sufficiently deep understanding of `Git` mechanisms.


## Others

Must be enabled:

- `Automatically delete head branches`, which means that after merging PR, the source branches are automatically deleted, which can help clean up the branches that are no longer needed in the code repository.
