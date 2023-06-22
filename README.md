# WiringPi

[![wiringpi C/C++ CI](https://github.com/mbhangui/wiringPi/actions/workflows/wiringpi-c-cpp.yml/badge.svg)](https://github.com/mbhangui/wiringPi/actions/workflows/wiringpi-c-cpp.yml)

This is an unofficial fork of another unofficial fork [wiringPi](https://github.com/WiringPi/WiringPi) of the original [wiringPi](http://wiringpi.com/).

  * The last "official" source release can be found at the [`final_source_2.50`](https://github.com/WiringPi/WiringPi/tree/final_official_2.50) tag.
  * The last "unofficial" release is more than a year old [Version 2.61-1](https://github.com/WiringPi/WiringPi/releases/tag/2.61-1)
  * Development of the "official" version ended as per this [post](https://web.archive.org/web/20220405225008/http://wiringpi.com/wiringpi-deprecated/)
  * I have updated this fork with few of the pull requests submitted to the [unofficial fork](https://github.com/WiringPi/WiringPi). I know C programming and I know how to created RPM, Debian and archlinux packages. But I have zero knowledge of hardware side of things and how wiringpi really works. So I welcome contributions from knowledgeable folks. My contribution would be to have the binary builds updated and synced with the source code. See this [commit](https://github.com/WiringPi/WiringPi/commit/7b92b3bad9cc2f122be36cc4d207c04f86dd9bf5)
  * Taking into account the points above, I have made this fork to support my [lcd-daemon](https://github.com/mbhangui/lcd-daemon) package which uses wiringPi. The package installs lcdDaemon - a daemon that runs continuously on a Raspberry PI. Any user/program on the network can print to a 16x2, 20x4 LCD using Hitachi HD44780 driver, using the pilcd command. I use the LCD to display songs being played on any of my Raspberry PIs in my house.
  * Debian/Ubuntu builds of this fork is available using [Open Build Service](https://software.opensuse.org//download.html?project=home%3Ambhangui%3Araspi&package=wiringpi)
  * If you find any bugs, that will be because of me. Do not harass the Gorodon for that.
  * Last but not the least, <b>A Big Thank You to Gordon Henderson for writing wiringPi</b>. This was the thing that got me hooked to Raspberry PI way back in 2014. I do not know Gordon personally but he got me inspired to use Raspberry PIs for playing Music throughout my house. See my [mpdev](https://github.com/mbhangui/mpdev) and [pistop](https://github.com/mbhangui/pistop) projects.

# Installation

## Source Installation

```
$ cd /usr/local/src
$ git clone --no-tags --no-recurse-submodules --depth=1 https://github.com/mbhangui/wiringPi
$ cd wiringPi
$ ./default.configure
$ make && sudo make install-strip
```

## Create RPM/Debian package

This is done by running the create\_rpm / create\_debian scripts. (Here `version` refers to the existing version of wiringPi package)

### Create RPM package

```
To create the RPM package run the create_rpm command

$ pwd
/usr/local/src/wiringPi
$ ./create_rpm
$ ls -l $HOME/rpmbuild/RPMS/x86_64/*wiringpi*
-rw-r--r--. 1 pi pi 42307 Jun 19 17:41 /home/pi/rpmbuild/RPMS/x86_64/libwiringpi-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 83713 Jun 19 17:40 /home/pi/rpmbuild/RPMS/x86_64/libwiringpi-debuginfo-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 25834 Jun 19 17:41 /home/pi/rpmbuild/RPMS/x86_64/libwiringpidev-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 37499 Jun 19 17:40 /home/pi/rpmbuild/RPMS/x86_64/libwiringpidev-debuginfo-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 31361 Jun 19 17:41 /home/pi/rpmbuild/RPMS/x86_64/libwiringpidev-devel-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 62002 Jun 19 17:41 /home/pi/rpmbuild/RPMS/x86_64/libwiringpi-devel-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 36584 Jun 19 17:41 /home/pi/rpmbuild/RPMS/x86_64/wiringpi-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 40876 Jun 19 17:40 /home/pi/rpmbuild/RPMS/x86_64/wiringpi-debuginfo-3.0-1.1.fc38.x86_64.rpm
-rw-r--r--. 1 pi pi 80848 Jun 19 17:40 /home/pi/rpmbuild/RPMS/x86_64/wiringpi-debugsource-3.0-1.1.fc38.x86_64.rpm

To install run the rpm command.

$ sudo rpm -ivh /home/pi/rpmbuild/RPMS/x86_64/wiringpi-3.0-1.1.fc38.x86_64.rpm \
    /home/pi/rpmbuild/RPMS/x86_64/libwiringpi-3.0-1.1.fc38.x86_64.rpm \
    /home/pi/rpmbuild/RPMS/x86_64/libwiringpidev-3.0-1.1.fc38.x86_64.rpm

If you are going to write/build applications that use the libwiringi
library then you need to install the development headers.

$ sudo rpm -ivh /home/pi/rpmbuild/RPMS/x86_64/libwiringpi-devel-3.0-1.1.fc38.x86_64.rpm \
    /home/pi/rpmbuild/RPMS/x86_64/libwiringpidev-devel-3.0-1.1.fc38.x86_64.rpm
```

### Create Debian package

```
To create the debian package run the create_debian command

$ pwd
/usr/local/src/wiringPi
$ ./create_debian
$ ls -l $HOME/stage/*wiring*
total 44
drwxr-xr-x  3 pi pi 4096 Jun 19 18:35 .
drwxr-xr-x 24 pi pi 4096 Jun 19 18:24 ..
-rw-r--r--  1 pi pi 2272 Jun 19 18:35 libwiringpi_3.0-1.1_arm64.deb
-rw-r--r--  1 pi pi 2296 Jun 19 18:35 libwiringpi-dev_3.0-1.1_arm64.deb
-rw-r--r--  1 pi pi 2468 Jun 19 18:35 libwiringpidev_3.0-1.1_arm64.deb
-rw-r--r--  1 pi pi 2484 Jun 19 18:35 libwiringpidev-dev_3.0-1.1_arm64.deb
-rw-r--r--  1 pi pi 6059 Jun 19 18:35 wiringpi_3.0-1.1_arm64.buildinfo
-rw-r--r--  1 pi pi 2552 Jun 19 18:35 wiringpi_3.0-1.1_arm64.changes
-rw-r--r--  1 pi pi 2344 Jun 19 18:35 wiringpi_3.0-1.1_arm64.deb

To install run the dpkg command.

$ sudo dpkg -i /home/i/stage/wiringpi_3.0-1.1_arm64.deb \
    /home/pi/stage/libwiringpi_3.0-1.1_arm64.deb\
    /home/pi/stage/libwiringpidev_3.0-1.1_arm64.deb

If you are going to write/build applications that use the libwiringi
library then you need to install the development headers.

$ sudo dpkg -i /home/pi/stage/libwiringpi-dev_3.0-1.1_arm64.deb\
    /home/pi/stage/libwiringpidev-dev_3.0-1.1_arm64.deb

```

## Prebuilt Binaries

[![build result](https://build.opensuse.org/projects/home:mbhangui:raspi/packages/wiringpi/badge.svg?type=percent)](https://build.opensuse.org/package/show/home:mbhangui:raspi/wiringpi)

Prebuilt binaries using openSUSE Build Service are available for wiringpi for

* Debian 10 (including ARM images for Debian 10 which work (and tested) for RaspberryPI (model 2,3))
* Raspbian 10 and 11 for RaspberryPI (arm and aarch64 images)
* Ubuntu 20, 22, 23 (arm and aarch64 images)

Use the below url for installation

[download](https://software.opensuse.org//download.html?project=home%3Ambhangui%3Araspi&package=wiringpi)

The above instructions will help you add the OBS repo in /etc/apt/sources.list.d for debian systems or /etc/yum.repos.d for rpm based systems. Once you have the repo, you can can install using the apt-get or the yum/dnf command

**For debian based systems**

```
$ sudo apt-get update && sudo apt-get install wiringpi
```

**For RPM based systems**

```
$ sudo dnf update && sudo dnf install wiringpi
```

# Support

Please do not email Gordon if you have issues, he will not be able to help. Feel free to create an [issue](https://github.com/mbhangui/wiringPi/issues/new/choose) on github instead.

I'm also available on [matrix](https://matrix.to/#/#Manvendra:matrix.org) where you can leave a message if you have any issue.
