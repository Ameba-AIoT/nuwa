## Introduction

This repository contains the source code and tools for Realtek Ameba IoT SoCs, including:
- AmebaPro2
  - rtl8735b_evb

## Setup Build Environment

* The toolchain is `asdk-10.3.1`.
* Linux platform is supported for now
* Python version 3.8 or higher is required.
* cmake, device-tree-compiler, west, python3-venv are also required.

## Compiling the Project

You can download and compile the SDK using the following steps
```
$ mkdir ameba-zephyr-pro2 && cd ameba-zephyr-pro2
$ west init -m git@github.com:Ameba-AIoT/nuwa.git --mr rtl8735b
$ west update
$ ln -sf tools/meta_tools/nuwa.py nuwa.py
$ ./nuwa.py setup
$ ./nuwa.py build -a <application> -d <device> -t <toolchain dir> -b <build folder>
```
e.g.: `$ ./nuwa.py build -a zephyr/samples/hello_world -d rtl8735b_evb -t ~/toolchain -b build` to build zephyr hello world sample for rtl8735b_evb board with
      toolchain in ~/toolchain/asdk-10.3.1. The generated files will be in build folder. if `-b` is not used to indicate the folder name, `build` folder will be used in default

And use `$ ./nuwa.py update` to update the lastest code.

## Flashing

After the compilation is complete, the generated image `flash_zephyr.bin` is located in the `build\amebapro2_gcc_project` folder. Please use `Pro2_PG_tool` to download the image to the SoC.
