#
# Copyright (C) 2021 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mongoose
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/TheRootED24/libmongoose.git
PKG-BRANCH=openwrt
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2024-07-28
			
PKG_SOURCE_VERSION:=fbb294824e06e33028922dc39843ac05a162ebd7

PKG_MIRROR_HASH:=de68883299c947b0513c66f082fc33db72c773d8dac5b8b61385abcd1fc6117a

PKG_MAINTAINER:=hostle <TheRootED24@gmail.com>
PKG_LICENSE:=MIT License

PKG_BUILD_FLAGS:=lto

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mongoose
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenWrt Mongoose C Networking shared Library
  DEPENDS:=+libopenssl
endef

TARGET_CFLAGS += -std=gnu99 -I$(STAGING_DIR)/usr/include/mongoose/

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/mongoose
	$(CP) \
		$(PKG_BUILD_DIR)/src/*.h \
		$(1)/usr/include/mongoose/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_BUILD_DIR)/src/libmongoose.so* \
		$(1)/usr/lib/
	
endef

define Package/mongoose/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/usr/lib/libmongoose.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,mongoose))
