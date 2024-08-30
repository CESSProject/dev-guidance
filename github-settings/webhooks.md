# Webhooks

Maintainers should set up at least one webhook for integration with an instant messaging (IM) communication software, corresponding to the key codebases.

## IM Integration

Webhooks integrated with IM should remain concise, only notifying of events and information necessary in our workflow, to avoid generating an excessive amount of IM messages during normal operations.

To achieve the desired effect, there should be a bot tool capable of customizing event filtering.

### Events to Include

We believe that webhooks of this kind should include at least the following events:

1. check runs

   - completed

   To help understand the results of checks, confirming when a pull request (pr) can be merged or to fix based on failed checks.

2. issues

   - opened
   - reopened
   - deleted
   - assigned
   - unassigned

   To help understand the creation and assignment of tasks/community reports.

3. issue comments

   - created

   To help understand new information about tasks/community reports.

4. pull requests

   - opened
   - closed
   - reopoened
   - assigned
   - unassigned
   - review requested
   - review request removed
   - ready to review

   To help understand the status of task execution.

5. pull request reviews
   To help understand the review status of tasks.

6. pull request review comments
   To help understand the review status of tasks.

7. pull request review threads
   To help understand the review status of tasks.

8. releases
   To help understand the status of version releases.

### Events to Include With Caution

For events that are numerous, frequently triggered, or not closely monitored during work processes, we should handle with caution, such as:

1. branch or tag
2. Other check runs.
3. Other issues.
4. Other issue comments.
