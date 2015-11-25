#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
# 

include $(TOPDIR)/rules.mk

PKG_NAME:=python-pygtk
PKG_VERSION:=2.24
PKG_VERSION_MICRO:=0
PKG_RELEASE:=1

PKG_SOURCE:=pygtk-$(PKG_VERSION).$(PKG_VERSION_MICRO).tar.gz
PKG_SOURCE_URL:=http://ftp.gnome.org/pub/GNOME/sources/pygtk/$(PKG_VERSION)
PKG_MD5SUM:=d27c7f245a9e027f6b6cd9acb7468e36

PKG_BUILD_DIR:=$(BUILD_DIR)/pygtk-$(PKG_VERSION)
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-pygtk
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=GTK library for Python.
  URL:=http://www.pygtk.org
  DEPENDS:=+python +python-setuptools
endef

define Package/python-pygtk/description
  GTK library for Python.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,\
		install --prefix="$(PKG_INSTALL_DIR)/usr" \
	)
endef

define Package/python-pygtk/install
        $(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
        $(CP) \
            $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
            $(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call PyPackage,python-pygtk))
$(eval $(call BuildPackage,python-pygtk))

