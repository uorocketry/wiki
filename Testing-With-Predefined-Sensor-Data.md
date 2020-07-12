To enable testing mode, define the `TESTING` environment variable.

On Linux/WSL:

**Set**: `export TESTING=1`

**Unset**: `unset TESTING`

### Testing Data

Testing data is a csv formatted in the same way as the following example file:

**TODO**

This file should be placed in **TBD**.

### Vscode Cmake Plugin

To use testing mode with the Cmake Vscode plugin, you can setup a cmake kit.

First, open up your current kits using `Ctrl + shift + P` and "Edit User-Local Cmake Kits". Copy the data from the one you are currently using.

Create a file in the `.vscode` folder called `cmake-kits.json` and format it like below:

```
[{
    "name": "Testing",
    "environmentVariables": {
        "TESTING": "1"
    },
    <DATA FROM EXISTING CMAKE KIT GOES HERE>
}]
```

Then, change your active kit and rebuild.

![Cmake Kit button](https://user-images.githubusercontent.com/12688112/87250980-76e1a980-c436-11ea-8d81-bc10759ebbec.png)
