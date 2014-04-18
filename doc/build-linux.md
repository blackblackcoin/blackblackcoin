Building on Linux
===============

To install the required dependencies, run the following command:

$ sudo apt-get install git-core build-essential libssl-dev libboost-all-dev libdb5.1-dev libdb5.1++-dev libgtk2.0-dev libminiupnpc-dev qt4-qmake mingw32 synaptic qt-sdk qt4-dev-tools libqt4-dev libqt4-core libqt4-gui libdb++-dev miniupnpc

Then grab the latest version of the BBCoin source code from Github

$ git clone https://github.com/BBC-Coin/BBCoin.git

To build the daemon, run the following commands

$ cd BBCoin/src

$ make -f makefile.unix

Optionally, debugging symbols can be removed from the binary to reduce it's size. This can be done using strip.

$ strip BBCoind

Then, to build the GUI, run the following commands:

$ cd ..

$ qmake

$ make

Troubleshooting:
-------------

Building miniupnpc
----------------

If your OS doesn't support libminiupnpc, you can build this manually by performing the following steps:

Don't use miniupnpc-1.6 as its broken an qmake compilation will fail to build BBCoin-QT.

$ wget 'http://miniupnp.free.fr/files/download.php?file=miniupnpc-1.5.tar.gz' -O miniupnpc-1.5.tar.gz

$ tar -xzvf miniupnpc-1.5.tar.gz

$ cd miniupnpc-1.5
	
$ make

$	make install

Cleaning the build:
----------------=

If you have to clean your build environment you may have to rebuild LevelDB manually. This can be done using:

$ cd src/leveldb

$ chmod +x build_detect_platform

$ ./build_detect_platform

Ignore the usage errors (it still builds the relevent file) and now run:

$ make libleveldb.a libmemenv.a
