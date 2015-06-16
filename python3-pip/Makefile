#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
# 

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pip
PKG_VERSION:=7.0.3
PKG_RELEASE:=1

PKG_SOURCE:=pip-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/pip/
PKG_MD5SUM:=54cbf5ae000fb3af3367345f5d299d1c

SETUPTOOLS_VERSION:=17.1.1
SETUPTOOLS_NAME:=setuptools-$(SETUPTOOLS_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/pip-$(PKG_VERSION)
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-pip
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Tool for installing Python packages.
  URL:=https://pip.pypa.io
  DEPENDS:=+python3 +python3-setuptools
endef

define Package/python3-pip/description
  A tool for installing and managing Python packages.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

PYTHON3_PIP_PKG_DIR:=$(PYTHON3_PKG_DIR)/pip-$(PKG_VERSION)-py$(PYTHON_VERSION).egg/pip
define PyPackage/python3-pip/filespec
+|$(PYTHON3_PKG_DIR)
-|$(PYTHON3_PIP_PKG_DIR)/_vendor/distlib/*.exe
endef

# Backup these files, so that they do not clash with python-setuptools
# If we install python-pip python-setuptools, we want these to be replaced,
# since python-pip replaces python-setuptools (when installed)
define Package/python3-pip/preinst
#!/bin/sh
cd "$${IPKG_INSTROOT}$(PYTHON3_PKG_DIR)"
mv -f easy_install.py easy_install.py.old
mv -f site.py site.py.old
exit 0
endef

# And put them back on remove
define Package/python3-pip/postrm
#!/bin/sh
cd "$${IPKG_INSTROOT}$(PYTHON3_PKG_DIR)"
mv -f easy_install.py.old easy_install.py
mv -f site.py.old site.py
exit 0
endef

define Package/python3-pip/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	#$(INSTALL_DIR) $(PKG_INSTALL_DIR)
	#echo 'echoing variables'
	#echo $(PYTHON3_PKG_DIR) # /usr/lib/python3.4/site-packages/
	#echo $(PKG_INSTALL_DIR) # /opt/OpenWRT/build_dir/target-i386_i486_uClibc-0.9.33.2/pip-7.0.3/ipkg-install
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python3-pip))
