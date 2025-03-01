# Build with MPLAB X and XC8 GitHub Action

This action will build a MPLAB X / XC8 project.

It runs on Linux Ubuntu 20.04 and uses:

* [MPLAB X](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-x-ide) v6.05
* [XC8](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-xc-compilers) v2.35

## Inputs

### `project`

**Required** The path of the project to build (relative to the repository). For example: `firmware.X`.

### `configuration`

The configuration of the project to build. Defaults to `default`.

## Outputs

None.

## Example Usage

Add the following `.github/workflows/build.yml` file to your project:

```yaml
name: Build
on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master
jobs:
  build:
    name: Build the project
    runs-on: ubuntu-latest
    steps:
      - name: Download the source code
        uses: actions/checkout@v1
      - name: Build
        uses: JolonB/mplabv6.05-xc8-build-action@v0.2.0
        with:
          project: firmware.X
          configuration: default
```

# Acknowledgements

Inspired by <https://github.com/velocitek/ghactions-mplabx>.  
Forked from <https://github.com/jeandeaual/mplabx-xc8-build-action>.
