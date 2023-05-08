KernelSU Action for Realme Kernel
Based on the magic version of this project, it is generally suitable for the construction of the OPLUS kernel

Note: This project does not support the compilation of OPPO and OnePlus kernels, you can take a look at this project

Support for kernels
4.14.x
4.19.x
use
After successful compilation, AnyKernel3 will be uploaded, device checking has been turned off, please flash in Twrp.Action

Fork this repository to your repository and edit config.env as follows, then click, you can see the options on the left, click on the options will see the top of the large dialog box on the right, click on it will start the build.ActionBuild KernelRun workflows

You will need to verify and fill in the following content. Typically, these configurations are stored in config.env
Kernel Source
Enter the download address of the kernel repository archive

The format is: https://github.com/内核所有者名称/内核仓库名称/archive/内核提交id(在源码地址主页后面输入commit然后访问点击最新的提交再查看链接地址的commits/后面的字符).tar.gz

Kernel Vendor
Enter the additional source code file for the kernel Concentrate:如果你的内核源码没有附加仓库的话，请将此项改为false

Kernel Defconfig
Enter the kernel configuration file name

Target Arch
For example: arm64

Kernel File
Fill in the image that needs to be flashed, which is generally the same as the BOARD_KERNEL_IMAGE_NAME in your aosp-device tree

For example: Image.gz-dtb

Clang
Use Custom Clang
Change to true You can use the official Clarang in addition to Google, such as Proton-Clang

Custom Clang
Support direct links to GitHub repositories or zip archives

Custom Clang Commands
I have used custom clang, so I should change the compiler position myself:)

Clang Branch
This option provides the option to customize Google's upstream branches, the main ones being branches

Clang branches
master
master-kernel-build-2021
master-kernel-build-2022
Or other branches, please look in https://android.googlesource.com/platform/prebuilts/clang/host/linux-x86 according to your needs

Clang Version
Enter the version of Clang that you want to use

Clang version	Corresponds to the Android version	AOSP-Clang version
12.0.5	Android S	r416183b
14.0.6	Android T	r450784d
14.0.7		r450784e
15.0.1		r458507
It is generally possible to compile most kernelsClang124.14 及以上

Extra Build Commands
Some kernels need to manually add some compilation commands to compile normally, and do not fill in if they are not needed Separate commands with spaces

For example: LLVM=1 LLVM_IAS=1

Disable LTO
Used to optimize the kernel, but sometimes it causes errors, so provide to disable it, set to true to disable

Use KernelSU
Whether to use KernelSU to troubleshoot kernel or compile kernels separately

KernelSU Branch or Tag
Select the branch or tag of KernelSU:

Main branch (development version): KERNELSU_TAG=main
Latest TAG (stable version): KERNELSU_TAG=
Specify TAG (such as): v0.5.2KERNELSU_TAG=v0.5.2
Use Kprobes
If your kernel Kprobes is working properly, change this to true to automatically inject parameters into defconfig

Use overlayfs
If the kernel does not have this parameter, please enable it, the module needs it

Need DTBO
If your kernel also needs to flash DTBO, set to true

Make Boot Image
Set to true will compile boot.img, which you need to provideSource boot image

Source Boot Image
Therefore, to provide a boot image that the source system can boot normally, you need a direct link, preferably the same set of kernel source code and the same set of device tree for your current system built from aosp. ramdisk contains partition tables and init, without which the image built will not boot properly.

