# ATF binaries
This repository provides reproducible, CI-built ARM-Trusted-Firmware binaries.

The newest releases can be found at: 
https://github.com/atf-builds/atf/releases

### Verifying yourself
Building the ATF manually was tested on Arch Linux and Ubuntu x86_64.   
It requires build-essential, git, wget, tar, bash to be present.   
It downloads a checksum-pinned version of the required ARM and AARCH64 none-eabi gcc toolchains from [arm.com](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-a/downloads), then loads the (also checksum-pinned) ATF sourcecode from the [official GitHub repository](https://github.com/ARM-software/arm-trusted-firmware)

```bash
git clone https://github.com/atf-builds/atf
cd atf
./build.sh
```
Resulting checksums are displayed and the files are copied to `output_dir/`.   
These should match the values of the last release in this repository exactly. 

### Adding new build targets
Targets are defined in [/targets](https://github.com/atf-builds/atf/tree/master/targets).  
Every target gets a clean copy of the ATF to start with and the required Cortex-M0 and -M3 compiler toolchains are set automatically.  
To automatically build ATFs for a new platform, check the [documentation](https://trustedfirmware-a.readthedocs.io/en/latest/plat/index.html) on how to compile for your platform.
A build target looks like this and is sourced as a bash-script:
```bash
PLAT=rk3399
TARGET=bl31
BINARY_PATH=bl31/bl31.elf
ARCH=aarch64
```

