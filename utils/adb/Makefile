include $(TOPDIR)/rules.mk
#Based on adb package from AUR https://aur.archlinux.org/packages/adb/ , reused adbMakefile

PKG_NAME:=adb
PKG_VERSION:=android.4.4.2_r2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://android.googlesource.com/platform/system/core
PKG_SOURCE_VERSION:=e65b7ea8801145626504c724c28aedd0e5038a28
# PKG_SOURCE_SUBDIR specifies where repo is cloned
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)
PKG_MAINTAINER:=Swift Geek <swiftgeek at gmail>

include $(INCLUDE_DIR)/package.mk

ifeq ($(CONFIG_BIG_ENDIAN),y)
TARGET_CFLAGS+= -DHAVE_BIG_ENDIAN=1
beinfo: $(info *** Big endian detected, look for -DHAVE_BIG_ENDIAN=1 ***)
endif

define Package/adb
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=Android Debug Bridge CLI tool
	URL:=http://tools.android.com/
	DEPENDS:=+zlib +libopenssl +libpthread
endef

define Package/bridge/description
	Android Debug Bridge (adb) is a versatile command line tool that lets you communicate with an emulator instance or connected Android-powered device.
endef

# Add Makefile from AUR
define Build/Prepare
	$(call Build/Prepare/Default)
	$(CP) ./adbMakefile $(PKG_BUILD_DIR)/adb/Makefile
endef

# Nothing just to be sure
define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/adb/ \
		$(TARGET_CONFIGURE_OPTS) \
		TARGET=Linux \
		CFLAGS="$(TARGET_CFLAGS)" \
		LDFLAGS="$(TARGET_LDFLAGS)"
	$(STRIP) $(PKG_BUILD_DIR)/adb/adb
endef

define Package/adb/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/adb/adb $(1)/usr/bin/
endef

$(eval $(call BuildPackage,adb))
