CROSS COMPILATION FOR 64-BIT aarch64 ON LINUX
==============================================

The steps below can be performed on debian:

    apt install cmake curl make patch git
    apt install bison g++ pkgconf python3 xz-utils
    apt install git build-essential wget pkg-config curl libtool autotools-dev autoconf automake
    apt install g++-aarch64-linux-gnu binutils-aarch64-linux-gnu
    git clone --branch depends-v23.2 https://github.com/jondow72/magi.git
    cd magi
    cd depends
    make HOST=aarch64-linux-gnu -j4
    cp -R /root/magi/depends/tmp/* /root/magi/depends/work/build/aarch64-linux-gnu/qt
    cd ..
    /root/magi/depends/work/build/aarch64-linux-gnu/qt/5.15.3-d71e76682ea/qtbase/bin/qmake m-wallet-aarch64.pro USE_QRCODE=1 USE_UPNP=1 USE_DBUS=1
    make -j4
    cd src
    make -f makefile.aarch64
    strip magid
<br/>

m-wallet is in magi/release<br/>
magid is in magi/src<br/>

jondow

