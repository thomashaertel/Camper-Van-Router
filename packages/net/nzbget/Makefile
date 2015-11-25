#
# Copyright (C) 2006-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nzbget
PKG_VERSION:=16.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/nzbget/nzbget/releases/download/v$(PKG_SOURCE)/$(PKG_SOURCE)
PKG_MD5SUM:=6813c6c0bc59e07fd1cc028c58e60c6f

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(BUILD_VARIANT)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

define Package/nzbget
  SUBMENU:=Usenet
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=$(CXX_DEPENDS)
  TITLE:=console-based Usenet client
  MAINTAINER:=Andrey Prygunkov <hugbug@users.sourceforge.net>
  URL:=http://nzbget.net/
endef

define Package/nzbget/description
	NZBGet is a Usenet client written in C++ and designed with performance in mind to achieve maximum download speed by using very little system resources.
endef

#CONFIGURE_VARS += \
#	CXXFLAGS="$$$$CXXFLAGS -fno-rtti"

define Package/nzbget/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/usr/bin/$(PKG_NAME)
endef

$(eval $(call BuildPackage,nzbget))
