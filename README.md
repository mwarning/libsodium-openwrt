libsodium-openwrt
=================

A simple (OpenWrt)[https://openwrt.org] package for the (libsodium)[https://github.com/jedisct1/libsodium] library.
The code is released under Public Domain.


# How to build

These commands show how to build libsodium
<pre>
git clone git://git.openwrt.org/12.09/openwrt.git
cd openwrt

./scripts/feeds update -a
./scripts/feeds install -a

https://github.com/mwarning/libsodium-openwrt.git
cp -r /libsodium-openwrt/libsodium package/
rm -rf libsodium-openwrt

make defconfig
make menuconfig
#select target hardware and libs => libsodium
make
</pre>

This package does only build libsodium as part of the build environment.
That means that libsodium will be only included when linked as static
library by some other program.

That is why we have no release libsodium packages here.
But that would be possible when the script would be changed
to create a dynamic library.

Static linking makes sense when not all parts of libsodium are used since
OpenWrt is used for embedded devices (mostly WLAN-routers).
When libsodium is linked by  multiple programs then those parts
are compressed by the filesystem to take up space only one time.
