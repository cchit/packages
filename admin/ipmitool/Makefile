#
# Copyright (C) 2017 Alexander Couzens <lynxis@fe80.eu>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ipmitool
PKG_VERSION:=1.8.18
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/$(PKG_NAME)
PKG_HASH:=0c1ba3b1555edefb7c32ae8cd6a3e04322056bc087918f07189eeedfc8b81e01
PKG_LICENSE:=BSD-3-clause
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define Package/ipmitool
  SECTION:=admin
  CATEGORY:=Administration
  DEPENDS:=+libopenssl +libncurses +libreadline
  TITLE:=Command-line interface to IPMI-enabled devices
  URL:=http://sourceforge.net/projects/ipmitool/
  MAINTAINER:=Alexander Couzens <lynxis@fe80.eu>
endef

define Package/ipmitool/Default/description
	Command-line interface to IPMI-enabled devices
endef

define Package/ipmitool/install
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ipmievd $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ipmitool $(1)/usr/sbin/
endef

define Package/ipmitool/conffiles
endef

CONFIGURE_ARGS += \
	--enable-intf-lan \
	--enable-intf-lanplus \
	--enable-intf-serial \
	--enable-intf-free \
	--enable-intf-open \
	--enable-intf-imb \
	--enable-ipmishell

$(eval $(call BuildPackage,ipmitool))
