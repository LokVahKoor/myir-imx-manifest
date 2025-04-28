# MYiR i.MX Yocto Project BSP Manifest README

This repository contains the manifest files for MYiR's i.MX-based BSP releases.

## Prerequisites

### Install the `repo` utility

To use this manifest repository, you must first install the `repo` tool:

```bash
mkdir ~/bin
curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo > ~/bin/repo
chmod a+x ~/bin/repo
export PATH=${PATH}:~/bin
```

### Install essential host packages

Your build host must install required packages for Yocto builds. Please refer to the "Build Host Packages" section in the Yocto Project documentation:
- https://docs.yoctoproject.org/5.0.3/brief-yoctoprojectqs/index.html#build-host-packages

## Download the BSP

```bash
mkdir myir-lmx91-6.6.36
cd myir-lmx91-6.6.36
repo init -u https://github.com/LokVahKoor/myir-imx-manifest -b i.MX91-6.6.36-scarthgap -m myir-6.6.36-1.0.0.xml
repo sync
```

## Setup the build environment

For MYiR i.MX BSP release:

```bash
MACHINE=<machine> DISTRO=myir-imx-<backend> source ./myir-setup-release.sh -b build-<backend>
```

Available options:
- `<machine>`: Your target machine (e.g., myimx8mm for MYiR i.MX8M Mini boards)
- `<backend>`: Graphics backend type
  - xwayland: Wayland with X11 support (default)
  - wayland: Wayland only
  - fb: Framebuffer

Example for XWayland:
```bash
DISTRO=fsl-imx-xwayland MACHINE=myd-lmx91 source ./myir-setup-release.sh -b build-lmx91
```

## Building Image

After setting up the build environment, you can build images with:

```bash
bitbake <image-recipe>
```

### Available Image Recipes

Image Name           | Description
---------------------|---------------------------------------------------
myir-image-full      | Complete image with multimedia, machine learning and Qt support

## Documentation

For more detailed information about MYiR i.MX products and BSP, please refer to:
- [MYiR Official Website](https://www.myir.cn)
- [MYiR Documentation Center](https://developer.myir.cn)

## Support

For technical support, please contact MYiR:
- Email: support@myirtech.com
