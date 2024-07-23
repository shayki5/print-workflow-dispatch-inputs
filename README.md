# Print Workflow Dispatch Inputs and Env Vars

This GitHub Action prints all input values from a `workflow_dispatch` event to the log. Optionally, it can also print all environment variables. It's a simple and effective tool for debugging or verifying input values and environment settings in your manually triggered workflows.

## Features

- Prints all `workflow_dispatch` inputs to the log
- Optionally prints all environment variables
- Minimal configuration required
- Doesn't require a GitHub token
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
        uses: shayki5/print-workflow-dispatch-inputs@v1.0.2
        with:
          print_env_vars: 'true' # Set 'true' to print environment variables as well (default: false)
```

When you manually trigger this workflow and provide values for the inputs, the action will print these input values to the log. If `print_env_vars` is set to 'true', it will also print all environment variables.

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `print_env_vars` | Whether to print environment variables | No | 'false' |

## How it Works

This action reads the event payload from the `GITHUB_EVENT_PATH` environment variable, which is automatically set by GitHub Actions. It then uses `jq` to extract and print the input values. If `print_env_vars` is set to 'true', it also prints all environment variables using the `env` command.

## Requirements

This action is designed to work with `workflow_dispatch` events. It will not print inputs for other event types, but can still print environment variables if enabled.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check [issues page](https://github.com/shayki5/print-workflow-dispatch-inputs/issues).

## Support

If you encounter any problems or have any questions, please open an issue in this repository.
