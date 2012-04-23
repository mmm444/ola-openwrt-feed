#
# Copyright (C) 2006-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ola
PKG_VERSION:=0.8.18
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://linux-lighting.googlecode.com/files
PKG_MD5SUM:=45310779932a2e015fa335e2f541438a

PKG_FIXUP:=libtool
PKG_INSTALL:=1

PKG_BUILD_DEPENDS:=protobuf/host

include $(INCLUDE_DIR)/package.mk

define Package/ola
  SECTION:=ola
  CATEGORY:=Open Lighting Architecture
  TITLE:=Open Lighting Architecture Daemon
  URL:=http://code.google.com/p/linux-lighting/
  DEPENDS:=+libartnet +libprotobuf +libmicrohttpd +libusb-1.0 +libuuid +libstdcpp +libpthread +librt +zlib +libncurses
endef

define Package/ola/description
  OLA (Open Lighting Architecture) is a framework that allows applications to 
  send and receive DMX512, using various hardware devices and 'DMX over IP'
  protocols. It enables software controllers talk to DMX hardware.
endef

define Build/Configure
  $(call Build/Configure/Default,--disable-dependency-tracking --disable-static --disable-slp)
endef

define Package/ola/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/lib/olad
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/olad/*.so* $(1)/usr/lib/olad
	$(INSTALL_DIR) $(1)/usr/share/olad/www
	$(CP) $(PKG_INSTALL_DIR)/usr/share/olad $(1)/usr/share
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/olad.init $(1)/etc/init.d/olad
endef

$(eval $(call BuildPackage,ola))
