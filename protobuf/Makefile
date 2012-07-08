# 
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=protobuf
PKG_VERSION:=2.4.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://protobuf.googlecode.com/files
PKG_MD5SUM:=dc84e9912ea768baa1976cb7bbcea7b5

PKG_BUILD_DEPENDS:=protobuf/host

PKG_INSTALL:=1

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/libprotobuf
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Protocol Buffers
  URL:=http://code.google.com/p/protobuf/
  DEPENDS:=+libpthread +libstdcpp +zlib
endef

CONFIGURE_ARGS += --with-protoc=protoc

define Package/libprotobuf/description
	Protocol Buffers are a way of encoding structured data in an efficient 
	yet extensible format. Google uses Protocol Buffers for almost all of 
	its internal RPC protocols and file formats.
	
	This package contains the full library.
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/google $(1)/usr/include/
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libprotobuf* $(1)/usr/lib/
	mkdir -p $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/protobuf*.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libprotobuf/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libprotobuf.so* $(1)/usr/lib/
endef

define Host/Compile
	$(MAKE) -C $(HOST_BUILD_DIR)
endef

define Host/Install
	$(MAKE) -C $(HOST_BUILD_DIR) install
endef

define Host/Clean
	-$(MAKE) -C $(HOST_BUILD_DIR) uninstall
	$(call Host/Clean/Default)
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,libprotobuf))
