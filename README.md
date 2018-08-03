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
$ sudo apt-get install git git-svn bc binfmt-support automake autogen autoconf autotools-dev libtool shtool python m4 gcc libtool zlib1g-dev libelf-dev libxml2-dev python-yaml python-pygments pigz pxz
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

Install Prebuilt GCC 4.9

```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo apt-get install gcc-4.9 g++-4.9
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 100
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.9 100
```

Install prebuilt clang 6.0:

```bash
$ wget -O - http://llvm.org/apt/llvm-snapshot.gpg.key | sudo apt-key add -
$ echo 'deb http://llvm.org/apt/[trusty/xenial/artful/bionic]/ llvm-toolchain-[trusty/xenial/artful/bionic]-6.0 main' | sudo tee -a /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get install clang-6.0 lldb-6.0 lld-6.0
$ sudo update-alternatives --install /usr/bin/clang clang /usr/bin/clang-6.0 100
$ sudo update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-6.0 100
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
