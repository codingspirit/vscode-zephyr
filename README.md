# vscode-zephyr
This is an example [vscode](https://code.visualstudio.com/) settings to provide supports for [zephyr](https://zephyrproject.org/) based projects build/debug.

<!--more-->

## Quick start

- Copy this *.vscode* folder into your project root folder.
- Modify the environment variables at the end of *task.json* and *launch.json* base on your own settings:
```json
    //task.json
    "options": {
        "env": {
            "ZEPHYR_TOOLCHAIN_VARIANT": "zephyr",
            "ZEPHYR_SDK_INSTALL_DIR": "/home/alex/zephyr-sdk-0.10.3",
            "ZEPHYR_BASE": "${workspaceFolder}/zephyrproject/zephyr",
            "VS_CODE_BOARD_TO_BUILD": "reel_board",
            "VS_CODE_ZEPHYR_BIN_NAME": "zephyr.elf",
        }
    }
```
```json
    //launch.json
            "miDebuggerPath": "/home/alex/zephyr-sdk-0.10.3/arm-zephyr-eabi/bin/arm-zephyr-eabi-gdb"
        }
    ]
}
```
- Press **Ctrl+Shit+B** to trigger build task(You also can run task "**zephyr build ninja**" alternatively if you want to use **ninja** to build).
- Press the holy **F5** button(which is on the right side of the **F4** button) to start debugging.
- An selecting list will jump out when terminated debug process, don't forget to select it.

## Know issues
- An exception will occur when stop at **main()**. Not sure where the root cause is, but debug process still can proceed, just ignore it.

- Breakpoints can't be added into some lines but you can run code step by step to those lines. Disable zephyr build optimization doesn't help on this, it might related to zephyr toolchain.
