## Overview

This repository contains custom GitHub Actions that are used across various repositories within our organization. These actions help to standardize CI/CD processes, code quality checks, and other automated workflows.

## Usage

To use any of the custom actions in your repository, reference them in your workflow YAML file like so:

### Pull Request

[Squadron Example](https://github.com/SwissLife-OSS/squadron/blob/master/.github/workflows/pull-request.yml)

```yaml
- name: Build, Test and Sonar
  uses: swisslife-oss/actions/pull-request@main
  with:
    sonar_token: ${{ secrets.SONAR_TOKEN }}
    sonar_project_key: 'SwissLife-OSS_Squadron'
    sonar_project_name: "squadron"
    pr_number: ${{ github.event.pull_request.number }}
    pr_source_branch: ${{ github.head_ref }}
    pr_target_branch: ${{ github.base_ref }}
    github_repository: ${{ github.repository }}
    sonar_exclusions: ${{ vars.SONAR_EXCLUSIONS }}
```

### Release

[Squadron Example](https://github.com/SwissLife-OSS/squadron/blob/master/.github/workflows/release.yml)

```yaml
- name: Build, Test and Sonar
  uses: swisslife-oss/actions/release-sonar@main
  with:
    tag: ${{ github.ref_name }}
    sonar_token: ${{ secrets.SONAR_TOKEN }}
    sonar_project_key: 'SwissLife-OSS_Squadron'
    sonar_project_name: "squadron"
    sonar_exclusions: ${{ vars.SONAR_EXCLUSIONS }}
```

```yaml
- name: Build, Test and Sonar
  uses: swisslife-oss/actions/release-sonar@main
  with:
    tag: ${{ github.ref_name }}
    sonar_token: ${{ secrets.SONAR_TOKEN }}
    sonar_project_key: 'SwissLife-OSS_Squadron'
    sonar_project_name: "squadron"
    sonar_exclusions: ${{ vars.SONAR_EXCLUSIONS }}
```

## Community

This project has adopted the code of conduct defined by the [Contributor Covenant](https://contributor-covenant.org/)
to clarify expected behavior in our community. For more information, see the [Swiss Life OSS Code of Conduct](https://swisslife-oss.github.io/coc).