#
# Copyright (C) 2017 Tomáš "Jethro" Pokorný <xtompok@gmail.com>
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pynrf24
PKG_VERSION:=b1f76ee2f6626b3fe55e057e19c9ff66b1c09232
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/xtompok/pynrf24.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/pynrf24
  SECTION:=utils
  CATEGORY:=Utils
  TITLE:=pynrf24
  URL:=https://github.com/xtompok/pynrf24
  DEPENDS:=+python
  MAINTAINER:=Tomas "Jethro" Pokorny <xtompok@gmail.com>
endef


define Package/pynrf24/description
	Pure python port of the RF24 (https://github.com/maniacbug/RF24/) library for NRF24L01+ radios through SPI.
endef

define Build/Compile
	cd $(PKG_BUILD_DIR) ; $(CONFIGURE_VARS) python ./setup.py install --prefix="$(PKG_INSTALL_DIR)/usr"
endef

define Package/pynrf24/install
	$(INSTALL_DIR) $(1)
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef
$(eval $(call BuildPackage,pynrf24))
