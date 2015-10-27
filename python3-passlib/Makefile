#
# Copyright (C) Daniel Kettle 2015
#
# CSS Compressor, licensed under BSD.
#
# TODO: Remove tests, possibly deal with .egg.info

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-passlib
PKG_VERSION:=1.6.5
PKG_RELEASE:=1
PKG_SOURCE:=passlib-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/passlib/
PKG_MD5SUM:=d2edd6c42cde136a538b48d90a06ad67

PKG_BUILD_DIR:=$(BUILD_DIR)/passlib-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-passlib
  SUBMENU:=Python3
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Password Hashing Library
  DEPENDS:=+python3 +python3-pip
endef

define Package/python3-passlib/description
	Passlib is a password hashing library for Python 2 & 3,
	which provides cross-platform implementations of over
	30 password hashing algorithms, as well as a framework
	for managing existing password hashes. It’s designed to
	be useful for a wide range of tasks, from verifying a
	hash found in /etc/shadow, to providing full-strength
	password hashing for multi-user application.
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

define Package/python3-passlib/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-passlib))
