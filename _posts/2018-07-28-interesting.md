---
layout: post
title: Building ROOT on Linux
---

ROOT is an open source modular scientific software framework that provides all the functionalities needed to deal with big data processing, statistical analysis, visualization and storage. Mainly written in C++, ROOT can be integrated with other languages such as Python and R as well.

In this post I will explain how to build CERN's [ROOT](https://root.cern.ch/) from scratch. I have Fedora 28 with KDE environment installed on my machine. The following procedure should work on all Linux configurations with little tweaks here and there.


### Dependencies
Dependencies are the underlying programs a computer needs in order to build new programs. So here we download some prerequisites to build root.

Get the required packages using:
```bash
sudo dnf install git cmake gcc-c++ gcc binutils libX11-devel libXpm-devel libXft-devel libXext-devel
```

There are other optional packages you may want to install:
```bash
sudo dnf install gcc-gfortran openssl-devel pcre-devel \
mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
fftw-devel cfitsio-devel graphviz-devel \
avahi-compat-libdns_sd-devel libldap-dev python-devel \
libxml2-devel gsl-static
```

### Download the latest source
Once you have all the dependencies the next steps will be to download the ROOT source files and build them/install them. One can download the entire ROOT source from their [github](https://github.com/root-project/root). Now the question arises, "where to install?". If you want to use ROOT system-wide, it should be built on root mounts (for example,`/usr/local` or `/usr/share/`). Lets change directory to our install location.
```bash
cd /usr/local/
```
Download the source:
```bash
sudo git clone http://github.com/root-project/root.git
```
The release specific tag can be obtained using:
```bash
cd root
git checkout -b v6-14-02 v6-14-02
```
Or you can choose to the latest commit using
```bash
sudo git clone --depth 1 http://github.com/root-project/root.git
```
The `--depth 1` will ensure you that you checkout the latest version from their git source.


Here you go
```bash
#CERN ROOT
export ROOTSYS=/usr/local/root
export PATH=$ROOTSYS/bin:$PATH
export PYTHONDIR=$ROOTSYS
export LD_LIBRARY_PATH=$ROOTSYS/lib:$PYTHONDIR/lib:$ROOTSYS/bindings/pyroot:$LD_LIBRARY_PATH
export PYTHONPATH=$ROOTSYS/lib:$PYTHONPATH:$ROOTSYS/bindings/pyroot
```

again well well 1 1 1

Thanks!
