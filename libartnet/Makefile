# 
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libartnet
PKG_VERSION:=1.1.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://open-lighting.googlecode.com/files
PKG_SHA1SUM:=52835fb4860033b0719de24ee32c649ce9828730

include $(INCLUDE_DIR)/package.mk

define Package/libartnet
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Libartnet is an implementation of the ArtNet protocol.
  URL:=http://code.google.com/p/linux-lighting/
endef

define Package/libartnet/description
	Libartnet is an implementation of the ArtNet protocol. ArtNet allows the
	transmission of DMX and related data over IP networks.
endef	

define Build/Configure
	$(call Build/Configure/Default, \
		--prefix=/usr \
	)
endef

TARGET_CPPFLAGS:=-I. -I.. $(TARGET_CPPFLAGS)

TARGET_CFLAGS += $(FPIC)

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		all install
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/artnet $(1)/usr/include/
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libartnet.{la,a,so,so.1,so.1.0.0} $(1)/usr/lib/
endef

define Package/libartnet/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libartnet.{so,so.1,so.1.0.0} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libartnet))
