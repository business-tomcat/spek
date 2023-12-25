# Installation instructions

## Windows

Download section offers two packages: an MSI installer and a ZIP archive. To
install Spek, download the MSI installer, double-click it and follow the
instructions.

If you don't want to use the installer, you can download the ZIP archive, unpack
it somewhere on your disk and run `Spek\spek.exe`.

## Mac OS X

Spek for Mac OS X is available in the download section. Download and open the
DMG package, then drag the Spek icon to Applications.

Spek requires OS X 10.5+ and an Intel-based Mac.

## *BSD and GNU/Linux

### Binary packages

 * Arch: [spek](https://aur.archlinux.org/packages/spek/) and
   [spek-git](https://aur.archlinux.org/packages/spek-git/)
 * Debian: [spek](https://packages.debian.org/search?keywords=spek)
 * Fedora: [RPMFusion package](https://bugzilla.rpmfusion.org/show_bug.cgi?id=1718)
 * FreeBSD: [audio/spek](https://www.freshports.org/audio/spek/)
 * Gentoo: [media-sound/spek](https://packages.gentoo.org/packages/media-sound/spek)
 * Ubuntu: [spek](http://packages.ubuntu.com/search?keywords=spek)

### Building from the tarball

To build Spek, download the source code tarball then run these commands from
terminal:

    tar -xvf spek-0.8.5.tar.xz
    cd spek-0.8.5
    ./configure
    make

To build you will need wxWidgets and FFmpeg packages. On Debian/Ubuntu you also
need development packages: `libwxgtk2.8-dev`, `wx-common`, `libavcodec-dev` and
`libavformat-dev`.

To start Spek, run:

    src/spek

Or install it with:

    sudo make install

### Building from the git repository

    git clone git://github.com/alexkay/spek.git
    cd spek
    ./autogen.sh
    make

### Building under Ubuntu 22.04 LTS

Additional instructions are used to build spek dependencies from sources with date 2023-12-27 (latest version 0.8.5).  
If you use the spek source tarball, then only newer ffmpeg libraries are needed.  
If you use spek git sources, also newer wxwidget libraries are needed.

#### ffmpeg

Ubuntu 22.04 LTS only provides ffmpeg version 4.x and libavformat58.
spek currenty relies on libavformat59, so you need ffmpeg libraries for version 5.x.

##### Instructions
Uninstall build-in ffmpeg (optional).  
Download ffmpeg sources for latest version 5.x from https://ffmpeg.org/download.html#get-sources  
Direct link: https://ffmpeg.org/releases/ffmpeg-5.1.4.tar.xz  

Build ffmpeg:

    tar xvf ffmpeg-5.1.4.tar.xz
    cd ffmpeg-5.1.4
    ./configure
    # check for errors or missing dependencies
    make
    sudo make install

Build spek (see instructions above):

    tar -xvf spek-0.8.5.tar.xz
    cd spek-0.8.5
    ./configure
    make

#### wxwidgets

Ubuntu 22.04 LTS only provides wxwidget in version 3.0.5, but version >=3.1.7 is needed.

##### Additional packages

Install it via apt:
* dh-autoreconf
* libgtk-3-dev
* libgtk-4-dev (?)
* gettext

##### Instructions to build newer wxwidets 3.2.4
Download latest wxwidgets from https://www.wxwidgets.org/downloads/  
Direct link: https://github.com/wxWidgets/wxWidgets/releases/download/v3.2.4/wxWidgets-3.2.4.tar.bz2  
Build wxwidgets with instructions from here https://github.com/wxWidgets/wxWidgets/blob/v3.2.4/docs/gtk/install.md

Build wxwidgets:

    tar xvjf wxWidgets-3.2.4.tar.bz2
    cd wxWidgets-3.2.4
    mkdir buildgtk
    cd buildgtk
    ../configure --with-gtk
    # check for errors or missing dependencies
    make
    sudo make install
    sudo ldconfig

Build spek (see instructions above):

    git clone git://github.com/alexkay/spek.git
    cd spek
    ./autogen.sh
    make
