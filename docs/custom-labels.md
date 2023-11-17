# Custom Labels

As part of implementing this project's workflows, you will be asked to create a number of new labels in your repo. These labels are required for the workflows to function properly, but you can customize the names of some of them.

In order to customize the labels, you will need to define inputs for the following actions:

* dequelabs/action-a11y-issue-labeler
* dequelabs/action-a11y-issue-categorizer

## Example

The following example illustrates a scenario in which the team wishes to namespace all severity-related labels to avoid confusion with other similar labels that are already used in the repo.

In labeler.yml:

```yaml
name: Issue Labeler
on:
  issues:
    types: [opened, edited]
jobs:
  add_labels:
    runs-on: ubuntu-latest
    steps:
    - uses: dequelabs/action-vpat-labels@main
    - uses: dequelabs/action-a11y-issue-labeler@main
      with:
        repo-token: "${{ secrets.GITHUB_TOKEN }}"
        include-title: 1
        label-blocker: "vpat:blocker"
        label-critical: "vpat:critical"
        label-serious: "vpat:serious"
        label-moderate: "vpat:moderate"
        label-minor: "vpat:minor"
```

In categorizer.yml:

```yaml
name: Issue Categorizer
on:
  workflow_dispatch:
  schedule:
    - cron: '0 0 * * SUN'
jobs:
  categorize:
    runs-on: ubuntu-latest
    steps:
    - uses: dequelabs/action-a11y-issue-categorizer@main
      with:
        repo-token: "${{ secrets.GITHUB_TOKEN }}"
        label-blocker: "vpat:blocker"
        label-critical: "vpat:critical"
        label-serious: "vpat:serious"
        label-moderate: "vpat:moderate"
```

## action-a11y-issue-labeler

The following inputs are available to override the default labels:

| Input | Description | Default |
| ----- | ----------- | ------- |
| `label-a11y` | Label to apply to issues that constitute accessibility issues | `A11Y` |
| `label-blocker` | Label to apply to issues that are blockers | `Blocker` |
| `label-critical` | Label to apply to issues that are critical | `Critical` |
| `label-serious` | Label to apply to issues that are serious | `Serious` |
| `label-moderate` | Label to apply to issues that are moderate | `Moderate` |
| `label-minor` | Label to apply to issues that are minor | `Minor` |
| `label-customer` | Label to apply to issues that were discovered by a customer | `Customer` |
| `label-production` | Label to apply to issues that exist in production | `Production` |
| `label-vpat` | Label to apply to issues that were discovered during a VPAT | `VPAT` |

## action-a11y-issue-categorizer

The following inputs are available to override the default labels:

| Input | Description | Default |
| ----- | ----------- | ------- |
| `label-a11y` | Label used to identify accessibility issues that should be categorized | `A11Y` |
| `label-blocker` | Label used to identify blocker issues | `Blocker` |
| `label-critical` | Label used to identify critical issues | `Critical` |
| `label-serious` | Label used to identify serious issues | `Serious` |
| `label-moderate` | Label used to identify moderate issues | `Moderate` |
| `label-production` | Label to apply to issues that exist in production | `Production` |
