#
# Copyright (C) Daniel Kettle 2016
#
# Requests
#

include $(TOPDIR)/rules.mk

PKG_NAME:=requests
PKG_VERSION:=2.12.4
PKG_RELEASE:=1

PKG_LICENSE:=Apache 2.0
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/r/requests/
PKG_MD5SUM:=acdb48888a9d3c7309da12fc7f83fedb
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)


PKG_SOURCE:=$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/bottlepy/bottle/archive
PKG_MD5SUM:=50a6ebada59391e8d01b2bd2ec52f05b
PKG_BUILD_DIR:=$(BUILD_DIR)/bottle-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/requests
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python3
	TITLE:=Python HTTP for Humans.
	URL:=http://bottlepy.org
	DEPENDS:=+python3
endef

define Package/python3-bottle/description
 Requests is the only Non-GMO HTTP library for Python, safe for human 
 consumption. Warning: Recreational use of other HTTP libraries may 
 result in dangerous side-effects, including: security vulnerabilities, 
 verbose code, reinventing the wheel, constantly reading documentation, 
 depression, headaches, or even death.
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/requests/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) $(PKG_BUILD_DIR)/bottle.py $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,requestss))
