#
# Copyright (C) Daniel Kettle 2015
#
# CSS Compressor, licensed under BSD.
#
# TODO: Remove tests, possibly deal with .egg.info

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-docutils
PKG_VERSION:=0.12
PKG_RELEASE:=1
PKG_SOURCE:=docutils-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/d/docutils/
PKG_MD5SUM:=4622263b62c5c771c03502afa3157768

PKG_BUILD_DIR:=$(BUILD_DIR)/docutils-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-docutils
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python Documentation Utilities
  DEPENDS:=+python3 +python3-pip
endef

define Package/python3-docutils/description
	Docutils is a modular system for processing documentation
	into useful formats, such as HTML, XML, and LaTeX. For
	input Docutils supports reStructuredText, an easy-to-read,
	what-you-see-is-what-you-get plaintext markup syntax.
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

define Package/python3-docutils/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-docutils))
