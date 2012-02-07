# 
# Copyright (c) 2010 mozzwald
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mouse-emu
PKG_VERSION:=0.1.2
PKG_RELEASE:=1

PKG_SOURCE:=mouse-emu-v0.1.2-0.tar.gz
PKG_SOURCE_URL:=http://www.mozzwald.com/zipit/
PKG_MD5SUM:=0232fce1b756d8b5fcd7dfb44abeb73f

include $(INCLUDE_DIR)/package.mk

define Package/mouse-emu
  SECTION:=utilities
  CATEGORY:=Utilities
  TITLE:=mouse-emu
  URL:=http://github.com/anarsoul
  MENU:=1
  DEPENDS:=+kmod-input-userlevel
endef

define Package/mouse-emu/description
  Tiny mouse emulator for mouse/touchpad-less devices
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		LDFLAGS="$(LDFLAGS) $(EXTRA_LDFLAGS)" \
		$(TARGET_CONFIGURE_OPTS) \
		CROSS="$(TARGET_CROSS)" \
		ARCH="$(ARCH)" \
		all
endef

define Package/mouse-emu/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mouse-emul $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mouse-emulrc $(1)/etc/
endef

$(eval $(call BuildPackage,mouse-emu))
