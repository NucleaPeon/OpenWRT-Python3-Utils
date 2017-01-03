#
# Copyright (C) Daniel Kettle 2016
#
# Requests
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dnslib
PKG_VERSION:=0.9.6
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=hg
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://bitbucket.org/paulc/dnslib
PKG_SOURCE_PROTO:=hg
PKG_SOURCE_VERSION:=c6871d81b4f85c2028a2a2665633698e37321c40
PKG_LICENSE:=BSD

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/dnslib
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python3
	TITLE:=A library to encode/decode DNS wire-format packets
	URL:=https://bitbucket.org/paulc/dnslib
	DEPENDS:=+python3
endef

define Package/dnslib/description
 The library provides:
 1. Support for encoding/decoding DNS packets between wire format, python objects, and Zone/DiG textual representation (dnslib.dns)
 2. A server framework allowing the simple creation of custom DNS resolvers (dnslib.server) and a number of example servers created using this framework
 3. A number of utilities for testing (dnslib.client, dnslib.proxy, dnslib.intercept)
endef

define Build/Configure
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/dnslib/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)
endef
$(eval $(call PyPackage,dnslib))
$(eval $(call BuildPackage,dnslib))
