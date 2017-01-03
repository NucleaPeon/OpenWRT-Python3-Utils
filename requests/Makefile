#
# Copyright (C) Daniel Kettle 2016
#
# Requests
#

include $(TOPDIR)/rules.mk

PKG_NAME:=requests
PKG_VERSION:=2.12.4
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/kennethreitz/requests.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=8e0a532cad39e28dc6e74002f79513dbb509bad2
PKG_LICENSE:=Apache 2.0
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

# PKG_BUILD_DEPENDS:=python3-setuptools/host
# HOST_BUILD_DEPENDS:=python3-setuptools/host

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/requests
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python3
	TITLE:=Python HTTP for Humans.
	URL:=http://docs.python-requests.org/en/master/
	DEPENDS:=+python3 +python3-setuptools
endef

# MAKE_FLAGS += prefix=/usr

define Package/requests/description
 Requests is the only Non-GMO HTTP library for Python, safe for human 
 consumption. Warning: Recreational use of other HTTP libraries may 
 result in dangerous side-effects, including: security vulnerabilities, 
 verbose code, reinventing the wheel, constantly reading documentation, 
 depression, headaches, or even death.
endef

define Build/Configure
endef

define Build/Compile
# 	python3 $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/setup.py install
	$(call Build/Compile/PyMod,,install --prefix="/usr" --root="$(PKG_INSTALL_DIR)")
endef

# define Package/requests/install
# 	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
# 	$(CP) \
# 		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
# 		$(1)$(PYTHON3_PKG_DIR)/
# 	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
# endef
$(eval $(call PyPackage,requests))
$(eval $(call BuildPackage,requests))
