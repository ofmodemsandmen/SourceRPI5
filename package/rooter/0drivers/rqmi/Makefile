include $(TOPDIR)/rules.mk

PKG_NAME:=uqmi
PKG_RELEASE:=5

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=$(PROJECT_GIT)/project/uqmi.git
PKG_SOURCE_DATE:=2022-05-04
PKG_SOURCE_VERSION:=56cb2d4056fef132ccf78dfb6f3074ae5d109992
PKG_MIRROR_HASH:=cc832b5318805df8c8387a3650f250dee72d5f1dbda4e4866b5503e186b2210c
PKG_MAINTAINER:=Matti Laakso <malaakso@elisanet.fi>

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=

PKG_FLAGS:=nonshared
PKG_BUILD_FLAGS:=gc-sections

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/rqmi
  SECTION:=net
  CATEGORY:=ROOter
  SUBMENU:=Drivers
  DEPENDS:=+libubox +libblobmsg-json +kmod-usb-net +kmod-usb-net-qmi-wwan +wwan +luci-proto-qmi
  TITLE:=Control utility for mobile broadband modems
endef

define Package/rqmi/description
  uqmi is a command line tool for controlling mobile broadband modems using
  the QMI-protocol.
endef

TARGET_CFLAGS += \
	-I$(STAGING_DIR)/usr/include \
	-Wno-error=dangling-pointer \
	-Wno-error=maybe-uninitialized

CMAKE_OPTIONS += \
	-DDEBUG=1

define Package/rqmi/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/uqmi $(1)/sbin/
	$(CP) ./files/* $(1)/
endef

$(eval $(call BuildPackage,rqmi))