Special thanks
AnyKernel3
AOSP
KernelSU
xiaoxindada
kernelSU_Action
KernelSU Action for Realme Kernel
基于[此项目](https://github.com/xiaoleGun/KernelSU_Action)的魔改版本，一般适用于OPLUS内核的构建

注:本项目不支持OPPO和一加的内核的编译，可以看看[这个项目](https://github.com/dabao1955/KernelSU_Action_OPLUS)
## 支持内核

- `4.14.x`
- `4.19.x`

## 使用

> 编译成功后，会在`Action`上传 AnyKernel3，已经关闭设备检查，请在 Twrp 刷入。

Fork 本仓库到你的储存库然后按照以下内容编辑config.env，之后点击`Action`，在左侧可看见`Build Kernel`选项，点击选项会看见右边的大对话框的上面会有`Run workflows`，点击它会启动构建。

# 你需要验证并填写以下内容。一般地，这些配置存放于config.env
*********


### Kernel Source

填写内核仓库归档文件的下载地址

格式为: `https://github.com/内核所有者名称/内核仓库名称/archive/内核提交id(在源码地址主页后面输入commit然后访问点击最新的提交再查看链接地址的commits/后面的字符).tar.gz`


### Kernel Vendor

填写内核的附加源码文件
注:`如果你的内核源码没有附加仓库的话，请将此项改为false`
### Kernel Defconfig

填写内核配置文件名称


### Target Arch

例如: arm64

### Kernel File

填写需要刷写的 image，一般与你的 aosp-device tree 里的 BOARD_KERNEL_IMAGE_NAME 是一致的

例如: Image.gz-dtb

### Clang

#### Use Custom Clang

改成true
可以使用除google官方的clang，如[proton-clang](https://github.com/kdrag0n/proton-clang)

#### Custom Clang

支持github仓库或者zip压缩包的直链

#### Custom Clang Commands

都用自定义clang了，自己改改编译器位置应该会吧 :)

#### Clang Branch
这个选项提供可自定义Google上游分支的选项，主要的有分支有
| Clang 分支 |
| ---------- |
| master |
| master-kernel-build-2021 |
| master-kernel-build-2022 |

或者其它分支，请根据自己的需求在 https://android.googlesource.com/platform/prebuilts/clang/host/linux-x86 中寻找

#### Clang Version

填写需要使用的 Clang 版本
| Clang 版本 | 对应 Android 版本 | AOSP-Clang 版本 |
| ---------- | ----------------- | --------------- |
| 12.0.5 | Android S | r416183b |
| 14.0.6 | Android T | r450784d |
| 14.0.7 | | r450784e |
| 15.0.1 | | r458507 |

一般 `Clang12` 就能通过大部分 `4.14 及以上`的内核的编译

### Extra Build Commands

有的内核需要手动加入一些编译命令，才能正常编译，不需要的话不填写即可
请在命令与命令之间用空格隔开

例如: LLVM=1 LLVM_IAS=1

### Disable LTO

用于优化内核，但有些时候会导致错误，所以提供禁用它，设置为 true 即禁用

### Use KernelSU

是否使用 KernelSU，用于排查内核故障或单独编译内核

#### KernelSU Branch or Tag

选择KernelSU的分支或tag:
- main分支(开发版): `KERNELSU_TAG=main`
- 最新TAG(稳定版): `KERNELSU_TAG=`
- 指定TAG(如`v0.5.2`): `KERNELSU_TAG=v0.5.2`

### Use Kprobes

如果你的内核 Kprobes 工作正常这项改成 true 即可自动在 defconfig 注入参数

### Use overlayfs

内核没有该参数的话请启用，模块需要

### Need DTBO

如果你的内核还需要刷入DTBO，请设置为true

### Make Boot Image

设置为true会编译boot.img，需要你提供`Source boot image`

### Source Boot Image

故名思义，提供一个源系统可以正常开机的 boot 镜像，需要直链，最好是同一套内核源码以及与你当前系统同一套设备树从 aosp 构建出来的。ramdisk 里面包含分区表以及 init，没有的话构建出来的镜像会无法正常引导。

## 特别鸣谢

- [AnyKernel3](https://github.com/osm0sis/AnyKernel3)
- [AOSP](https://android.googlesource.com)
- [KernelSU](https://github.com/tiann/KernelSU)
- [xiaoxindada](https://github.com/xiaoxindada)
- [kernelSU_Action](https://github.com/xiaoleGun/KernelSU_Action)
