OLA OpenWrt Feed
================

This allows to compile and run [OLA](http://www.opendmx.net/index.php/Open_Lighting_Architecture)
on the [OpenWrt](https://openwrt.org/) Linux distribution. It has been successfully tested with the Asus WL-500W router.

In addition, a [boblight](https://code.google.com/p/boblight/)-fork with ola-support is also included. There's already an issue to [integrate ola support into boblight](https://code.google.com/p/boblight/issues/detail?id=9).

Please see the OpenWrt documentation at http://wiki.openwrt.org/doc/start and especially http://wiki.openwrt.org/doc/howto/build to better understand how this works.

_Patches and comments are welcome!_

Quick start
-----------

Make sure you have all the dependencies of the OpenWrt build system installed.

Checkout OpenWrt from svn (tested with r27259):

    mkdir openwrt
    cd openwrt
    svn co svn://svn.openwrt.org/openwrt/trunk .

Change feeds setup to inculde reference to this feed:

    cp feeds.conf.default feeds.conf
    echo "src-git ola git://github.com/doits/ola-openwrt-feed.git" >> feeds.conf

Update the feeds:

    scripts/feeds update

Include ola in the build:

    scripts/feeds install ola

Include other packages from feeds in the build. Perhaps:

    scripts/feeds install luci

Configure the build. Do not forget to select OLA:

    make menuconfig

Run build and go for a walk:

    make

TODO
----

Split the olad and its plugins into separate packages.
