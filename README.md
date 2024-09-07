# Fibocom-FM350-GL
Install instructions for Fibocom FM350-GL 5G modem on Openwrt

Update OpenWRT to snapshot version ( stable version has an old kernel):
sysupgrade https://downloads.openwrt.org/snapshots/targets/mediatek/filogic/openwrt-mediatek-filogic-bananapi_bpi-r3-mini-squashfs-sysupgrade.itb
If you want a clean install, use the -n flag

wget https://openwrt.132lan.ru/packages/23.05/packages/aarch64_cortex-a53/modemfeed/fm350-modem_0.0.2-2_all.ipk
wget https://openwrt.132lan.ru/packages/23.05/packages/aarch64_cortex-a53/modemfeed/luci-proto-fm350_git-24.126.71869-e102c3d_all.ipk
opkg update && opkg install picocom luci fm350-modem_0.0.2-2_all.ipk luci-proto-fm350_git-24.126.71869-e102c3d_all.ipk

add this to /etc/config/network:

config interface 'LTE'
        option proto 'fm350'
        option device '/dev/ttyUSB4'
        option apn 'three.co.uk'
        option auth 'auto'
        option pdp 'ip'
