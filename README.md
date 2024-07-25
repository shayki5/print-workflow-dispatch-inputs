# Print Workflow Dispatch Inputs and Env Vars

This GitHub Action prints all input values from a `workflow_dispatch` event to the log. Optionally, it can also print environment variables and add inputs to the GitHub Summary in a collapsible format.

## Features

- Prints all `workflow_dispatch` inputs to the log
- Optionally prints all environment variables
- Optionally adds inputs to GitHub Summary in a collapsible format
- Minimal configuration required
- Lightweight and fast

## Usage

To use this action in your workflow, add it as a step in your `workflow_dispatch` triggered workflow:

```yaml
name: Print Inputs and Env Vars Example

on:
  workflow_dispatch:
    inputs:
      name:
        description: 'Your name'
        required: true
        type: string
      age:
        description: 'Your age'
        required: false
        type: number

jobs:
  print-inputs-and-env:
    runs-on: ubuntu-latest
    steps:
      - name: Print Workflow Dispatch Inputs and Env Vars
        uses: shayki5/print-workflow-dispatch-inputs@v1
        with:
          print_env_vars: 'true'  # Set to 'true' to print environment variables
          add_to_summary: 'true'  # Set to 'true' to add inputs to GitHub Summary
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `print_env_vars` | Whether to print environment variables | No | 'false' |
| `add_to_summary` | Whether to add inputs to GitHub Summary | No | 'false' |


## GitHub Summary

When `add_to_summary` is set to 'true', the action will add the workflow dispatch inputs to the GitHub Summary in a collapsible format. This allows you to easily view the inputs without cluttering the summary.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check [issues page](https://github.com/shayki5/print-workflow-dispatch-inputs/issues).

## Support

If you encounter any problems or have any questions, please open an issue in this repository.
