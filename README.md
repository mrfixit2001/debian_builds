This repo contains debian builds with 2 partitions, one for the rockchip boot and one which has a vanilla debian filesystem with a core set of default packages. 

Included in this build are the following debian packages: 
firmware-realtek fake-hwclock libcec-dev libp8-platform-dev cmake autotools-dev parted rsync dosfstools curl xz-utils iw rfkill wpasupplicant openssh-server alsa-utils nano git build-essential vim jq ethtool wget ca-certificates software-properties-common sudo htop eatmydata systemd systemd-sysv udev apt kmod locales sudo netbase net-tools ethtool iproute iputils-ping ifupdown dhcpcd5 firmware-brcm80211 wpasupplicant ssh avahi-daemon ntp wireless-tools apt-transport-https

The GBM (non-X11 and non-Wayland) MALI library and headers are also installed in this build, but they are not a debian package (read below). If you want to use X11 or Wayland, just download the correct mali library file from the rockchip libmali repo and copy the library over as this file: /usr/lib/arm-linux-gnueabihf/libmali.so

There are three custom parts of this build:
- MrFixIt's custom kernel which has been optimized for usage for retro-gaming and 4k high definition media playback
- Rockchip MALI userspace drivers are installed manually - meaning there's no debian package for this installation. The reason here is that often other packages (such as MESA) overwrite the libraries included by the mali driver. So if at some point this happens, simply run /usr/lib/arm-linux-gnueabihf/install_mali.sh and it will re-create all the symlinks for the mali driver to begin working again.
- MrFixIt's custom bootup service which provides two features: 
    1) enables this build to boot from sd, emmc, and (if you have SPI flashed) usb
    2) generates a 3rd partition that fills up the rest of the available space on the disk and is mounted to /home

Default usernames and passwords:
- User: root    Pass: root
- User: rock    Pass: rock
