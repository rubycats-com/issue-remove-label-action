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
      issues: write
    steps:
      - name: Remove Label
        uses: rubycats-com/issue-remove-label-action
        with:
          number: ${{ github.event.issue.number }}
          label: 'research'
```

## Inputs

| Input    | Required | Description |
|----------|----------|-------------|
| `number` | true     | Issue id    |
| `label`  | true     | Label text  |

## Outputs

No outputs in this action
