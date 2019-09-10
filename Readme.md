# Build mod.io from source on centos 7.6

## install dependencies

```
yum install git wget centos-release-scl curl-devel nano
yum-config-manager --enable rhel-server-rhscl-7-rpms
yum install devtoolset-7
scl enable devtoolset-7 bash
```

## install curl 3.14

```
wget https://github.com/Kitware/CMake/releases/download/v3.14.6/cmake-3.14.6.tar.gz
tar -zxvf cmake-3.14.6.tar.gz 
cd cmake-3.14.6
./bootstrap --prefix=/usr/local
make
make install
nano ~/.bash_profile # append this to the end: PATH=/usr/local/bin:$PATH:$HOME/bin
source ~/.bash_profile
```

## compile mod.io

```
cd
git clone https://github.com/modio/SDK.git
cd SDK/
mkdir build
cd build/
cmake ..
make
```

The library is now located at ~/SDK/build/libmodio.so

# Grabbing the precompiled binary

Alternatively just grab the `libmodio.so` on this repo and isntall `curl-devel`.

```
yum install curl-devel
````