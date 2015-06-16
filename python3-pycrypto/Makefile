#
# Copyright (C) Daniel Kettle 2015
#
# PyCrypto is Public Domain software
#


include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pycrypto
PKG_VERSION:=2.6.1
PKG_RELEASE:=1
PKG_SOURCE:=pycrypto-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/pycrypto/
PKG_MD5SUM:=55a61a054aa66812daf5161a0d5d7eda

PKG_BUILD_DIR:=$(BUILD_DIR)/pycrypto-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-pycrypto
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Cryptographic modules for Python.
  DEPENDS:=+python3
endef

define Package/python3-pycrypto/description
  This is a collection of both secure hash functions 
  (such as SHA256 and RIPEMD160), and various encryption 
  algorithms (AES, DES, RSA, ElGamal, etc.). The package 
  is structured to make adding new modules easy. 
  This section is essentially complete, and the software 
  interface will almost certainly not change in an 
  incompatible way in the future; all that remains 
  to be done is to fix any bugs that show up.
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

define Package/python3-pycrypto/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-pycrypto))
