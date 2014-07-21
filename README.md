libsodium-openwrt
=================

A simple [OpenWrt](https://openwrt.org) package for the [libsodium](https://github.com/jedisct1/libsodium) library.
The code is released under the GPLv2 license.

### How to build a OpenWrt .ipk package

These commands show how to build an OpenWrt image and .ipk package of libsodium
<pre>
git clone git://git.openwrt.org/openwrt.git
cd openwrt

./scripts/feeds update -a
./scripts/feeds install -a

echo "src-git libsodium git://github.com/mwarning/libsodium-openwrt.git" >> feeds.conf

make defconfig
make menuconfig
</pre>

You are now shown the OpenWrt configuration interface.
Select the appropiate "Target System" and "Target Profile".
This depends on what target chipset/router you want to build for.
You also need to select the OpenWrt SDK option and libsodium:

<pre>
Target System (Atheros AR7xxx/AR9xxx)
Target Profile (TP-LINK TL-WR841N/ND)
[*] Build the OpenWrt SDK
Libraries  ---> <*> libsodium
</pre>

Exit and save the settings. Then build the packages/images:

<pre>
make
</pre>

The ipk packages can now be found in `bin/ar71xx/packages/libsodium_0.6.1-1_ar71xx.ipk`.
