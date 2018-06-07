# CLANG toolchain build script

This is a script to build CLANG toolchains targeting arm, arm64, and x86 devices
based on [nathanchance's scripts](https://github.com/nathanchance/scripts/blob/master/build-clang).


## Using the script

To build a toolchain, you will need to the
following:

+ A Linux distribution
+ A decent processor and RAM (i5 and 8GB of RAM or more is preferred)
+ Core developer packages

For Debian and Ubuntu:
```
$ sudo apt-get install build-essential git git-svn bc binfmt-support libllvm-3.6-ocaml-dev llvm-3.6 llvm-3.6-dev llvm-3.6-runtime automake autogen autoconf autotools-dev libtool shtool python m4 gcc libtool zlib1g-dev
```

Install CMake 3.4.3:

```bash
$ wget http://www.cmake.org/files/v3.4/cmake-3.4.3.tar.gz
$ tar xf cmake-3.4.3.tar.gz
$ cd cmake-3.4.3
$ ./bootstrap && make && sudo make install
```

Install subversion 1.10.0:

```bash
$ sudo sh -c 'echo "deb http://opensource.wandisco.com/ubuntu `lsb_release -cs` svn110" >> /etc/apt/sources.list.d/subversion110.list'
$ sudo wget -q http://opensource.wandisco.com/wandisco-debian.gpg -O- | sudo apt-key add -
$ sudo apt-get update && sudo apt-get install subversion
```

Install prebuilt clang 3.8.0:

```bash
$ wget -O - http://llvm.org/apt/llvm-snapshot.gpg.key|sudo apt-key add -
$ echo 'deb http://llvm.org/apt/trusty/ llvm-toolchain-trusty-3.8 main' | sudo tee -a /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get install clang-3.8 lldb-3.8
$ sudo update-alternatives --install /usr/bin/clang clang /usr/bin/clang-3.8 100
$ sudo update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-3.8 100
```


Once you have set up your environment, run the following to build clang:

```bash
$ git clone https://github.com/khusika/build-tools-clang
$ cd build-tools-clang
$ ./build-clang
```

## Credits/thanks

+ [nathanchance](https://github.com/nathanchance): For great script!
+ [krasCGQ](https://github.com/krasCGQ): For some modifications to update the script/components
