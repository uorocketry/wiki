To enable testing mode, define the `TESTING` environment variable.

On Linux/WSL:

**Set**: `export TESTING=1`

**Unset**: `unset TESTING`

You can also [set this up with Vscode](Set-Environement-Variable-In-Vscode-With-The-Cmake-Plugin)

### Testing Data

Testing data is a csv formatted in the same way as the log file (located at `sbgECom/bin/data/log.csv` or `./data/log.csv` if running the built code somewhere else).

This file should be placed in `sbgECom/bin/data/test-data.csv` or `./data/test-data.csv` if running the built code somewhere else.
