#
# Copyright (C) 2020 Jo-Philipp Wich <jo@mein.io>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ucode
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/jow-/ucode.git
PKG_SOURCE_DATE:=2020-10-27
PKG_SOURCE_VERSION:=8b4d0d5d18c0b60ed3365f442385ee253981d5d4
PKG_MIRROR_HASH:=
PKG_MAINTAINER:=Jo-Philipp Wich <jo@mein.io>
PKG_LICENSE:=ISC

PKG_ASLR_PIE_REGULAR:=1
PKG_BUILD_DEPENDS = ustream-ssl
PKG_CONFIG_DEPENDS:= CONFIG_ucode_lua

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
include $(INCLUDE_DIR)/version.mk

define Package/ucode/default
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=ucode - Tiny template language
endef

define Package/ucode
  $(Package/ucode/default)
  DEPENDS:=+libjson-c
endef

define Package/ucode/description
 ucode is a tiny script interpreter featuring an ECMAScript oriented
 script language and Jinja-inspired templating.
endef


define Package/ucode-mod-fs
  $(Package/ucode/default)
  TITLE+= (filesystem module)
  DEPENDS:=ucode
endef

define Package/ucode-mod-fs/description
 The filesystem plugin module allows interaction with the local file system.
endef


define Package/ucode-mod-math
  $(Package/ucode/default)
  TITLE+= (math module)
  DEPENDS:=ucode
endef

define Package/ucode-mod-math/description
 The math plugin provides access to various <math.h> procedures.
endef


define Package/ucode-mod-ubus
  $(Package/ucode/default)
  TITLE+= (ubus module)
  DEPENDS:=ucode +libubus +libblobmsg-json
endef

define Package/ucode-mod-ubus/description
 The ubus module allows ucode template scripts to enumerate and invoke ubus
 procedures.
endef


define Package/ucode-mod-uci
  $(Package/ucode/default)
  TITLE+= (uci module)
  DEPENDS:=ucode +libuci
endef

define Package/ucode-mod-uci/description
 The uci module allows templates to read and modify uci configuration.
endef


define Package/ucode/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ucode $(1)/usr/bin/ucode
endef

define Package/ucode-mod-fs/install
	$(INSTALL_DIR) $(1)/usr/lib/ucode
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lib/fs.so $(1)/usr/lib/ucode/
endef

define Package/ucode-mod-math/install
	$(INSTALL_DIR) $(1)/usr/lib/ucode
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lib/math.so $(1)/usr/lib/ucode/
endef

define Package/ucode-mod-ubus/install
	$(INSTALL_DIR) $(1)/usr/lib/ucode
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lib/ubus.so $(1)/usr/lib/ucode/
endef

define Package/ucode-mod-uci/install
	$(INSTALL_DIR) $(1)/usr/lib/ucode
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lib/uci.so $(1)/usr/lib/ucode/
endef


$(eval $(call BuildPackage,ucode))
$(eval $(call BuildPackage,ucode-mod-fs))
$(eval $(call BuildPackage,ucode-mod-math))
$(eval $(call BuildPackage,ucode-mod-ubus))
$(eval $(call BuildPackage,ucode-mod-uci))
