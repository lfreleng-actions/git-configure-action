<!--
SPDX-License-Identifier: Apache-2.0
SPDX-FileCopyrightText: 2024 The Linux Foundation
-->

# 🛠️ Configure Git Settings

Action to configure the git username/email from inside a GitHub action/workflow.

## git-configure-action

## Usage Examples

### Basic Usage (configure current directory/repository)

```yaml
- name: 'configure Git settings for commit'
  uses: lfit/releng-reusable-workflows/.github/actions/git-configure-action@main
  with:
      commit_user_name: 'John Doe'
      commit_user_email: 'john.doe@somedomain.org'
```

### Configure Git for a Specific Repository/Directory

```yaml
- name: 'Configure Git settings for submodule/folder'
  uses: lfit/releng-reusable-workflows/.github/actions/git-configure-action@main
  with:
      commit_user_name: 'John Doe'
      commit_user_email: 'john.doe@somedomain.org'
      path_prefix: 'path/to/git/repository'
```

## Inputs

By default, the action will configure git operations to use the github actions
automation/bot account.

<!-- markdownlint-disable MD013 -->

| Variable name     | Required | Default value                                         | Description                              |
| ----------------- | -------- | ----------------------------------------------------- | ---------------------------------------- |
| commit_user_name  | false    | github-actions[bot]                                   | user name                                |
| commit_user_email | false    | 41898282+github-actions[bot]@users.noreply.github.com | user email address                       |
| path_prefix       | false    | .                                                     | directory location containing git repository |

<!-- markdownlint-enable MD013 -->

## Outputs

The action has no outputs, but does provide summary step information when
invoked. The action will configure the git repository located at the specified
path_prefix directory (defaults to current directory if not specified).

## Requirements/Dependencies

The git command-line tool must be available in the environment for the action
to succeed. The specified path_prefix directory must exist and contain a valid
git repository (with a .git folder).
