#
# Copyright (C) Daniel Kettle 2015
#
# CSS Compressor, licensed under BSD.
#
# TODO: Remove tests, possibly deal with .egg.info

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-click
PKG_VERSION:=5.1
PKG_RELEASE:=1
PKG_SOURCE:=click-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/c/click/
PKG_MD5SUM:=9c5323008cccfe232a8b161fc8196d41
PKG_BUILD_DIR:=$(BUILD_DIR)/click-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-click
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python Simple Command Line Parser
  DEPENDS:=+python3 +python3-pip
endef

define Package/python3-click/description
	Click is a Python package for creating beautiful command line interfaces
	in a composable way with as little code as necessary. It's the "Command
	Line Interface Creation Kit". It's highly configurable but comes with
	sensible defaults out of the box.

	It aims to make the process of writing command line tools quick and fun
	while also preventing any frustration caused by the inability to implement
	an intended CLI API.
endef

define Host/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(STAGING_DIR)$(PYTHON3_PKG_DIR)
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-click/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-click))
