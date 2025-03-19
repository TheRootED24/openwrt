include $(TOPDIR)/rules.mk

PKG_NAME:=glinet-uboot-scr
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/TheRootED24/glinet-uboot-scr.git
PKG_MIRROR_HASH:=0a955d4cf30721eeadea6616e56fdbd217428d1d03a2dbfd1f6c073acdd14f28
PKG_SOURCE_VERSION:=95c40784aa5eeb309423bab1f06703928849e652
PKG_SOURCE_DATE:=2025-03-19

PKG_MAINTAINER:=Scott Mercer <TheRootED24@gmail.com>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/glinet-uboot-scr
	SECTION:=utils
	CATEGORY:=Utilities
	SUBMENU:=Boot Loaders
	TITLE:= Uboot flash.scr Files
	URL:=https://github.com/TheRootED24/glinet-uboot-scr.git
endef

define Package/glinet-uboot-scr/description
  This package contains the uboot scr file needed to
  enable uboot webui recovery and firmware upgrades
  for OpenWrt Firmwares.

           REQUIRED INSTALLATION NOTES

  This package MUST be included <*> in the firmware to
  effectively enable uboot webui recovery and upgrades
  for Openwrt.

  Installation of this package post-build will have
  zero effect and will not enable uboot upgrades and
  recovery options for Openwrt Firmwares.
endef

MAKE_PATH:=src

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/glinet-uboot-scr
	$(CP) \
		$(PKG_BUILD_DIR)/src/*.scr \
		$(1)/usr/include/glinet-uboot-scr/
endef

$(eval $(call BuildPackage,glinet-uboot-scr))
