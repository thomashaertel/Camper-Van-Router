# Camper-Van-Router
Camper Van UMTS/WiFi Router with Music Server and BT A2DP based on OpenWRT Chaos Calmer (15.05)

# Hardware
The following components are used to build the device:
- Raspberry Pi 2 B
- Edimax EW-7612UAN V2
- Edimax EW-7811UN
- LogiLink BT0015 USB Bluetooth V4.0 EDR Class1
- UMTS Device (currently missing and not tested)

# Installation Instructions
1. Download OpenWRT Image for Raspbaerry Pi 2: http://downloads.openwrt.org/chaos_calmer/15.05/brcm2708/bcm2709/openwrt-15.05-brcm2708-bcm2709-sdcard-vfat-ext4.img
2. Copy image on sd card
3. Connect Raspberry Pi to monitor and keyboard
4. Boot Raspberry Pi with sd card
4. Press "Enter" to login to console

## Setup Router

### Change Password
$ passwd

### Configure internet access over local LAN for installation
$ uci set network.lan.proto=dhcp <br/>
$ uci commit <br/>
$ reboot

### Install drivers for Edimax WLAN dongles
$ opkg update <br/>
$ opkg install rtl8192cu <br/>
$ opkg install wpa_supplicant hostapd <br/>
$ reboot

### Add german language for Web Interface
$ opkg update <br/>
$ opkg install luci-i18n-base-de

### Configure Web Interface (Luci)
TBD

## Install music server

### Install drivers for Bluetooth dongle
$ opkg update <br/>
$ opkg install kmod-usb-ohci kmod-usb-storage kmod-usb2 <br/>
$ opkg install kmod-bluetooth kmod-bluetooth_6lowpan <br/>
$ opkg install bluez-utils bluez-libs ip <br/>
$ reboot

### 
$ opkg update <br/>
$ opkg install kmod-usb-audio kmod-sound-core <br/>
$ opkg install mpd mpc alsa-utils <br/>
$ reboot

# Used Installation Guides
- http://computers.tutsplus.com/articles/installing-openwrt-on-a-raspberry-pi-as-a-new-home-firewall--mac-55984
- https://devzone.nordicsemi.com/blogs/663/6lowpan-for-bluetooth-low-energy-on-openwrt/ 
- https://silkemeyer.net/wifihifi-how-to-run-music-player-daemon-on-an-openwrt-wifi-router
