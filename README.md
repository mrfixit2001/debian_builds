This repo contains 2-partition debian builds which have a vanilla debian filesystem with a core set of default packages. 

There are two customized parts of this build:
- MrFixIt's custom kernel which has been optimized for usage for retro-gaming and 4k high definition media playback
- MrFixIt's custom bootup service which provides two features: 
    1) enables this build to boot from sd, emmc, and (if you have SPI flashed) usb
    2) generates a 3rd partition that fills up the rest of the available space on the disk and is mounted to /home

Default usernames and passwords:
- User: root    Pass: root
- User: rock    Pass: rock
