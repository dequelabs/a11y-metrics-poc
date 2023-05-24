# a11y-metrics-poc

## Badge using JSON

![Accessibility Badge](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/dequelabs/a11y-metrics-poc/auto-generate-vpat-report/a11y_metrics.json)

JSON file must be publically available for this to work. Options: 
* Commit file to a user GIST
* Commit file to a public repo
* Host a public endpoint that responds with this JSON

## Instructions:

1. Copy the following files to your repo:
    * `./github/ISSUE_TEMPLATE/accessibility_violation.md`
    * `./github/workflows/categorizer.yml`
    * `./github/workflows/labeler.yml`
    * `./github/workflows/vpat.yml`
    * `./github/a11y-metrics.yaml`
2. Update `vpat.yml` to include your product name and any additional labels
    * Update the `product-name` input of the dequelabs/action-vpat-report action
    * Update the `--repo` option on each command line that stores a `CAT{0-4}` local variable
3. Create the `vpats` folder referenced in `vpat.yml`. You may need to add an empty text file to add the folder in GitHub.
4. Create the following labels:
    * A11Y
    * CAT0
    * CAT1
    * CAT2
    * CAT3
    * CAT4
    * Production
    * Customer
    * Released
    * Minor
    * Moderate
    * Serious
    * Critical
    * Blocker
5. Copy the `Accessibility Badge` to your README.md. Update `<REPO_NAME>` with your repository name
```
![Accessibility Badge](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/dequelabs/<REPO_NAME>/auto-generate-vpat-report/a11y_metrics.json)
```
