#
# Copyright (C) 2016 Seeed Technology Limited.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pycryptodomex
PKG_VERSION:=v3.4.6
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Legrandin/pycryptodome.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_BUILD_DEPENDS:=+python

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/pycryptodomex
	SECTION:=respeaker
	CATEGORY:=ReSpeaker
	TITLE:=pycrypto
	URL:=https://github.com/Legrandin/pycryptodome
	DEPENDS:=+python +libgmp
endef

define Package/pycryptodomex/description
	web A self-contained Python package of low-level cryptographic primitives
endef

define Build/Configure
	touch $(PKG_BUILD_DIR)/.separate_namespace
endef

define Build/Compile
	$(call Build/Compile/PyMod,, \
		install --prefix=/usr --root=$(PKG_INSTALL_DIR), \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

define Package/pycryptodomex/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)/
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,pycryptodomex))
