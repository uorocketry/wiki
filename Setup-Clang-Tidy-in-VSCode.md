1. Install `clang-tidy` in your environment (`sudo apt update && sudo apt install clang-tidy`)
2. Install the [Clang-Tidy](https://marketplace.visualstudio.com/items?itemName=notskm.clang-tidy) extension
3. Add the following lines to `.vscode/settings.json`

```json
"clang-tidy.checks": [
    "clang-diagnostic-*",
    "clang-analyzer-*",
    "-*",
    "bugprone*",
    "modernize*",
    "performance*",
    "-modernize-use-trailing-return-type"
],
"clang-tidy.buildPath": "./build"
```