include $(TOPDIR)/rules.mk

PKG_NAME:=ucentral-schema
PKG_RELEASE:=1

PKG_SOURCE_URL=https://github.com/blogic/ucentral-schema.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-11-27
PKG_SOURCE_VERSION:=42662a247f3b85cd38f6f33d155e8a831af9d7b8

PKG_MAINTAINER:=John Crispin <john@phrozen.org>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

define Package/ucentral-schema
  SECTION:=ucentral
  CATEGORY:=uCentral
  TITLE:=OpenWrt uCentral schema
endef

define Build/Compile

endef

define Package/ucentral-schema/install
	$(INSTALL_DIR) $(1)/usr/share/ucentral
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/ucentral.schema.json $(1)/usr/share/ucentral
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/sys/*.uc $(1)/usr/share/ucentral
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/cmd/*.uc $(1)/usr/share/ucentral
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/cfg/*.uc $(1)/usr/share/ucentral
endef

$(eval $(call BuildPackage,ucentral-schema))
