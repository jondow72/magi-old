CROSS COMPILATION FOR 32-BIT ARM32 ON LINUX
==============================================

The steps below can be performed on debian:

    sudo apt update
    sudo apt upgrade
    sudo apt install build-essential autotools-dev xz-utils git make automake pkg-config cmake curl g++-multilib gcc-multilib libtool binutils bsdmainutils pkg-config python3 patch bison
    sudo apt install g++-arm-linux-gnueabihf binutils-arm-linux-gnueabihf
    git clone https://github.com/magi-dev/magi.git
    cd magi
    cd depends
    make HOST=arm-linux-gnueabihf -j4
    cd ..
    ~/magi/depends/work/build/arm-linux-gnueabihf/qt/5.15.3-*/qtbase/bin/qmake cross-compilation.pro USE_QRCODE=1 USE_UPNP=0 USE_DBUS=1 HOST=arm-linux-gnueabihf
    make -j4
    cd src
    make -j4 -f makefile.arm32
    arm-linux-gnueabihf-strip magid
<br/>

m-wallet is in magi/release<br/>
magid is in magi/src<br/>

Michiel Meijer