# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=naiveproxy
PKG_VERSION:=122.0.6261.43-2
PKG_RELEASE:=50

ifeq ($(ARCH_PACKAGES),aarch64_cortex-a53)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),aarch64_cortex-a72)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),aarch64_generic)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_arm1176jzf-s_vfp)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_arm926ej-s)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a15_neon-vfpv4)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a5_vfpv4)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a7)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a7_neon-vfpv4)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a7_vfpv4)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a8_vfpv3)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a9)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a9_neon)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_cortex-a9_vfpv3-d16)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_mpcore)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),arm_xscale)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),mipsel_24kc)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),mipsel_mips32)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),riscv64)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),x86)
  PKG_HASH:=skip
else ifeq ($(ARCH_PACKAGES),x86_64)
  PKG_HASH:=skip
else
  PKG_HASH:=skip
endif

PKG_SOURCE:=naiveproxy-v$(PKG_VERSION)-openwrt-$(ARCH_PACKAGES).tar.xz
PKG_SOURCE_URL:=https://github.com/klzgrad/naiveproxy/releases/download/v$(PKG_VERSION)/
PKG_BUILD_DIR:=$(BUILD_DIR)/naiveproxy-v$(PKG_VERSION)-openwrt-$(ARCH_PACKAGES)

PKG_LICENSE:=BSD 3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=sbwml <admin@cooluc.com>

include $(INCLUDE_DIR)/package.mk

define Package/naiveproxy
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=Make a fortune quietly
  URL:=https://github.com/klzgrad/naiveproxy
  DEPENDS:=@!(arc||armeb||mips||mips64||powerpc||TARGET_gemini) +libatomic
endef

define Package/naiveproxy/description
  NaïveProxy uses Chrome's network stack to camouflage traffic with strong
  censorship resistance and low detectability. Reusing Chrome's stack also
  ensures best practices in performance and security.
endef

define Package/naiveproxy/conffiles
/etc/config/naiveproxy
endef

define Build/Compile
endef

define Package/naiveproxy/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/naive $(1)/usr/bin/naive
	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d
	$(INSTALL_CONF) $(CURDIR)/files/naiveproxy.config $(1)/etc/config/naiveproxy
	$(INSTALL_BIN) $(CURDIR)/files/naiveproxy.init $(1)/etc/init.d/naiveproxy
endef

$(eval $(call BuildPackage,naiveproxy))