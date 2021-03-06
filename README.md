# Camper-Van-Router
Camper Van UMTS/WiFi Router with Music Server and BT A2DP based on OpenWRT Chaos Calmer (15.05)

# Hardware
The following components are used to build the device:
- Raspberry Pi 2 B
- TP-Link TP-WN722N (as WAN interface)
- Edimax EW-7612UAN V2 (as Access Point)
- LogiLink BT0015 USB Bluetooth V4.0 EDR Class1
- UMTS Device (currently missing and not tested)

Note: When running multiple devices with the rtl8192cu driver (e.g. multiple Edimax sticks) you will get huge packet loss on the access point device.

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

### Install utilities
$ okpg install usbutils kmod-usb2 kmod-usb-uhci kmod-usb-ohci <br/>
$ opkg update

### Install drivers for TP-Link TP-WN722N dongle
$ opkg update <br/>
$ opkg install kmod-ath9k-common kmod-ath9k-htc <br/>
$ reboot

### Install drivers for Edimax WLAN dongle
$ opkg update <br/>
$ opkg install rtl8192cu <br/>
$ opkg install wpa_supplicant hostapd <br/>
$ reboot

### Install Huawai UMTS dongle
$ opkg update <br/>
$ opkg install comgt kmod-usb-serial kmod-usb-serial-option kmod-usb-serial-wwan usb-modeswitch

$ vi /etc/config/network <br/>
config interface 'WAN_UMTS' <br/>
        option proto '3g' <br/>
        option device '/dev/ttyUSB0' <br/>
        option service 'umts' <br/>
        option apn '\<Provider APN\>' <br/>
        option pincode '\<Your SIM-PIN\>' <br/>
        option username '\<Providers Username\>' <br/>
        option password '\<Providers Password\>' <br/>
        

Optional for Web Interface: <br/>
$ opkg install luci-proto-3g <br/>
$ reboot

### Add german language for Web Interface
$ opkg update <br/>
$ opkg install luci-i18n-base-de

### Configure Web Interface (Luci)
TBD

## Install music server (Mopidy)
$ opkg update <br/>
$ opkg install python python-pip <br/>
$ opkg install gstreamer1 gstreamer1-libs gstreamer1-plugins-base gstreamer1-utils<br/>
$ opkg install python python-pip <br/>
$ pip install -U PyGObject <br/>
$ pip install -U mopidy <br/>

### Install drivers for Bluetooth dongle
$ opkg update <br/>
$ opkg install kmod-usb-ohci kmod-usb-storage kmod-usb2 <br/>
$ opkg install kmod-bluetooth kmod-bluetooth_6lowpan <br/>
$ opkg install bluez-utils bluez-libs ip <br/>
$ reboot

### Audio
$ opkg update <br/>
$ opkg install kmod-usb-audio kmod-sound-core <br/>
$ opkg install mpd mpc alsa-utils <br/>
$ reboot

# APN Configuration
- http://www.unlockit.co.nz/mobilesettings/
- http://www.hw-group.com/products/HWg-Ares/HWg-Ares_GSM_APN_en.html
- http://www.gsmnation.com/apn/network/calculator/

# Additional Packages
- NZBGet 0.8.0

# Used Installation Guides
- http://computers.tutsplus.com/articles/installing-openwrt-on-a-raspberry-pi-as-a-new-home-firewall--mac-55984
- https://devzone.nordicsemi.com/blogs/663/6lowpan-for-bluetooth-low-energy-on-openwrt/ 
- https://silkemeyer.net/wifihifi-how-to-run-music-player-daemon-on-an-openwrt-wifi-router
