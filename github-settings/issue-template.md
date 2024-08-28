# Issue Template

Using an `issue template` can help maintainers preset issues for different purposes and set different content formats for each, making it easier to prompt submitters to focus on necessary explanations and collect necessary information.

You can refer to the official documentation [Configuring issue templates for your repository](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) for more details.

## Why Use It

Appropriately using `issue template` can:

1. Guide submitters to gradually check and attempt to resolve some quick-fix issues during the process.
2. Guide submitters to collect more valuable information as expected.

Overall, `issue template` work by reducing the speed of submission and increasing the amount of thought, avoiding unnecessary submissions, while helping both parties focus on key information and reducing the cost of subsequent communication.

## How to Use

To enable a new `issue template`, simply add a `.yml` configuration file that meets the format requirements to the `.github/ISSUE_TEMPLATE` directory at the root of your repository.

**Note: `config.yml` will be considered as a global issue template configuration. Its format and function are different from other `.yml` files.**

Such a `.yml` configuration file is essentially a form description, following the [syntax](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms), with available form elements referenced in [GitHub form schema syntax](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-githubs-form-schema).

Here is an example of a `enhancement.yml` file, and the template will consist of a set of checkboxes and a text box.:

```yaml
name: Enhancement
description:  "New feature request or improvement suggestion"
labels: [enhancement]
body:
- type: checkboxes
  attributes:
    label: Components
    description: |
      Please select the components you are filing a bug for
    options:
      - label: cess-node-runtime
        required: false
      - label: cess-node
        required: false
      - label: ceseal
        required: false
      - label: cifrost
        required: false      
- type: textarea
  id: description
  attributes:
    label: Description
    placeholder: |
      I suggest ...
  validations:
    required: true
```

After setting up the issue template, when users click the `New issue` button to create one, they will first enter an issue type selection page, and then fill in the corresponding information based on the selected type.
