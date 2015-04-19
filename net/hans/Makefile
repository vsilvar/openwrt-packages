#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hans
PKG_VERSION:=0.4.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/hanstunnel
PKG_MD5SUM:=97a93a886bc766212257198fd99d1061

include $(INCLUDE_DIR)/package.mk

define Package/hans
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Firewall Tunnel
  DEPENDS:=+libstdcpp +kmod-tun
  TITLE:=Hans IP over ICMP
  URL:=http://code.gerade.org/hans/
endef

define Package/hans/description
	Hans makes it possible to tunnel IPv4 through ICMP echo packets,
	so you could call it a ping tunnel. This can be useful when you
	find yourself in the situation that your Internet access is
	firewalled, but pings are allowed.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) GCC=$(TARGET_CC) GPP=$(TARGET_CXX)
endef

define Package/hans/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/hans $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/hans.init $(1)/etc/init.d/hans
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/hans.config $(1)/etc/config/hans
endef

define Package/hans/conffiles
/etc/config/hans
endef

$(eval $(call BuildPackage,hans))
