#
# Copyright (C) 2010-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=automount
PKG_VERSION:=1
PKG_RELEASE:=21
PKG_ARCH:=all

PKG_CONFIG_DEPENDS:= CONFIG_PACKAGE_$(PKG_NAME)_NTFS-3G

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)/config
config PACKAGE_$(PKG_NAME)_NTFS-3G
	bool "Support NTFS mount"
	default n
endef

define Package/automount
  TITLE:=Mount autoconfig hotplug script.
  MAINTAINER:=Lean
  DEPENDS:=+block-mount +kmod-usb-storage +kmod-usb-storage-extras +kmod-fs-vfat +kmod-fs-ext4 +PACKAGE_$(PKG_NAME)_NTFS-3G:ntfs-3g
endef

define Package/automount/description
A usb autoconfig hotplug script.
endef

define Build/Compile
endef

define Package/automount/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/15-automount $(1)/etc/15-automount
	$(INSTALL_BIN) ./files/zzz-move-automount $(1)/etc/uci-defaults/zzz-move-automount
endef

$(eval $(call BuildPackage,automount))
