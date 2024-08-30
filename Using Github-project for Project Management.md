# Using Github-project for Project Management

## Background

In order to enable the team to communicate better with the community regarding development intentions, design, and processes, as well as to share ideas and thoughts with the community.The `CESS` team uses `GitHub Projects` as an aid for project management.Try to make most development matters into "issues" and reflect them in the project.

## Github Project

### Github Issue

"Github issues" serve as the core of project management.Below is a list of items that can create an `issue` in the format of `issue name: issue content`:

- `Sprint XX`: The goals included in a certain `Sprint`.Each goal will be listed in the form of a `task list` before the `sprint` planning meeting for the team to discuss during the planning session.[cess-xxx] release vX.Y.Z: The `CESS` component has released a new version.
- `[cess-xxx] fix/add/update xxx feature`: A development task for a certain component that can be completed with a single `PR`.A development task can be a `bug`, a new `feature`, an optimization, and so on.
- `[cess-docs] xxx document`: Tasks related to the writing of `cess-docs` or documentation for a specific component.

### Github Issue Label

The `label` plays a significant role in helping to classify/statistics on `issues`.In order for the team to use `labels` more effectively, their settings should not be overly complicated.Below is a list of commonly used `labels` in the format of `label name: label meaning`:

It seems like you've entered a code or a tag. Could you please provide more context or clarify what you would like to discuss? This `label` indicates that the `issue` is a `bug`.

- `c:enhancement`: This `label` indicates that the `issue` is an `enhancement`, which can be a new feature or an improvement to an existing feature.
- `c:docs`: This `label` refers to issues related to the documentation.
It seems like you've entered a command or code snippet. Could you please provide more context or clarify what you would like to know? This `label` refers to an `issue` as a test case/requirement.
- `community`: This `label` indicates that the `issue` comes from the community.
- `epic`: This `label` refers to an `issue` that is a relatively large goal, and its completion may encompass multiple `issues`.
- `design`: This `label` refers to issues related to design.
- `P0`, `P1`, `P2`: This `label` refers to the priority of the `issue`.`P0` has the highest priority.

### Github Issue Projects

An `issue` can not only be labeled but also assigned to its respective `projects`, facilitating visual management.

### Github Issue Assignees

Through `assign`, you can assign an `issue` to a designated person, facilitating the visual management of task executors in a `GitHub project`.It also facilitates internal collaboration within the team.

## Issue Submission Process

1. When submitting a new issue, you can refer to the types of `github issues` mentioned above. Example：

    ```plain text
    Sprint 50
    [cess-node] release v3.0.0
    [cess-node] fix retrieval polling panic bug
    ```

2. According to the prompts of the `issue` template, add the necessary description for the `issue`.
3. Add the corresponding `label` for the `issue`.The explanation of `label` can be found in the above `Github Issue Label` section.
4. Add the corresponding `projects` to the `issue`, and click on `+1 more` to assign the `sprint` for that `issue`.

## PR Submission Process

1. Name the `PR` according to the naming conventions specified for `PR`. Example：

    ```plain text
    feat: api: add xxx
    refactor: rename xxx
    chore: remove xxx log
    ```

2. The `PR` description uses GitHub keywords such as `resolve`, `close`, and `fix` to link to the relevant `issue`. Example： `Fix #168`

3. Add the `projects` corresponding to the `PR`, and click on `+1 more` to assign the `sprint` for that `PR`.

## Introduction to the Github Project Panel

### Introduction to Different Views

- `Backlog`: A collection of all `issues` that do not have a defined `sprint`.It can be understood as the current pool of `issues` that need to be completed.Before each sprint planning meeting, the development team needs to review each issue and select issues to include in the new sprint development plan.If you have any questions, we can discuss them together in the planning meeting.
- `Current Sprint: Added to the list view of all issues in the current sprint.It is convenient to visually see which R&D has been assigned to which issues.
- `Last Sprint`: Added to the list view of all issues from the last sprint.It is convenient to visually check the task completion status of the last sprint.
- `Next Sprint`: Added to the list view of all `issues` for the next `sprint`.

### Status Column

The current status of the Github Project includes:

- `No Status`: When an `issue` is newly added to `projects`, it will automatically be assigned to the `No Status` state.
- `In Progress`: Limited by the relatively basic conditions for automated status transitions in the current `github project`.The `issue` needs to be manually dragged from `No Status` to `In Progress` for the time being.
- `In Review`: When a `PR` is added to a project or is requested to have `review:changes_requested`, this `PR` will automatically transition to the `In Review` status.
- `Reviewed`: When a `PR` is `review:approved`, it will automatically transition to the `Reviewed` status.
- `Done`: When a `PR` is merged and the description of that `PR` correctly uses GitHub keywords such as `resolve`, `close`, `fix`, etc., to link to the related `issue`, both the `issue` and the `PR` will automatically transition to the `Done` status.

### Sprint Column/Section

`Sprint` defines the `sprint` corresponding to the `issue`.When an `issue` is not defined with a `sprint`, by default, these `issues` will exist in the `Backlog`. Before each `sprint planning meeting`, the team needs to organize them and consider whether to include them in the `sprint` development plan.After defining the `sprint`, the `issue` will appear in the `cess project`, within the corresponding `sprint view`, making it easier for visual management.

## Project Management Process

With the correct settings in GitHub Projects, and with `issues` and various component `PRs` submitted correctly and according to standards, the management of the project can achieve good results in terms of openness and visualization.

### Sprint Start

Before holding the Sprint planning meeting, based on the Sprint theme derived from the summary meeting, the Milestone plan, and the quarterly goals, each person should select or create issues as needed in the GitHub Projects Sprint board.And choose the appropriate `assignee`.Adhere to the `SMART` principles of `Sprint` development.
During the planning meeting, we need to discuss and analyze each issue on the `Sprint` board of `GitHub Projects` one by one, explaining the reasons for selecting each issue for this iteration.Let's decide together on the feature set for this Sprint.

### Sprint in Progress

- During the `Sprint`, if there is a need to modify or supplement an `issue` while expanding the objectives, adjustments can be made as necessary, and the `GitHub Projects` board should be updated accordingly.
If there is an unexpected issue that needs to be addressed during the Sprint, the Sprint goals can be appropriately adjusted, and the Sprint issues need to be updated accordingly.The `issue` status has changed, and the board status needs to be updated accordingly. It is recommended to update it before the morning meeting; those who haven't updated it should do so during the meeting.

### Sprint Completed

- Before the summary meeting, it is necessary to synchronize and update the issue status on the board, including the completion percentage and other information in the `Remarks` column.
- During the `Sprint` summary meeting, evaluate the completion of each goal for the current `Sprint` and summarize using the agile methods of `KISS`, while also recording the meeting minutes.
- Organize the unfinished `issues`, evaluate and explain them, and close or add them to the `Backlog` as appropriate.
- Determine the theme for the next Sprint and fill out the `Sprint Issue`.Example: `Sprint 64`
