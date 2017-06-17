#
# Copyright (C) 2017 Tomáš "Jethro" Pokorný <xtompok@gmail.com>
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-spidev
PKG_VERSION:=a76493f2917dc9b5736327c7dfac7d451c9cc269
PKG_RELEASE:=1
PKG_LICENSE:=GPLv2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/doceme/py-spidev.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-spidev
  SECTION:=utils
  CATEGORY:=Utils
  TITLE:=python-spidev
  URL:=https://github.com/doceme/py-spidev.git
  DEPENDS:=+python
  MAINTAINER:=Tomas "Jethro" Pokorny <xtompok@gmail.com>
endef

define Package/python-spidev/description
	This project contains a python module for interfacing with SPI devices
	from user space via the spidev linux kernel driver.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-spidev/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,python-spidev))
