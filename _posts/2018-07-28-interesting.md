---
layout: post
title: Building ROOT on Linux
---

ROOT is an open source modular scientific software framework that provides all the functionalities needed to deal with big data processing, statistical analysis, visualization and storage. Mainly written in C++, ROOT can be integrated with other languages such as Python and R as well.

In this post I will explain how to build CERN's [ROOT](https://root.cern.ch/) from scratch. I have Fedora 28 with KDE environment installed on my machine. The following procedure should work on all Linux configurations with little tweaks here and there.


### Download the latest source
The entire ROOT source can be obtained from ROOT's public Git repository:
{% highlight js %}
$ git clone http://github.com/root-project/root.git
{% endhighlight %}
The release specific tag can be obtained using:
{% highlight js %}
$ cd root
$ git checkout -b v6-14-02 v6-14-02
{% endhighlight %}

### Dependencies
Dependencies are the underlying programs a computer needs in order to build new programs. So here we download some prerequisites to build root.

Get the required packages using:
{% highlight sh %}
$ sudo dnf install git cmake gcc-c++ gcc binutils libX11-devel libXpm-devel libXft-devel libXext-devel
{% endhighlight %}

There are other optional packages you may want to install:
{% highlight sh %}
$ sudo yum install gcc-gfortran openssl-devel pcre-devel \
mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
fftw-devel cfitsio-devel graphviz-devel \
avahi-compat-libdns_sd-devel libldap-dev python-devel \
libxml2-devel gsl-static
{% endhighlight %}

~~~~
$ sudo dnf install git cmake gcc-c++ gcc binutils libX11-devel libXpm-devel libXft-devel libXext-devel
$ sudo yum install gcc-gfortran openssl-devel pcre-devel \
mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
fftw-devel cfitsio-devel graphviz-devel \
avahi-compat-libdns_sd-devel libldap-dev python-devel \
libxml2-devel gsl-static
~~~~

<pre><code>$ sudo dnf install git cmake gcc-c++ gcc binutils libX11-devel libXpm-devel libXft-devel libXext-devel 
</code></pre>

Thanks!
