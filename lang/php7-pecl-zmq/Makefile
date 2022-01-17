#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PECL_NAME:=zmq
PECL_LONGNAME:=PHP extension for ZeroMQ software library
PKG_VERSION:=1.1.3
PKG_RELEASE:=1
PKG_HASH:=c492375818bd51b355352798fb94f04d6828c6aeda41ba813849624af74144ce

PKG_NAME:=php7-pecl-zmq
PKG_SOURCE:=$(PECL_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://pecl.php.net/get/

PKG_MAINTAINER:=Michael Heimpold <mhei@heimpold.de>

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/pecl-php7/$(PECL_NAME)-$(PKG_VERSION)
PKG_BUILD_PARALLEL:=1

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include ../php7/pecl.mk

CONFIGURE_ARGS+= \
	--with-zmq=yes \
	--with-czmq=no

$(eval $(call PECLPackage,$(PECL_NAME),$(PECL_LONGNAME),+libzmq))
$(eval $(call BuildPackage,$(PKG_NAME)))
