# Get issue labels action

This action get issue labels via gh client

## Usage

Here's an example of how to use this action in a workflow file:

```yaml
name: Example Workflow
jobs:
  lint:
    name: Lint
    runs-on: ubuntu-latest
    permissions:
      issues: read
    steps:
      - name: Get Labels Action
        id: issue-labels
        uses: rubycats-com/get-issue-labels-action
        with:
          number: ${{ github.event.issue.number }}
      - uses: rubycats-com/jarvis-report-action@main
        if: contains(fromJSON(issue-labels.output.labels), 'notify')
        with:
          report-to: ${{ secrets.JARVIS_TELEGRAM_REPORT_TO }}
          token: ${{ secrets.JARVIS_TELEGRAM_TOKEN }}
```

## Inputs

| Input      | Required | Description        |
|------------|----------|--------------------|
| `number`   | true     | Issue id           |

## Outputs

| Output   | Description                                              |
|----------|----------------------------------------------------------|
| `labels` | Labels for issue in JSON format, eg ["notify","feature"] |
