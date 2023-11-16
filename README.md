# a11y-metrics-poc

> Tools for generating accessibility metrics and reports for GitHub repositories.

## Configuring your repo

Use the following instructions to configure your repo to automatically generate VPAT reports based on the issues in your repo.

### Step 1: Add templates, workflows, and config files

Copy the following files to your repo:

* `./github/ISSUE_TEMPLATE/accessibility_violation.md`
* `./github/workflows/categorizer.yml`
* `./github/workflows/labeler.yml`
* `./github/workflows/vpat.yml`
* `./github/a11y-metrics.yaml`

### Step 2: Define VPAT storage location

Choose or create a directory that will store your VPAT reports. For example, you might create a `/vpats` directory in your repo. If you're creating a new directory, you may need to add an empty text file to add the folder in GitHub.

### Step 3: Update the VPAT workflow

Make the following changes to the `vpat.yml` workflow file:

* In the step named "Generate VPAT file"
    * Update the `product-name` input to match your product name
    * Make sure the `output-file` input matches the path of your desired VPAT storage location
* In the step named "Generate a11y metrics score"
    * Update each `--repo` option to match your repo name
* **Optional**: Modify the `on` trigger events to something sensible for your project's release cycle (see [When to run the VPAT workflow](#when-to-run-the-vpat-workflow))

### Step 4: Create labels

Create the following labels in your project. These labels are required for the workflows to function properly.

These labels must be created exactly as shown:

* CAT0
* CAT1
* CAT2
* CAT3
* CAT4

These labels can be created as shown, or customized (see [Custom Labels](./docs/custom-labels.md)):

* A11Y
* Blocker
* Critical
* Serious
* Moderate
* Minor
* Production
* Customer
* Released

### Step 5 (Optional): Add Badge to README

Copy the `Accessibility Badge` to your README.md. Update `<REPO_NAME>` with your repository name.

```
![Accessibility Badge](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/dequelabs/<REPO_NAME>/auto-generate-vpat-report/a11y_metrics.json)
```

## When to run the VPAT workflow

By default, the `vpat.yml` workflow is triggered by two events:

1. `workflow_dispatch` - Manually trigger the workflow using the GitHub API, CLI, or browser interface
2. `schedule` - Every week on Sunday at 12:00 AM UTC

You can modify the `on` trigger events to something sensible for your project's release cycle. For example, you may want to trigger the workflow only when a new release is created using the `release` event trigger. Or you may want to trigger the workflow when commits are pushed to your `main` branch using the `push` event trigger.

See [Events that trigger workflows](https://docs.github.com/en/actions/reference/events-that-trigger-workflows) for more information.

## Publishing VPAT reports

To automatically publish your project's most recent VPAT report to the product docs site, follow these instructions:

1. Copy `./github/workflows/vpat-publisher.yml` to your repo
2. Make the following changes to the `vpat-publisher.yml` workflow file:
    * Configure the `on` trigger event for your project:
        * `branches` - Branch whose latest VPAT report should be published (typically your production branch)
        * `paths` - The location of the VPAT reports in your repo
    * Configure the inputs for the `dequelabs/action-vpat-publish` action:
        * `target-repo-github-token` - GitHub token with write access to the product-docs-site repo
        * `product-id` - The product ID used to identify your product on the docs site

Once configured, and when triggered, this workflow will open a pull request into the product-docs-site repo.

## Badge using JSON

![Accessibility Badge](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/dequelabs/a11y-metrics-poc/auto-generate-vpat-report/a11y_metrics.json)

The JSON file must be publically available for this to work. Options: 
* Commit file to a user GIST
* Commit file to a public repo
* Host a public endpoint that responds with this JSON
