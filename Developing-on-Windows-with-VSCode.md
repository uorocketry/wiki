If you want linting and error detection, you can use VSCode remote debugging. To compile in the command line, see [here](Compiling-the-SBG-Library-on-Linux-Unix-WSL).

VSCode supports remote debugging with WSL. First, install WSL.

1. Install the [Remote - WSL extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl).
2. Click the bottom left and select "Remote Debugging with WSL". 

![Remote Debugging with WSL Button](https://user-images.githubusercontent.com/12688112/93003773-74bbca00-f50f-11ea-8cb8-75671f5e6c25.png)

**Note**: This can actually be done with a real linux machine, such as a Raspberry Pi over SSH

3. Install CMake Tools Extension

To setup CMake kits for different environement configurations, see [this document](Set-Environement-Variable-In-Vscode-With-The-Cmake-Plugin).

**Note**: Remote WSL is like a new VSCode environment. You will have to reinstall most extensions.