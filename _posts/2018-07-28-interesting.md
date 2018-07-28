---
layout: post
title: Building ROOT on Linux
---

ROOT is an open source modular scientific software framework that provides all the functionalities needed to deal with big data processing, statistical analysis, visualization and storage. Mainly written in C++, ROOT can be integrated with other languages such as Python and R as well.

Here I will explain how to build ROOT from scratch. I have Fedora 28 with KDE environment installed on my machine. The following procedure should work on all Linux configurations with little tweaks here and there.


### Download the latest source
The entire ROOT source can be obtained from ROOT's public Git repository:
{% highlight js %}
	git clone http://github.com/root-project/root.git
{% endhighlight %}
The release specific tag can be obtained using:
{% highlight js %}
	cd root
	git checkout -b v6-14-02 v6-14-02
{% endhighlight %}

Thanks!
