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
git clone -n https://github.com/Turupawn/modioSDK.git # clone the specific commit you're lookingo for
cd modioSDK/
git checkout 0a0e040831d600cf8b0cd938eb90df5d4a26ce3c
# git clone https://github.com/modio/SDK.git # alternatively use the current official mod.io version
mkdir build
cd build/
cmake ..
make
```

The library is now located at ~/modioSDK/build/libmodio.so

# Grabbing the precompiled binary

Alternatively just grab the [libmodio.so](https://github.com/Turupawn/ModioCentos7BuildInstructions/raw/master/libmodio.so) on this repo and install `curl-devel`.

```
yum install curl-devel
````
