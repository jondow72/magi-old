# Cross-Compiling the Magi wallet for Windows

This document explains how to build Windows binaries from a Linux
system.

## Install MXE requirements
```
sudo apt install -y autoconf automake autopoint bash bison bzip2 flex g++ g++-multilib gettext git gperf intltool libc6-dev-i386 libgdk-pixbuf2.0-dev libltdl-dev libssl-dev libtool-bin libxml-parser-perl make openssl p7zip-full patch perl pkg-config python ruby scons sed unzip wget xz-utils zram-tools software-properties-common lsb-release
```

## Install MXE from the binary distribution
To obtain the current version, run:
```
sudo apt-key adv \
    --keyserver keyserver.ubuntu.com \
    --recv-keys 86B72ED9 && \
sudo add-apt-repository \
    "deb [arch=amd64] https://pkg.mxe.cc/repos/apt `lsb_release -sc` main" && \
sudo apt-get update
```

## Install the MXE packages for the build

For a 32-bit build:

```
sudo apt-get --yes install mxe-i686-w64-mingw32.static-cc
sudo apt-get --yes install mxe-i686-w64-mingw32.static-openssl
sudo apt-get --yes install mxe-i686-w64-mingw32.static-db
sudo apt-get --yes install mxe-i686-w64-mingw32.static-boost
sudo apt-get --yes install mxe-i686-w64-mingw32.static-miniupnpc
sudo apt-get --yes install mxe-i686-w64-mingw32.static-qttools
sudo apt-get --yes install mxe-i686-w64-mingw32.static-gmp
```

For a 64-bit build:

```
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-cc
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-openssl
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-db
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-boost
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-miniupnpc
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-qttools
sudo apt-get --yes install mxe-x86-64-w64-mingw32.static-gmp
```
## Build Windows executables

Add the path to MXE:

```
$ export PATH=$PATH:/usr/lib/mxe/usr/bin
```

To make a 32-bit Windows executable, go to the Magi repository
and use the following:

```
$ cd src
$ make -f makefile.linux-mingw TARGET_PLATFORM=i686
```

To make a 64-bit Windows executable, go to the Magi repository
and use the following:

```
$ cd src
$ make -f makefile.linux-mingw TARGET_PLATFORM=x86_64
```

created a file will be located in magi/src `magid.exe`

## Build Windows Qt executables

To make a 32-bit Windows GUI executable, go to the Magi repository
and use the following:

```
$ i686-w64-mingw32.static-qmake-qt5 QMAKE_LFLAGS+="-Wl,--large-address-aware"
$ make
```

To make a 64-bit Windows GUI executable, go to the Magi repository
and use the following:

```
$ x86_64-w64-mingw32.static-qmake-qt5
$ make
```
created a file will be located in `release/m-wallet.exe`

For further details you can visit https://mxe.cc/#tutorial
