#
# Copyright (C) 2021 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mgjson
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/TheRootED24/mgjson.git
PKG-BRANCH=openwrt
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2024-08-13
			
PKG_SOURCE_VERSION:=2dc18a96e6ecefb60bd00e75736fbbebefe74ba7

PKG_MIRROR_HASH:=ad53bb5bb663012c35456bcbac115e16662984acc6368418d402036bc5453fb9

PKG_MAINTAINER:=hostle <TheRootED24@gmail.com>
PKG_LICENSE:=MIT License

PKG_BUILD_FLAGS:=lto

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mgjson
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Stripped down OpenWrt version of Mongoose C Networking built as a shared Library
endef

TARGET_CFLAGS += -std=gnu99 -I$(STAGING_DIR)/usr/include/mgjson/

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/mgjson
	$(CP) \
		$(PKG_BUILD_DIR)/src/*.h \
		$(1)/usr/include/mgjson/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_BUILD_DIR)/src/libmgjson.so \
		$(1)/usr/lib/
	
endef

define Package/mgjson/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/usr/lib/libmgjson.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,mgjson))
