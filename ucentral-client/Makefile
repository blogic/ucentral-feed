include $(TOPDIR)/rules.mk

PKG_NAME:=ucentral-client
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/blogic/ucentral-client.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-11-27
PKG_SOURCE_VERSION:=64f7415d39404ecfbf0cd0b4e2ecca162e481018

PKG_MAINTAINER:=John Crispin <john@phrozen.org>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/ucentral-client
  SECTION:=ucentral
  CATEGORY:=uCentral
  TITLE:=OpenWrt uCentral websocket client
  DEPENDS:=+ucentral-jsonschema +ucentral-schema \
  	   +ucode +ucode-mod-fs +ucode-mod-ubus +ucode-mod-uci \
	   +libubox +libwebsockets-openssl +libblobmsg-json +libubus
endef

define Package/ucentral-client/conffiles
/etc/ucentral/
/etc/config-shadow/
endef

define Package/ucentral-client/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/{ucentral,config,init.d,uci-defaults}
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ucentral $(1)/usr/sbin/
	$(INSTALL_BIN) ./files/ucentral_*.sh $(1)/usr/sbin/
	$(INSTALL_BIN) ./files/ucentral.init $(1)/etc/init.d/ucentral
	$(INSTALL_DATA) ./files/ucentral.config $(1)/etc/config/ucentral
	$(INSTALL_DATA) ./files/zzz-ucentral $(1)/etc/uci-defaults/
endef

$(eval $(call BuildPackage,ucentral-client))
