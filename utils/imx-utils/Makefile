#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=imx-utils
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mhei/imx-uuc.git
PKG_SOURCE_DATE:=2018-05-07
PKG_SOURCE_VERSION:=625c36e8e67b9ef0f4c18da94b5daacc42bf4f8c
PKG_MIRROR_HASH:=ce7018d6ba6f2cccc64a40103cfb64f8905c96262140cdc8bf5f7674f192b81b

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING

PKG_MAINTAINER:=Michael Heimpold <mhei@heimpold.de>

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/imx-utils
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Tools for NXP i.MX23/28/6 manufacturing
  URL:=https://github.com/mhei/imx-uuc.git
endef

define Package/imx-utils/description
  This package contains userspace utilities, which can be used during
  manufacturing process of NXP (formerly Freescale) i.MX23/28/6/...
  devices.
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
	        $(TARGET_CONFIGURE_OPTS) CFLAGS="$(TARGET_CFLAGS)"
endef

define Package/imx-utils/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/uuc $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sdimage $(1)/sbin
endef

$(eval $(call BuildPackage,imx-utils))
