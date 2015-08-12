#
# Copyright (C) Daniel Kettle 2015
#
# CSS Compressor, licensed under BSD.
#
# TODO: Remove tests, possibly deal with .egg.info

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-networkx
PKG_VERSION:=1.10
PKG_RELEASE:=1
PKG_SOURCE:=networkx-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/n/networkx/
PKG_MD5SUM:=eb7a065e37250a4cc009919dacfe7a9d

PKG_BUILD_DIR:=$(BUILD_DIR)/networkx-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-networkx
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Create, manipulate, and study networks.
  DEPENDS:=+python3 +python3-pip
endef

define Package/python3-networkx/description
	NetworkX is a Python language software package for
	the creation, manipulation, and study of the structure,
	dynamics, and functions of complex networks.

	Features

	* Python language data structures for graphs, digraphs, and multigraphs.
	* Many standard graph algorithms
	* Network structure and analysis measures
	* Generators for classic graphs, random graphs, and synthetic networks
	* Nodes can be "anything" (e.g. text, images, XML records)
	* Edges can hold arbitrary data (e.g. weights, time-series)
	* Open source BSD license
	* Well tested: more than 1800 unit tests, >90% code coverage
	* Additional benefits from Python: fast prototyping, easy to teach, multi-platform

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

define Package/python3-networkx/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-networkx))
