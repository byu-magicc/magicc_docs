# ROS
This PowerPoint gives a basic overview of what ROS is and why it is used: [ROS Tutorial PowerPoint](http://magiccvs.byu.edu/ROS_Tutorial.pptx)

# ROS Versions
A new version of ROS is released every year.  Every two years, a Long-Term Support (LTS) version is released.  The LTS version released in 2016 was ROS kinetic, a new version was released in 2017, called Lunar, but Lunar is not LTS, meaning that support for that distribution (distro) will end in April 2018.  Updating ROS distributions can be pretty time-consuming, so to avoid frequent updates, we generally use only the LTS versions of ROS.  As of this writing, we are using kinetic.  _Don't install Luanr_.  It will get confusing to everyone if you install Lunar and your code has weird bugs.

Ubuntu has a similar release schedule, but it is released every 6 months.  Ubuntu 16.04 LTS (April, 2016) Xenial Xerus is the current LTS version that we use, soon to be replaced by Ubuntu 18.04 (April, 2018).  There have been several Ubuntus released since 16.04.  Namely 16.10, 17.04, and 17.10.  (the first two digits are the year, the last two are the month).  Just like ROS, we use 16.04.  It may be tempting to try the latest distribution, but ROS doesn't always support other releases besides the LTS.  To be safe, just stick with the LTS versions.

# Linux Mint, Elementary OS and other distros
There are several variants of Linux, all of which have their own pros and cons.  Theoretically, since many of these distros are based on Debian (which is what Ubuntu is based on), and many of them are based directly on Ubuntu, they will be compatible with ROS.  If you're just getting started, I would not recommend using one of these distros to develop ROS with.  They are kinda fun to toy around with, but don't expect everything to work well, because not all Linux distros are created equal.  Last I checked, Linux Mint was based on Ubuntu 15.10 or something, and Elementary OS is based on 15.10 too, which means only Jade is supported, but don't take my word for it.

# Installing Linux and ROS

Here are links to other pages that go through installing Ubuntu and ROS

- [Installing Ubuntu](getting_started/installing_ubuntu_16.04.md)
- [Installing ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu)
