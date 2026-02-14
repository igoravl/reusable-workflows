# Release GitHub Release on Merged PR

A reusable workflow that automatically creates a GitHub release when a pull request is merged to the main branch.

## Usage

```yaml
name: Create Release
on:
  pull_request:
    types: [closed]

jobs:
  release:
    uses: HAL-PE/platform-devops-reusable-workflows/create-release/workflow.yml@v1
    with:
      release_notes: 'Optional custom release notes'
      version: 'Optional version number (e.g., 1.2.3)'
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `release_notes` | Custom release notes for the new version | No | PR body |
| `version` | Specific version number for the release | No | Auto-generated via GitVersion |

## Features

- **Automatic Versioning**: Uses GitVersion to automatically determine the next semantic version
- **Custom Versioning**: Optionally specify a custom version number
- **Release Notes**: Uses PR body as release notes by default, or accepts custom notes
- **Git Tagging**: Automatically tags the commit with the version (prefixed with 'v')
- **GitHub Release**: Creates a GitHub release with auto-generated or custom release notes

## Permissions Required

The calling workflow must have `contents: write` permission (already configured in the reusable workflow).
