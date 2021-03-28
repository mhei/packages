include $(TOPDIR)/rules.mk

PKG_NAME:=bcm27xx-hats-eepromutils
PKG_VERSION:=9d16a6cbcaa29cbeaef9a49c54e2a7a6077773a1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/raspberrypi/hats/tar.gz/$(PKG_VERSION)?
PKG_HASH:=e3f771e4dfd4016b3d834c5207705266019d99811df50595acde2f77231c67c7

PKG_MAINTAINER:=Michael Heimpold <mhei@heimpold.de>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENCE

include $(INCLUDE_DIR)/package.mk

TAR_OPTIONS:=--strip-components 1 $(TAR_OPTIONS)
TAR_CMD=$(HOST_TAR) -C $(1) $(TAR_OPTIONS)

define Package/bcm27xx-hats-eepromutils
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+kmod-eeprom-at24 +kmod-i2c-gpio +bcm27xx-userland
  TITLE:=BCM27xx HAT EEPROM tools
endef

define Package/bcm27xx-hats-eepromutils/description
  BCM27xx EEPROM tools for HAT development
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/eepromutils \
	            CC="$(TARGET_CC)" \
	            CFLAGS="$(TARGET_CFLAGS) $(TARGET_CPPFLAGS)" \
	            LDFLAGS="$(TARGET_LDFLAGS)"
endef

define Package/bcm27xx-hats-eepromutils/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/eepromutils/eepmake $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/eepromutils/eepdump $(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/eepromutils/eepflash.sh $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,bcm27xx-hats-eepromutils))
