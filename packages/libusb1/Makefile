#
# Copyright (C) 2009 Djarvur.net, www.djarvur.net, info@djarvur.net
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libusb1
PKG_VERSION:=1.0.2
PKG_RELEASE:=4

PKG_BUILD_DIR:=$(BUILD_DIR)/libusb-$(PKG_VERSION)

PKG_SOURCE:=libusb-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/libusb
PKG_MD5SUM:=dc8865eaff167aabe78e5799762b8067
PKG_FIXUP:=lib

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

define Package/libusb1
  SECTION:=fwwrt
  CATEGORY:=FWWRT
  TITLE:=A library for accessing Linux USB devices, v 1.0
  URL:=http://libusb.sourceforge.net/
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-shared \
		--enable-static \
	)
endef

TARGET_CFLAGS += $(FPIC)

define Build/InstallDev
	#$(INSTALL_DIR) $(2)/bin

	$(INSTALL_DIR) $(1)/usr/include/libusb-1.0
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/libusb-1.0/libusb.h \
		$(1)/usr/include/libusb-1.0/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libusb*.{la,so*,a} \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libusb-1.0.pc \
		$(1)/usr/lib/pkgconfig/
endef

define Package/libusb1/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libusb*.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libusb1))
