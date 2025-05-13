# GitHub Action For Magento Code Sniffer

This action is used to evaluate the quality of code by utilizing code sniffer.

**Author:** Patryk Waluś (patryk.walus@vaimo.com)

## Supported versions
- v1
    - Code sniffer analysis
    - Possibility to choose full or partial (modified files) analysis

## Compatibility

This action is compatible only with the custom Docker image: [vaimo/image-action-magento](https://github.com/vaimo/image-action-magento).

# Usage

```yaml
jobs:
  code-sniffer:
    runs-on: ubuntu-latest
    container:
      image: ghcr.io/vaimo/image-action-magento:${{inputs.version}}-v1
    steps:
      - name: Code Sniffer action
        uses: vaimo/action-magento-code-sniffer@v1
        with:
          # Directories that should be evaluated (separated by comma).
          # Required
          directories: ./app/code/Vaimo
          # Directory name that will be used to run action.
          # Optional - if not specified then uses the root directory.
          working-directory: src
          # If true code sniffer will analyze all files in the seleced directories.
          # If false code sniffer will analyze only modified files.
          # Optional - if not specified then uses full analysis.
          full-analysis: true/false
```