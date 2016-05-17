*libsodium is in the openwrt package feed now and maintenance will happen there*

libsodium-openwrt
=================

A simple [OpenWrt](https://openwrt.org) package for the [libsodium](https://github.com/jedisct1/libsodium) library.
The code is released under the GPLv2 license.

### Where to download packages?

Check the [release section](https://github.com/mwarning/libsodium-openwrt/releases) for the most recent release!

### How to build a OpenWrt .ipk package?

These commands show how to build an OpenWrt image and .ipk package of libsodium
<pre>
git clone git://git.openwrt.org/14.07/openwrt.git
cd openwrt

echo "src-git libsodium git://github.com/mwarning/libsodium-openwrt.git" >> feeds.conf.default

./scripts/feeds update -a
./scripts/feeds install -a

make defconfig
make menuconfig
</pre>

You are now shown the OpenWrt configuration interface.
Select the appropiate "Target System" and "Target Profile".
This depends on what target chipset/router you want to build for.
Here is an example on what you might want to select:

<pre>
Target System (Atheros AR7xxx/AR9xxx)
Target Profile (TP-LINK TL-WR841N/ND)
Libraries  ---> <*> libsodium
</pre>

Exit and save the settings. Then build the packages/images:

<pre>
make
</pre>

The ipk packages can now be found in `bin/ar71xx/packages/`.
