#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-tornado
PKG_VERSION:=4.1
PKG_RELEASE:=1

PKG_LICENSE:=Apache 2.0
PKG_MAINTAINER:=Daniel Kettle <daniel.kettle@angrycoders.com>

PKG_SOURCE:=tornado-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/t/tornado/
PKG_MD5SUM:=a06ea343375f2247344257ef691641f9
PKG_BUILD_DIR:=$(BUILD_DIR)/tornado-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-tornado
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=Tornado is an asynchronous Python web server
	URL:=http://www.tornadoweb.org
	DEPENDS:=+python3 +libcurl +ca-certificates
endef

define Package/python3-tornado/description
 Tornado is a Python web framework and asynchronous networking library, 
 originally developed at FriendFeed. By using non-blocking network I/O, 
 Tornado can scale to tens of thousands of open connections, making it 
 ideal for long polling, WebSockets, and other applications that require 
 a long-lived connection to each user.
endef


define Build/Compile
	echo $(PKG_BUILD_DIR)
endef


define Package/python3-tornado/install
	$(INSTALL_DIR) $(1)/usr/lib/python3.4/site-packages/tornado/
	$(INSTALL_DIR) $(1)/usr/lib/python3.4/site-packages/tornado/platform
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tornado/*.py $(1)/usr/lib/python3.4/site-packages/tornado/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tornado/platform/*.py $(1)/usr/lib/python3.4/site-packages/tornado/platform/
	$(CP) -r $(PKG_BUILD_DIR)/tornado/* $(1)/usr/lib/python3.4/site-packages/tornado/
endef


$(eval $(call BuildPackage,python3-tornado))
