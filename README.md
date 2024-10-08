# Vulture Dead Code Scanner GitHub Action

This GitHub Action runs [Vulture](https://github.com/jendrikseipp/vulture), a tool for detecting unused Python code, on your repository. It helps you identify and eliminate dead code, improving your project's maintainability and reducing its complexity.

## Features

- Easy integration with GitHub workflows.
- Flexible configuration using Vulture's CLI arguments.
- Supports all Vulture options and features.
- Customizable for different project structures and requirements.

## Usage

To use this action in your workflow, include the `gtkacz/vulture-action` action on one of your GitHub workflow yml files. The file may look like the following:

```yaml
name: Vulture Dead Code Check

on: [push, pull_request]

jobs:
  vulture:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Run Vulture
      uses: gtkacz/vulture-action@1.0.0
      with:
        args: '. --min-confidence 70 --exclude "tests,docs" --verbose'
```

## Inputs

This action accepts three inputs:

- `src`: Source to run vulture. Default: `.`.
- `args`: Arguments passed to Vulture. Use `vulture --help` to see available options or refer to the [Vulture documentation](https://github.com/jendrikseipp/vulture#usage).
- `version`: The version of Vulture to use, e.g. `==2.11.0`. Default is null.

## Examples

### Basic Usage

Scan the entire repository with default settings:

```yaml
- name: Run Vulture
  uses: gtkacz/vulture-action@1.0.0
```

### Custom Configuration

Scan with a minimum confidence of 80%, excluding specific directories, and using verbose output:

```yaml
- name: Run Vulture
  uses: gtkacz/vulture-action@1.0.0
  with:
    args: '--min-confidence 80 --exclude "tests,docs,build" --verbose'
```

### Scanning Specific Files or Directories

Scan only the `src` directory:

```yaml
- name: Run Vulture
  uses: gtkacz/vulture-action@v1
  with:
    src: 'package'
```

## Contributing

Contributions to improve this GitHub Action are welcome! Please feel free to submit issues or pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- This action uses [Vulture](https://github.com/jendrikseipp/vulture), created by Jendrik Seipp.
- Thanks to the GitHub Actions team for providing the platform and documentation.

## Support

If you encounter any problems or have any questions, please open an issue in this repository.
