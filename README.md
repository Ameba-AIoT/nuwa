## Introduction

This repository contains the source code and tools for Realtek Ameba IoT SoCs, including:
- AmebaDPlus
  - RTL872xda_evb
- AmebaD
  - RTL872xd_evb

## Setup Build Environment

* The toolchain will be intalled in `/opt/rtk-toolchain` by default. If an error "Error: No Toolchain in `/opt/rtk-toolchain/vsdk-10.3.1/linux/newlib`" encounters when building the project, please refer to ApplicationNote section **Installing Toolchain** for more details.
* Linux platform is supported for now, Ubuntu version 16.04 64-bit or higher is required.
* Windows built with VScode will be supported in the future.
* Python version 3.7 or higher is required. Run `python --version` to check the version. If an error "Command `python` not found" encounters, please refer to ApplicationNote section **Preparing GCC Environment** install python3. If still error appears, please run `sudo ln -s /usr/bin/python3 /usr/bin/python` to create symbolic link from `/usr/bin/python3` to `/usr/bin/python`.

## Compiling the Project

You can download and compile the SDK using the following steps
```
$ mkdir nuwa && cd nuwa
$ west init -m git@github.com:Ameba-AIoT/nuwa.git
$ west update
$ ln -sf tools/meta_tools/nuwa.py nuwa.py
$ ./nuwa.py setup
$ ./nuwa.py build -a <application> -d <device>
```
e.g.: `$ ./nuwa.py build -a zephyr/samples/hello_world -d rtl872xda_evb`

And use `$ ./nuwa.py update` to update the lastest code.

## Flashing

After the compilation is complete, the generated image is located in the `nuwa\images` folder. Please use the software in `nuwa\tools\ameba\ImageTool_Legacy` to download the image to the SoC.

* Environment Requirements: EX. WinXP, Win 7 or later, Microsoft .NET Framework 4.0.
* Connect chip and PC with USB wire.
* Choose the Device profiles according to the chip you use.
* Select the corresponding serial port and transmission baud rate. The default baud rate is 1500000.
* Select the images to be programmed.
* Click the Download button and start. The progress bar will show the download progress of each image and the log window will show the operation status.

For more details on how to use ImageTool, refer to the Tools section on the website:
```
English: https://aiot.realmcu.com/docs/en/latest/rst_tools/image_tool/1_image_tool_toprst.html
Chinese: https://aiot.realmcu.com/docs/cn/latest/rst_tools/image_tool/1_image_tool_toprst.html
```

## Feedback
- If you have any issues or suggestions when using these documentations, please log in [RealMCU](https://www.realmcu.com/en/Account/Login) and give feedback.
- If you find a bug or any error, you can directly create a Pull Request on GitHub.
