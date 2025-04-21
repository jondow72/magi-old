CROSS COMPILATION FOR 64-BIT AARCH64 ON LINUX
==============================================

The steps below can be performed on debian:

    sudo apt install cmake curl make patch git
    sudo apt install bison g++ pkgconf python3 xz-utils
    sudo apt install git build-essential wget pkg-config curl libtool autotools-dev autoconf automake
    sudo apt install g++-aarch64-linux-gnu binutils-aarch64-linux-gnu
    git clone https://github.com/magi-dev/magi.git
    cd magi
    cd depends
    make HOST=aarch64-linux-gnu -j4
    cd ..
    ~/magi/depends/work/build/aarch64-linux-gnu/qt/5.15.3-*/qtbase/bin/qmake cross-compilation.pro USE_QRCODE=1 USE_UPNP=0 USE_DBUS=1 HOST=aarch64-linux-gnu
    make -j4
    cd src
    make -j4 -f makefile.aarch64
    aarch64-linux-gnu-strip magid
<br/>

m-wallet is in magi/release<br/>
magid is in magi/src<br/>

jondow