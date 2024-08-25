#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=YSFReflector
#PKG_REV:=HEAD
PKG_REV:=441ac34
PKG_VERSION:=BIPPCS-2024
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/qzyuebing/YSFReflector
PKG_MIRROR_HASH:=a7bb70b4312441ce898d0f6ace13bef49c5aea744d5588d8b98ac14519edfdce
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=git
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

define Package/${PKG_NAME}
	SECTION:=net
	CATEGORY:=MMDVM
	TITLE:=MMDVM YSFReflector
	URL:=$(PKG_SOURCE_URL)
	DEPENDS:=+libpthread +libstdcpp
endef

define Package/${PKG_NAME}/description
System Fusion network servers, including gateway and parrot.
endef

TARGET_CFLAGS += -std=c++0x -DOPENWRT=1

TARGET_LDFLAGS += \
        -Wl,-rpath-link=$(STAGING_DIR)/usr/lib \

MAKE_FLAGS +=\
        CFLAGS="$(TARGET_CFLAGS) $(TARGET_CPPFLAGS)" \
        LDFLAGS="$(TARGET_LDFLAGS)" \

define Package/${PKG_NAME}/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/YSFReflector/YSFReflector $(1)/usr/sbin/
	$(CP) -a files/* $(1)/
endef

define Package/${PKG_NAME}/conffiles
/etc/YSFReflector.ini
endef

define Package/${PKG_NAME}/postinst
endef

$(eval $(call BuildPackage,${PKG_NAME}))
