#
# Copyright (C) Daniel Kettle 2015
#
# Spartacus
#


include $(TOPDIR)/rules.mk

PKG_NAME:=python3-spartacus
PKG_VERSION:=0.9
PKG_RELEASE:=1
PKG_SOURCE_URL:=https://subversion.assembla.com/svn/teletics.spartacus/trunk/dist/
PKG_MD5SUM:=831e948c7e19ac0a3a8d1c90f28ee50d

PKG_BUILD_DIR:=$(BUILD_DIR)/spartacus-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-spartacus
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=SSH2 protocol library
  DEPENDS:=+python3-paramiko +python3-pip +python3-tornado +liburl +openssh-server +openssh-client +openssh-client-utils +openssh-keygen +openssh-sftp-server +openssh-sftp-client +sshtunnel +libssh2
endef

define Package/python3-spartacus/description

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

define Package/python3-spartacus/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-spartacus))
