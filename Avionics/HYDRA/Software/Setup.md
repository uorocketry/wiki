---
title: HYDRA Setup
description: 
published: true
date: 2022-12-31T17:42:46.108Z
tags: 
editor: markdown
dateCreated: 2022-12-31T17:42:46.108Z
---

# Building
1. Install Rust: https://www.rust-lang.org/tools/install
2. Build: `cargo build`

# Flashing and debugging
These instructions are relevant for the on-board debugger of the SAM E51 eval kit. These have only been tested on Linux.

### Terminal
1. Install OpenOCD.
2. Install GDB for cross-compile ARM targets (`arm-none-eabi-gdb`)*.
3. In a separate terminal, navigate to the `debug` folder, and run `openocd`.
4. Run `cargo run --bin {board}`, replacing `{board}` with the desired board.
5. GDB should open. Type `l` to load to flash the program to the device. Type `c` to continue program execution.
6. Optionally, run `logging.sh {board}` in a separate terminal to get logs from the board.

*: On some distros like Ubuntu, GDB can be found in `gdb-multiarch`. For other distros, xPack can be used instead: https://xpack.github.io/arm-none-eabi-gcc/install/.

### VSCode
TODO

### CLion
To flash and debug directly from CLion, first create a OpenOCD Run Configuration. A board config file can be found in `debug/openocd.cfg` and binaries are found in `target/thumbv7em-none-eabihf/debug`.