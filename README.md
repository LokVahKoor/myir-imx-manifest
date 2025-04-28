# MYiR i.MX Yocto Project BSP Manifest README

This repository contains the manifest files for MYiR's i.MX-based BSP releases.

## Prerequisites

### Install the `repo` utility

To use this manifest repository, you must first install the `repo` tool:

```bash
mkdir ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
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
repo init -u https://github.com/MYiR-DEV/myir-lmx91-manifest -b scarthgap -m myir-6.6.36-1.0.0.xml
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
MACHINE=myimx8mm DISTRO=myir-imx-xwayland source ./myir-setup-release.sh -b build-xwayland
```

## Building Images

After setting up the build environment, you can build images with:

```bash
bitbake <image-recipe>
```

### Available Image Recipes

Image Name           | Description
---------------------|---------------------------------------------------
myir-image-core      | Core image with basic graphics support
myir-image-multimedia | Image with multimedia and graphics support
myir-image-full      | Complete image with multimedia, machine learning and Qt support

## Documentation

For more detailed information about MYiR i.MX products and BSP, please refer to:
- [MYiR Official Website](https://www.myirtech.com)
- [MYiR Documentation Center](https://www.myirtech.com/list.asp?id=516)

## Support

For technical support, please contact MYiR:
- Email: support@myirtech.com
- Forum: [MYiR Community](https://www.myirtech.com/list.asp?id=519)
