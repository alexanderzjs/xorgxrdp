This xorgxrdp version accompanies xrdp with NVIDIA acceleration, which is https://github.com/alexanderzjs/xrdp, for remote desktop and is a copy of ``https://github.com/Nexarian/xorgxrdp.git --branch mainline_merge_backup``. You should have ``nasm, xorg.xorgserver`` in order to build this library.

To build it, you need to run:

1. ``./bootstrap``
2. ``./configure --with-simd --enable-lrandr``.
3. ``make -j $(nproc) clean all``
4. ``sudo make install``

# xorgxrdp

## Overview

**xorgxrdp** is a collection of modules to be used with a pre-existing X.Org
install to make the X server act like X11rdp. Unlike X11rdp, you don't have to
recompile the whole X Window System. Instead, additional modules are installed to
a location where the existing Xorg installation would pick them.

xorgxrdp is to be used together with [xrdp](https://github.com/neutrinolabs/xrdp)
and X.Org Server. It is pretty useless using xorgxrdp alone.

![xorgxrdp overview](https://github.com/neutrinolabs/xorgxrdp/raw/gh-pages/docs/xorgxrdp_overview.png)

## Features

xorgxrdp supports screen resizing. When an RDP client connects, the screen is
resized to the size supplied by the client.

xorgxrdp uses 24 bits per pixel internally. xrdp translates the color depth for
the RDP client as requested. RDP clients can disconnect and reconnect to the same
session even if they use different color depths.

## Usage

When logging in to xrdp using an RDP client, make sure to select Xorg on the
login screen. xrdp will tell xrdp-sesman to start Xorg with the configuration
file that activates the xorgxrdp modules.

Make sure your system has the X.Org server (typically **xserver-xorg-core** or
**xorg-x11-server-Xorg** package). Check that Xorg is in the standard path
(normally in `/usr/bin`).

## Contributing

First off, thanks for taking your time for improve xorgxrdp.

If you contribute to xorgxrdp, checkout **devel** branch and make changes to
the branch. Please make pull requests also versus **devel** branch.

To debug xorgxrdp, you can run Xorg with xorgxrdp manually:

```
Xorg :10 -config xrdp/xorg.conf
```

See also the `tests` directory for the tests that exercise xorgxrdp modules.
