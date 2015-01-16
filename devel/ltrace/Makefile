#
# Copyright (C) 2008-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ltrace
PKG_VERSION:=0.7.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).orig.tar.bz2
PKG_SOURCE_URL:=http://ltrace.org/
PKG_MD5SUM:=b3dd199af8f18637f7d4ef97fdfb9d14
PKG_MAINTAINER:=Luiz Angelo Daros de Luca <luizluca@gmail.com>
PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

PKG_BUILD_DEPENDS:=libelf1

define Package/ltrace
  SECTION:=devel
  CATEGORY:=Development
  TITLE:=ltrace
  URL:=http://ltrace.org/
  MAINTAINER:=Juan Cespedes <cespedes@debian.org>
  DEPENDS:=+libelf1 +libstdcpp
endef

define Package/ltrace/description
  ltrace intercepts and records dynamic library calls which are called by an executed
  process and the signals received by that process. It can also intercept and print the
  system calls executed by the program.
endef

CONFIGURE_ARGS+=--disable-werror

define Package/ltrace/install
    $(MAKE) -C $(PKG_BUILD_DIR) DESTDIR="$(PKG_INSTALL_DIR)" install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/ltrace $(1)/usr/bin/
endef

$(eval $(call BuildPackage,ltrace))
