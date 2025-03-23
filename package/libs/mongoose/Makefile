include $(TOPDIR)/rules.mk

PKG_NAME:=mongoose
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2025-03-22
PKG_SOURCE_URL=https://github.com/TheRootED24/libmongoose.git

PKG_MIRROR_HASH:=d1505aeb869ab7b39118d4de346d1384b6e31eec4e60fd04ec1be9e68eb46d44
PKG_SOURCE_VERSION:=49dfd34a52348e71a2844e93c0ee18c8dd10cf23

PKG_MAINTAINER:=hostle <TheRootED24@gmail.com>
PKG_LICENSE:=MIT License

PKG_BUILD_FLAGS:=lto

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mongoose
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Mongoose C/C++ Networking Library
  DEPENDS:=+libmbedtls
endef

define Package/mongoose/description
  Mongoose is a network library for C/C++. It provides event-driven non-blocking APIs for TCP, UDP, HTTP,
  WebSocket, MQTT, and other protocols. It is designed for connecting devices and bringing them online.
  Mongoose makes embedded network programming fast, robust, and easy.
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include/mongoose/

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
