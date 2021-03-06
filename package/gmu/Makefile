# 
# Copyright (c) 2010 wejp
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gmu
PKG_VERSION:=0.8.0BETA1
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://wejp.k.vu/files/
PKG_MD5SUM:=a1a3d346802f3877b4c739b3c65225d6

include $(INCLUDE_DIR)/package.mk

define Package/gmu
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=Gmu Music Player
  URL:=http://wejp.k.vu/projects/gmu/
  MENU:=1
  DEPENDS:=+libsdl +libsdl-image +libsdl-gfx +libmpcdec +libmikmod \
	  +libvorbisidec +libspeex +libflac +libogg +BUILD_PATENTED:libmpg123
endef

define Package/gmu/description
  A popular music player for various handheld devices.
  It supports various file formats and comes with a
  file browser and a playlist editor/viewer.
endef

MAKE_VARS += TARGET=zipit-z2 $(if $(CONFIG_BUILD_PATENTED),MORE_DECODERS="decoders/mpg123.so")
CFLAGS += -I$(STAGING_DIR)/usr/include/SDL
LDFLAGS += \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/SDL \

define Package/gmu/install
	$(INSTALL_DIR) \
		$(1)/etc/gmu \
		$(1)/usr/bin \
		$(1)/usr/share/gmu \
		$(1)/usr/share/gmu/decoders \
		$(1)/usr/share/gmu/frontends \
		$(1)/usr/share/gmu/themes/default-modern \
		$(1)/usr/share/gmu/themes/default-modern-large 

	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/gmu \
		$(1)/usr/bin/gmu.bin

	$(INSTALL_BIN) \
		./files/gmu \
		$(1)/usr/bin/

	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/*.conf \
		$(1)/etc/gmu/

	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/*.keymap \
		$(1)/etc/gmu/

	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/decoders/* \
		$(1)/usr/share/gmu/decoders/

	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/frontends/* \
		$(1)/usr/share/gmu/frontends/

	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/themes/default-modern/* \
		$(1)/usr/share/gmu/themes/default-modern/

	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/themes/default-modern-large/* \
		$(1)/usr/share/gmu/themes/default-modern-large/

	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/README.txt \
		$(1)/usr/share/gmu/
endef

$(eval $(call BuildPackage,gmu))
