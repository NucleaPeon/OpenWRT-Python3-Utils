#
# Copyright (C) Daniel Kettle 2015
#
# PyYAML, Licensed under ZPL 2.1
#
# TODO: Remove tests, possibly deal with .egg.info

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-waitress
PKG_VERSION:=0.8.9
PKG_RELEASE:=1
PKG_SOURCE:=waitress-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/w/waitress/
PKG_MD5SUM:=da3f2e62b3676be5dd630703a68e2a04

PKG_BUILD_DIR:=$(BUILD_DIR)/waitress-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-waitress
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Pure Python WSGI server
  DEPENDS:=+python3 +python3-pip
endef

define Package/python3-waitress/description
	Waitress is meant to be a production-quality pure-Python
	WSGI server with very acceptable performance.

	It has no dependencies except ones which live in the Python
	standard library. It runs on CPython on Unix and Windows under
	Python 2.6+ and Python 3.2+. It is also known to run on
	PyPy 1.6.0+ on UNIX. It supports HTTP/1.0 and HTTP/1.1.
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

define Package/python3-waitress/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-waitress))
