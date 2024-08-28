#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=DMRGateway
#PKG_REV:=HEAD
PKG_REV:=f2cc04x
PKG_VERSION:=BI4PCS
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/g4klx/DMRGateway
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=git

include $(INCLUDE_DIR)/package.mk

define Package/${PKG_NAME}
	SECTION:=net
	CATEGORY:=MMDVM
	TITLE:=MMDVM DMRGateway
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
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/DMRGateway/DMRGateway $(1)/usr/sbin/
	$(CP) -a files/* $(1)/
endef

define Package/${PKG_NAME}/conffiles
/etc/DMRGateway.ini
endef

define Package/${PKG_NAME}/postinst
endef

$(eval $(call BuildPackage,${PKG_NAME}))
