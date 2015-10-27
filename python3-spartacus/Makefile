#
# Copyright (C) Daniel Kettle 2015
#
# Spartacus
#


include $(TOPDIR)/rules.mk

PKG_NAME:=spartacus
PKG_VERSION:=0.13
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://localhost:8000/
#PKG_SOURCE_URL:=https://www.assembla.com/spaces/teletics/subversion-3/source/HEAD/trunk/dist/$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_MD5SUM:=96e6cdc23da46ab9599d1672d79f7a0e

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/spartacus
  SUBMENU:=Python3
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python-side Rapid Application Development Toolkit
  DEPENDS:=+python3-paramiko +python3-pip +python3-tornado +libcurl +openssh-server +openssh-client +openssh-client-utils +openssh-keygen +openssh-sftp-server +openssh-sftp-client +sshtunnel +libssh2
endef

define Package/spartacus/description
	Rapid Prototyping Toolbox written in Python3
endef

define Build/Compile

endef

define Package/spartacus/install
	$(INSTALL_DIR) $(1)/usr/lib/python3/
	$(INSTALL_DIR) $(1)/usr/lib/python3/site-packages/
	$(INSTALL_DIR) $(1)/usr/lib/python3/site-packages/Spartacus
	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) -r $(PKG_BUILD_DIR)/Spartacus/ $(1)/usr/lib/python3/site-packages/Spartacus/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/Spartacus/Scripts/webserver.py $(1)/usr/bin/spartacus-web-server
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/Spartacus/Scripts/spartacusstop.py $(1)/usr/bin/spartacus-stop
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/Spartacus/Scripts/spartacusstart.py $(1)/usr/bin/spartacus-start
endef

$(eval $(call BuildPackage,spartacus))
