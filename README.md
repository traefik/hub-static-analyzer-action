
# Traefik Hub Static Analyzer GitHub Action

This GitHub Action performs static analysis on Traefik Hub Custom Resource Definitions (CRD) manifests. 
It allows you to lint the manifests and generate a diff report between commits. 
The action is based on [hub-static-analyzer](https://github.com/traefik/hub-static-analyzer), a tool provided by [TraefikLabs](https://traefik.io/).

## Usage

```yaml
name: Traefik Hub Static Analysis

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Run Traefik Hub Static Analyzer
      uses: traefik/hub-static-analyzer-action:latest
      with:
        # Version of hub-static-analyzer to use.
        # By default, the latest version available will be used.
        version: "latest"
        
        # Path to the directory containing the manifests to analyze. 
        # By default, the current directory will be used.
        path: "path/to/manifests"
        
        ## Linting options:
        
        # Enable linting.
        # By default, "false".
        lint: "true"
        
        # Configure the output format of the linter. One of `unix`, `checkstyle` or `json`. 
        # By default, `unix` format will be used.
        lint-format: "unix"
        
        # Path where to store the linting results. The file will be overwritten if it exists.
        # By default, in "traefik-hub-static-analyzer-lint.out".
        lint-output-file: "/path/to/output.lint.out"
        
        ## Diff report options:
        
        # Enable the generation of a diff report.
        # By default, "false".
        diff: "true"
        
        # Range of commits on which to run the analysis.
        # This could be a strict range: 5f6b21d...cff824e
        # Or use relative references: HEAD~3...HEAD~1
        # Or simply from a specific commit to HEAD: 5f6b21d
        # By default, diff with unstaged changes.
        diff-range: "HEAD~1"

        # Path where to store the diff report. The file will be overwritten if it exists.
        # By default, in "traefik-hub-static-analyzer-diff.out".
        diff-output-file: "/path/to/output.lint.out"
```

## Scenarios:

- [Lint your manifests and display linting errors in PR](#Lint-your-manifests-and-display-linting-errors-in-PR)
- [Generate a diff report and displays it in PR](#Generate-a-diff-report-and-displays-it-in-PR)

# Lint your manifests and display linting errors in PR

```yaml

```


# Generate a diff report and displays it in PR

```yaml

```
