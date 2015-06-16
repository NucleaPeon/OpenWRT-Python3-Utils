#
# Copyright (C) Daniel Kettle 2015
# Copyright (C) OpenWRT
#
# This is free software, licensed under the MIT License
# (ECDSA is MIT-licensed Software)
# 
# Note: ECDSA is pure python software and has no install dependencies.
# However, it depends on openssl for running tests, therefore it's 
# recommended to install openssl in tandem with this package.
# 
# If this is a requirement, openssl will be added to depends
#


include $(TOPDIR)/rules.mk

PKG_NAME:=python3-ecdsa
PKG_VERSION:=0.13
PKG_RELEASE:=1

PKG_SOURCE:=ecdsa-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/e/ecdsa/
PKG_MD5SUM:=1f60eda9cb5c46722856db41a3ae6670

PKG_BUILD_DIR:=$(BUILD_DIR)/ecdsa-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-ecdsa
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=ECDSA cryptographic signature library (pure python)
  DEPENDS:=+python3
endef

define Package/python3-ecdsa/description
  This is an easy-to-use implementation of ECDSA cryptography (Elliptic Curve
  Digital Signature Algorithm), implemented purely in Python, released under
  the MIT license. With this library, you can quickly create keypairs (signing
  key and verifying key), sign messages, and verify the signatures. The keys
  and signatures are very short, making them easy to handle and incorporate
  into other protocols.
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

define Package/python3-ecdsa/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/easy_install \
		$(1)/usr/bin/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-ecdsa))
