SPK_NAME = zerotier
SPK_VERS = 1.4.0
SPK_REV = 0
SPK_ICON = src/zerotier.png

DEPENDS = cross/$(SPK_NAME)

MAINTAINER = ZeroTier, Inc.
DESCRIPTION = An easy-to-use encrypted P2P LAN for all of your devices.
LICENSE  = GPLv3
CHANGELOG = TUN/TAP-related bugfix, identity files now reside in /var/lib/zerotier-one
HOMEPAGE = https://my.zerotier.com
REPORT_URL = https://github.com/zerotier/ZeroTierNAS/issues
DISPLAY_NAME = ZeroTier

# Special build of 1.2.13 which contains changes required for spksrc pull request.
# This will be removed after next major ZeroTier version bump (1.4.0)
PRODUCT_DIR = $(WORK_DIR)/ZeroTierOne-db813db7e875c257e42c41ab8091c3df1e9300a5
# PRODUCT_DIR=$(WORK_DIR)/$(DISPLAY_NAME)One-$(SPK_VERS)

DSM_UI_DIR = ui
RELOAD_UI = yes
STARTABLE = yes
REQUIRED_DSM = 5.0
BETA = 0

ENV += ZT_SYNOLOGY=1
#ZT_DISABLE_COMPRESSION=1

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT = src/dsm-control.sh

PRE_STRIP_TARGET = zerotier_install

include ../../mk/spksrc.spk.mk

.PHONY: zerotier_install
zerotier_install:
	install -m 755 -d $(STAGING_DIR)/bin
	install -m 755 -d $(STAGING_DIR)/ui
	install -m 755 $(PRODUCT_DIR)/zerotier-one $(STAGING_DIR)/bin/zerotier-one
	cp -r src/ui/* $(STAGING_DIR)/ui
