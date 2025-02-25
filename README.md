# race-a-trivial-diff

A GitHub Action that detects when multiple people quickly approve a small pull request and posts the winner to Slack.

## What it does

- Checks if a PR has less than 10 lines changed
- If multiple approvals happen within 60 seconds, declares a winner
- Posts a fun message to Slack celebrating the fastest reviewer

## Usage

```yaml
name: "Race a Trivial Diff"
on:
  pull_request_review:
    types: [submitted]

jobs:
  race:
    permissions:
      contents: read
      pull-requests: read
    runs-on: ubuntu-latest
    steps:
      - name: Race a Trivial Diff
        uses: jekozyra/race-a-trivial-diff@v0.0.1
```

## How it works

The action uses the GitHub API to check the number of lines changed in a PR and the timestamps of approvals. It then compares the timestamps of the approvals to determine which one happened first.

## Contributing

If you'd like to contribute to this action, please fork the repository and create a pull request.
