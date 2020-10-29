### Installing depencies
```
sudo apt-get install software-properties-common autoconf git build-essential libtool libprotobuf-c-dev libgmp-dev libsqlite3-dev python python3 zip jq libevent-dev pkg-config libssl-dev libcurl4-gnutls-dev cmake
add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install -y libdb4.8-dev libdb4.8++-dev
```
### Installing boost libraries
```
cd
wget https://dl.bintray.com/boostorg/release/1.64.0/source/boost_1_64_0.zip
unzip boost_1_64_0.zip
cd boost_1_64_0
./bootstrap.sh
./b2
./b2 install
```
### Compiling and running CHIPS node
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
