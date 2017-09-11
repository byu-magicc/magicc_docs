# Installing Ubuntu 14.04 Linux

Here are some basic instructions for installing Ubuntu and ROS:

## Installing Linux
Right now, we are running everything on Ubuntu 16.04 LTS, which is the most recent, long term support version. This should be a valid distribution to use until 2018 or so. Install that version of Ubuntu. You can make any computer a "dual boot" system, in which you can split your hard drive into two "patitions" and choose whether to boot into Ubuntu, or another operating system, such as Mac or Windows on startup. This tends to be the best solution to getting both operating systems on one machine. Creating a "virtual machine" inside another operating system is also an option, but that tends to reduce system performance and is all-around more difficult to get working.

The best ways to do this is probably to create a bootable USB drive. The first link is the link below leads to the operating system disk image. The second link allows you to copy that image to a USB stick and install ubuntu. There is usually one of these USB drives already floating around in the lab, so if you'll ask around, one of the other lab members can supply you with one if you don't want to go through the hassle of making your own.

* [OS Disk Image](http://www.ubuntu.com/download/desktop)
* [Bootable USB Maker](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
* [Thorough Guide to Installing Linux](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

All you have to do after creating the bootable USB image is put the disk in the USB slot and restart the computer. On some systems, you have to enter the BIOS to change which disk the computer first tries to boot from (enter the BIOS by pressing random "F" buttons at the top of the keyboard while the computer is booting up).

If your computer originally came with Windows 8, or came out after 2014, then you will have difficulty installing Ubuntu due to windows updating their bootloader to the new UEFI system. Talk to one of the more experienced lab members about getting a dual-boot setup working on your computer, because as of this date, external support for this procedure is not fabulous.

If you don't have experience using the command line, [this](http://linuxcommand.org/) is a pretty good tutorial that will help you get familiar with using the linux terminal.
