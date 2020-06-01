+++
title = "Wayland"
date = 2017-07-08
weight = 500
tags = ["wayland"]
+++

# Porting Weston-Wayland

Porting Wayland is not as simple as you think because many packages are related to it and they have dependencies.

Wayland official website provides some guide but it is not fully covered (source version difference cloned from git).

Moreover, the command the website introduced is not acceptable on Ubuntu 16.04.
    sudo apt-get install wayland weston wayland-protocols libinput xserver-xorg

Therefore, I modified guideline in a way of my own taste:


    # setup environment for local install:
    export WLD=$HOME/install
    export LD_LIBRARY_PATH=$WLD/lib
    export PKG_CONFIG_PATH=$WLD/lib/pkgconfig/:$WLD/share/pkgconfig/
    export PATH=$WLD/bin:$PATH
    export ACLOCAL_PATH=$WLD/share/aclocal
    export ACLOCAL="aclocal -I $ACLOCAL_PATH"
    mkdir -p $ACLOCAL_PATH
    export MAKEFLAGS="j5" # run 5 threads, or use your own flags

    sudo apt install git autoconf libtool libffi-dev libexpat1-dev libxml2-dev \
      doxygen xmlto graphviz libmtdev-dev libudev-dev libevdev-dev libwacom-dev \
      xutils-dev libgl1-mesa-dev libmd-dev \
      x11proto-xcmisc-dev x11proto-bigreqs-dev x11proto-randr-dev \
      x11proto-fonts-dev x11proto-video-dev x11proto-composite-dev \
      x11proto-record-dev x11proto-scrnsaver-dev x11proto-resource-dev \
      x11proto-xf86dri-dev x11proto-present-dev x11proto-xinerama-dev \
      libxkbfile-dev libxfont-dev libpixman-1-dev x11proto-render-dev \
      libepoxy-dev libgles2-mesa-dev libxcb-composite0-dev libxcursor-dev \
      libcairo2-dev libgbm-dev libpam0g-dev

    git clone git://anongit.freedesktop.org/wayland/wayland
    git clone git://anongit.freedesktop.org/wayland/wayland-protocols
    git clone git://anongit.freedesktop.org/wayland/libinput
    git clone git://anongit.freedesktop.org/xorg/lib/libXfont
    git clone git://anongit.freedesktop.org/xorg/xserver
    git clone git://anongit.freedesktop.org/wayland/weston

    # wayland

    cd wayland
    git checkout 1.12.0    # Ubuntu 16.04 LTS (Xenial)
    ./autogen.sh --prefix=$WLD # --disable-documentation
    make check && make && make install
    cd ..


    # wayland-protocols:

    cd wayland-protocols
    git checkout 1.1    # Ubuntu 16.04 LTS (Xenial)
    ./autogen.sh --prefix=$WLD
    make check && make && make install
    cd ..


    # libinput:

    cd libinput
    git checkout 1.6.0    # Ubuntu 16.04 LTS (Xenial)
    ./autogen.sh --prefix=$WLD
    make check && make && make install
    cd ..


    # X Server:

    # No package 'xfont2' found

    cd libXfont
    git checkout libXfont-1.5.1    # Ubuntu 16.04 LTS (Xenial)
    ./autogen.sh --prefix=$WLD
    make check && make && make install
    cd ..


    cd xserver
    git checkout xorg-server-1.18.4    # Ubuntu 16.04 LTS (Xenial)
    ./autogen.sh --prefix=$WLD --disable-docs --disable-devel-docs \
      --enable-xwayland --disable-xorg --disable-xvfb --disable-xnest \
      --disable-xquartz --disable-xwin
    make check && make && make install
    cd ..


    # weston:

    # Links needed so XWayland works:
    mkdir -p $WLD/share/X11/xkb/rules
    ln -s /usr/share/X11/xkb/rules/evdev $WLD/share/X11/xkb/rules/
    ln -s /usr/bin/xkbcomp $WLD/bin/

    cd weston
    git checkout 1.9.0    # Ubuntu 16.04 LTS (Xenial)
    ./autogen.sh --prefix=$WLD --disable-setuid-install --with-xserver-path=$WLD/bin/Xwayland
    make check # runs Xwayland
    make && make install
    cd ..


    # Weston configuration:
    mkdir -p ~/.config
    cp weston/weston.ini ~/.config
    editor ~/.config/weston.ini # edit to set background and turn on xwayland.so module

    # Run it in an X11 window:
    weston
