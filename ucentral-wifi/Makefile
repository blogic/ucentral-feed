include $(TOPDIR)/rules.mk

PKG_NAME:=ucentral-wifi
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/blogic/ucentral-wifi.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-11-27
PKG_SOURCE_VERSION:=652db65912a1a585be58d800cc22080e67657af3

PKG_MAINTAINER:=John Crispin <john@phrozen.org>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/ucentral-wifi
  SECTION:=ucentral
  CATEGORY:=uCentral
  TITLE:=OpenWrt wifi status daemon
  DEPENDS:=+libubox +libubus +libnl-tiny
endef

TARGET_CFLAGS += \
	-I$(STAGING_DIR)/usr/include \
	-I$(STAGING_DIR)/usr/include/libnl-tiny

define Package/ucentral-wifi/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ucentral-wifi $(1)/usr/sbin/
	$(INSTALL_BIN) ./files/ucentral-wifi $(1)/etc/init.d/
endef

$(eval $(call BuildPackage,ucentral-wifi))
