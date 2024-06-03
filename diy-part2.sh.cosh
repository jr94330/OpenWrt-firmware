#!/bin/bash
#
# https://github.com/P3TERX/Actions-OpenWrt
# File name: diy-part2.sh
# Description: OpenWrt DIY script part 2 (After Update feeds)
#
# Copyright (c) 2019-2024 P3TERX <https://p3terx.com>
#
# This is free software, licensed under the MIT License.
# See /LICENSE for more information.
#

# Modify default IP
sed -i 's/192.168.1.1/192.168.31.1/g' package/base-files/files/bin/config_generate

# Modify default theme
sed -i 's/luci-theme-bootstrap/luci-theme-argon/g' feeds/luci/collections/luci/Makefile

# Modify hostname
sed -i 's/OpenWrt/XiaoMi BE7000 OpenWrt/g' package/base-files/files/bin/config_generate

# Add additional plugins
# Ensure the following plugins are installed
PLUGINS=(
    luci-app-bird1-ipv4
    luci-app-bird1-ipv6
    luci-app-ddns-go
    luci-app-ddns
    luci-app-filetransfer
    luci-app-firewall
    luci-app-nlbwmon
    luci-app-samba
    luci-app-samba4
    luci-app-syncdial
    luci-app-clash
    luci-app-ramfree
    luci-app-easymesh
    luci-app-argon-config
    luci-app-attendedsysupgrade
    luci-app-docker
    luci-app-fileassistant
    luci-app-aria2
    luci-app-passwall
    luci-app-webadmin
    luci-app-uhttpd
)

for plugin in "${PLUGINS[@]}"; do
    echo "CONFIG_PACKAGE_${plugin}=y" >> .config
done

# Run feed updates and install all packages
./scripts/feeds update -a
./scripts/feeds install -a
