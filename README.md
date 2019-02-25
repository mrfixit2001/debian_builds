This repo contains debian builds with 2 partitions, one for the rockchip boot and one which has a vanilla debian filesystem with a core set of default packages. 

Included in this build are the following debian packages: 
firmware-realtek fake-hwclock libcec-dev libp8-platform-dev cmake autotools-dev parted rsync dosfstools curl xz-utils iw rfkill wpasupplicant openssh-server alsa-utils nano git build-essential vim jq ethtool wget ca-certificates software-properties-common sudo htop eatmydata systemd systemd-sysv udev apt kmod locales sudo netbase net-tools ethtool iproute iputils-ping ifupdown dhcpcd5 firmware-brcm80211 wpasupplicant ssh avahi-daemon ntp wireless-tools apt-transport-https

The GBM + X11 MALI library and headers are also installed in this build, but they are not a debian package (read below). If you want to use Wayland, just download the correct mali library file from the rockchip libmali repo and copy the library over as this file: /usr/lib/arm-linux-gnueabihf/libmali.so

There are three custom parts of this build:
- MrFixIt's custom kernel (https://github.com/mrfixit2001/rockchip-kernel) which has been optimized for usage for retro-gaming and 4k high definition media playback. For the RockPro64, it also allows for the use of Wifi, Bluetooth, and PCIe all at the same time.
- Rockchip MALI userspace drivers are installed manually - meaning there's no debian package for this installation. The reason here is that often other packages (such as MESA) overwrite the libraries included by the mali driver. So if at some point this happens, simply run /usr/lib/arm-linux-gnueabihf/install_mali.sh and it will re-create all the symlinks for the mali driver to begin working again.
- MrFixIt's custom bootup service which provides two features: 
    1) enables this build to boot from sd, emmc, and (if you have SPI flashed) usb
    2) *by default* generates a 3rd partition that fills up the rest of the available space on the disk and is mounted to /home

* CHANGING THE DEFAULT AND USING ONLY 2 PARTITIONS *
You have the option to change the default and tell the script to only use two partitions, expanding the main system partition to the full capacity of the disk. 
WARNING: changing this option will delete anything you have previously saved to the /home folder so back up your data before making this change!
To change this default simply type this:
  sudo touch /usr/bin/2parts.touch
and then reboot. This creates a new empty file that tells the script to use the alternative setting. Do not remove this empty file.


Default usernames and passwords:
- User: root    Pass: root
- User: rock    Pass: rock
