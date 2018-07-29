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

### Building ROOT
```bash
cd root
#Create a directory where you want to compile
mkdir rootBuild
```
Now if the system complains about you not being a super user `sudo`, you can choose to unlock the folder permissions back to you as a user. Just try this command line
```bash
#go one step up from root directory
cd ..
#change ownership to yourself (no sudo command needed later)
sudo chown -R $(whoami)"$(id -g -n $(whoami)) " root
```
Now go to the downloaded directory `root` one more time and try to create a new directory:
```bash
cd root
mkdir rootBuild
##It should not complain now
cd rootBuild
cmake -Dpython=ON -Droofit=ON -DCMAKE_INSTALL_PREFIX:PATH=/usr/local/root ..
make -j$(nproc)
sudo make install
```

### Install ROOT
Now install the source:
```bash
cd /usr/local/root
source bin/thisroot.sh
```
Now add these lines to your `.bashrc` file. You can access it at `~/.bashrc`
```bash
#ROOT CERN environment variables
export ROOTSYS=/usr/local/root
export PATH=$ROOTSYS/bin:$PATH
export PYTHONDIR=$ROOTSYS
export LD_LIBRARY_PATH=$ROOTSYS/lib:$PYTHONDIR/lib:$ROOTSYS/bindings/pyroot:$LD_LIBRARY_PATH
export PYTHONPATH=$ROOTSYS/lib:$PYTHONPATH:$ROOTSYS/bindings/pyroot
```
You are all set. Try running root `root -l`. To check if ROOT is also installed for python properly, you can run an interactive session and try to import ROOT:
```bash
python
>>> import ROOT
```
If there are no import errors, then you are ready to use ROOT.

Have fun!
Thanks for reading!
