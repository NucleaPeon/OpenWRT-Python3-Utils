#
# Copyright (C) Daniel Kettle 2015
#
# Paramiko
#


include $(TOPDIR)/rules.mk

PKG_NAME:=python3-paramiko
PKG_VERSION:=1.15.3
PKG_RELEASE:=1
PKG_SOURCE:=paramiko-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/paramiko/
PKG_MD5SUM:=c959088669f8d951585aa6abc25c8ef6
PKG_BUILD_DIR:=$(BUILD_DIR)/paramiko-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-paramiko
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=SSH2 protocol library
  DEPENDS:=+python3 +python3-pycrypto +python3-ecdsa +python3-pip +openssh-server +openssh-client +openssh-client-utils +openssh-keygen +openssh-sftp-server +openssh-sftp-client +sshtunnel +libssh2
endef

define Package/python3-paramiko/description
  This is a library for making SSH2 connections (client or server).
  Emphasis is on using SSH2 as an alternative to SSL for making
  secure connections between python scripts. All major ciphers and
  hash methods are supported. SFTP client and server mode are both
  supported too.
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

define Package/python3-paramiko/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-paramiko))
