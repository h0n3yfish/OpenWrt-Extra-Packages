#
# Copyright (C) 2012-2023 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=dae
PKG_VERSION:=0.1.7
PKG_RELEASE:=1

PKG_SOURCE:=dae-linux-arm64.zip
PKG_SOURCE_URL:=https://github.com/daeuniverse/dae/releases/download/v$(PKG_VERSION)
PKG_HASH:=28ffaf9ed740d4350a412857eff3b4f4ff9218beab2556ed6c59c9bfae3914fa

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILE:=LICENSE

UNZIP_CMD:=unzip -q -d $(INSTALL_DIR) $(DL_DIR)/$(PKG_SOURCE)

define Package/dae
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=A lightweight and high-performance transparent proxy solution
  URL:=https://github.com/daeuniverse/dae
endef

define Package/dae/description
  dae, means goose, is a lightweight and high-performance transparent
  proxy solution.
endef

define Package/dae/conffiles
/etc/dae/config.dae
endef

define Package/dae/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(INSTALL_DIR)/dae-linux-arm64 $(1)/usr/bin/dae

	$(INSTALL_DIR) $(1)/etc/dae/
	$(INSTALL_CONF) $(INSTALL_DIR)/example.dae $(1)/etc/dae/

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) $(CURDIR)/files/dae.config $(1)/etc/config/dae

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(CURDIR)/files/dae.init $(1)/etc/init.d/dae
endef

$(eval $(call BuildPackage,dae))
