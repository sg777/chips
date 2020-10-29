### Steps to build chips-qt wallet for windows 

```
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3

sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev

sudo apt-get -y install software-properties-common
sudo add-apt-repository -y ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get -y install libdb4.8-dev libdb4.8++-dev

sudo apt-get install libminiupnpc-dev
sudo apt-get install libzmq3-dev

sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler
sudo apt-get install libqrencode-dev

sudo apt install g++-mingw-w64-x86-64 libunivalue-dev

sudo apt install software-properties-common
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu zesty universe"
sudo apt update
sudo apt upgrade
sudo update-alternatives --config x86_64-w64-mingw32-g++ # Set the default mingw32 g++ compiler option to posix.


cd ~
git clone https://github.com/chips-blockchain/chips
cd chips/depends

make HOST=x86_64-w64-mingw32 -j$(nproc)

cd ..

./autogen.sh
./configure --prefix=$(pwd)/depends/x86_64-w64-mingw32 LDFLAGS="-L${CHIPS_PREFIX}/lib/" CPPFLAGS="-I${CHIPS_PREFIX}/include/" --with-gui=yes --disable-tests --disable-bench --without-miniupnpc --enable-experimental-asm --enable-static --disable-shared
make -j$(nproc)
```

### ARM64 - without QT wallet - Only CLI binaries

```
# https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md#arm-cross-compilation

sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools
sudo apt-get install libqrencode-dev
sudo apt-get install libminiupnpc-dev
sudo apt-get install libzmq3-dev
sudo apt-get install g++-aarch64-linux-gnu binutils-aarch64-linux-gnu

cd ~
git clone https://github.com/chips-blockchain/chips

cd chips/depends
make HOST=aarch64-linux-gnu -j$(nproc)
cd ..
./autogen.sh
./configure --prefix=$(pwd)/depends/aarch64-linux-gnu LDFLAGS="-L${CHIPS_PREFIX}/lib/" CPPFLAGS="-I${CHIPS_PREFIX}/include/" --with-gui=no --disable-tests --disable-bench --enable-upnp-default --enable-experimental-asm --enable-static --disable-shared
make -j$(nproc)
```
### ARM32 - without QT wallet - Only CLI binaries

```
# https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md#arm-cross-compilation

sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools
sudo apt-get install libqrencode-dev
sudo apt-get install libminiupnpc-dev
sudo apt-get install libzmq3-dev
sudo apt-get install g++-arm-linux-gnueabihf curl


cd ~
git clone https://github.com/chips-blockchain/chips
cd chips/depends
make HOST=arm-linux-gnueabihf -j$(nproc)
cd ..
./autogen.sh
./configure --prefix=$(pwd)/depends/arm-linux-gnueabihf LDFLAGS="-L${CHIPS_PREFIX}/lib/" CPPFLAGS="-I${CHIPS_PREFIX}/include/" --with-gui=no --disable-tests --disable-bench --enable-upnp-default --enable-experimental-asm --enable-static --disable-shared
make -j$(nproc)
```

### For Linux static builds, AMD64 - QT wallet

```
# https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md#arm-cross-compilation

sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools
sudo apt-get install libqrencode-dev
sudo apt-get install libminiupnpc-dev
sudo apt-get install libzmq3-dev
sudo apt-get install g++-aarch64-linux-gnu binutils-aarch64-linux-gnu


cd ~
git clone https://github.com/chips-blockchain/chips

To build dependencies for the current arch+OS:

cd chips/depends
make
cd ..

For 64bit Linux, it might make a dependency path something like `depends/x86_64-pc-linux-gnu`. Or better check the `depends/` directory and use that as path for your arch+OS.
So, based on 64bit linux can use `--prefix=$(pwd)/depends/x86_64-pc-linux-gnu`


./autogen.sh
./configure --prefix=$(pwd)/depends/x86_64-pc-linux-gnu LDFLAGS="-L${CHIPS_PREFIX}/lib/" CPPFLAGS="-I${CHIPS_PREFIX}/include/" --with-gui=no --disable-tests --disable-bench --enable-upnp-default --enable-experimental-asm --enable-static --disable-shared
make -j$(nproc)
```

### For Linux static builds - without QT wallet - Only CLI binaries

```
cd
git clone https://github.com/chips-blockchain/chips.git
cd ~/chips
./autogen.sh
./configure --with-boost=/usr/local/
cd src
make -j8 chipsd
make chips-cli
cp chips-cli /usr/bin # just need to get chips-cli to work from command line
# make -> will build everything, including QT wallet
sudo ldconfig /usr/local/lib # thanks smaragda!
./chipsd -addnode=5.9.253.195 &
```
