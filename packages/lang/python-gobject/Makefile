#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
# 

include $(TOPDIR)/rules.mk

PKG_NAME:=python-pygobject
PKG_VERSION:=2.90
PKG_VERSION_MICRO:=4
PKG_RELEASE:=1

PKG_SOURCE:=pygobject-$(PKG_VERSION).$(PKG_VERSION_MICRO).tar.xz
PKG_SOURCE_URL:=https://git.gnome.org/browse/pygobject/snapshot
PKG_MD5SUM:=

PKG_BUILD_DIR:=$(BUILD_DIR)/pygobject-$(PKG_VERSION)
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-pygobject
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=GObject library for Python.
  URL:=https://git.gnome.org/browse/pygobject/refs/tags
  DEPENDS:=+python +python-setuptools
endef

define Package/python-pygobject/description
  GObject library for Python.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,\
		install --prefix="$(PKG_INSTALL_DIR)/usr" \
	)
endef

define Package/python-pygobject/install
        $(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
        $(CP) \
            $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
            $(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call PyPackage,python-pygobject))
$(eval $(call BuildPackage,python-pygobject))

