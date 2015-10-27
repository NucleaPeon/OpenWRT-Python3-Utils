#
# Copyright (C) Daniel Kettle 2015
#
# PyYAML, Licensed under MIT
#
# TODO: Remove tests, possibly deal with .egg.info

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-yaml
PKG_VERSION:=3.11
PKG_RELEASE:=1
PKG_SOURCE:=PyYAML-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/P/PyYAML/
PKG_MD5SUM:=f50e08ef0fe55178479d3a618efe21db

PKG_BUILD_DIR:=$(BUILD_DIR)/PyYAML-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-yaml
  SUBMENU:=Python3
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=PyYAML, YAML parser and emitter for Python
  DEPENDS:=+python3 +python3-pip
endef

define Package/python3-yaml/description
	YAML parser and emitter for Python
	YAML is a data serialization format designed for human
	readability and interaction with scripting languages.
	PyYAML is a YAML parser and emitter for Python.

	PyYAML features a complete YAML 1.1 parser, Unicode support,
	pickle support, capable extension API, and sensible error
	messages. PyYAML supports standard YAML tags and provides
	Python-specific tags that allow to represent an arbitrary
	Python object.

	PyYAML is applicable for a broad range of tasks from complex
	configuration files to object serialization and persistance.
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

define Package/python3-yaml/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-yaml))
