include $(TOPDIR)/rules.mk

PKG_NAME:=meson
PKG_VERSION:=1.6.1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/mesonbuild/meson/releases/download/$(PKG_VERSION)
PKG_HASH:=1eca49eb6c26d58bbee67fd3337d8ef557c0804e30a6d16bfdf269db997464de

PKG_MAINTAINER:=Andre Heider <a.heider@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/host-build.mk

define Host/Configure
endef

define Host/Compile
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/bin
	$(HOST_BUILD_DIR)/packaging/create_zipapp.py $(HOST_BUILD_DIR) --outfile $(STAGING_DIR_HOST)/bin/meson.py
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/lib/meson
	$(INSTALL_CONF) files/openwrt-cross.txt.in $(STAGING_DIR_HOST)/lib/meson/
	$(INSTALL_CONF) files/openwrt-native.txt.in $(STAGING_DIR_HOST)/lib/meson/
endef

define Host/Clean
	$(call Host/Clean/Default)
	rm -rf $(STAGING_DIR_HOST)/lib/meson
endef

$(eval $(call HostBuild))
