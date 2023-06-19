# WiringPi

This is an unofficial fork of another unofficial fork [wiringPi](https://github.com/WiringPi/WiringPi) of the original [wiringPi](http://wiringpi.com/).

  * The last "official" source release can be found at the [`final_source_2.50`](https://github.com/WiringPi/WiringPi/tree/final_official_2.50) tag.
  * Debian/Ubuntu builds of this fork is available using [Open Build Service](https://software.opensuse.org//download.html?project=home%3Ambhangui%3Araspi&package=wiringPi)

# Installation

## Source Installation

```
$ cd /usr/local/src
$ git clone --no-tags --no-recurse-submodules --depth=1 https://github.com/mbhangui/wiringPi
$ cd wiringPi
$ ./default.configure
$ make && sudo make install-strip
```

## Create RPM package

This is done by running the create\_rpm / create\_debian scripts. (Here `version` refers to the existing version of wiringPi package)

### Create debian package

```
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
-rw-rw-r--. 1 pi pi  290567 Feb  8 09:05 wiringpi-3.0-1.1.fc38.x86_64.rpm
```

### Create debian package

```
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
```

## Prebuilt Binaries

[![wiringPi](https://build.opensuse.org/projects/home:mbhangui:raspi/packages/wiringPi/badge.svg?type=percent)](https://build.opensuse.org/package/show/home:mbhangui:raspi/wiringPi)

Prebuilt binaries using openSUSE Build Service are available for wiringPi for

* Debian 10 (including ARM images for Debian 10 which work (and tested) for RaspberryPI (model 2,3))
* Raspbian 10 and 11 for RaspberryPI (arm and aarch64 images)
* Ubuntu 20, 22, 23 (arm and aarch64 images)

Use the below url for installation

[download](https://software.opensuse.org//download.html?project=home%3Ambhangui%3Araspi&package=wiringPi)

# Support

Please do not email Gordon if you have issues, he will not be able to help. Feel free to create an [issue](https://github.com/mbhangui/wiringPi/issues/new/choose).
