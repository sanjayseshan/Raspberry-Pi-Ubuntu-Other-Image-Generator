# Raspberry Pi Image Generator

Debian Stretch image builder for Raspberry Pi (all versions) (32-bit only).

Based on worky by Klaus M Pfeiffer, http://www.kmp.or.at/~klaus/raspberry/build_rpi_sd_card.sh

script will:
  - create, partition and format an image
  - install and configure base debian jessie system with Open SSH server
  - download rpi-update which will install the nescessary firmware and bootloader for RPi3 (wifi & bt also)
  - install a first-run script that will re-configure SSH server keys and resize partition to fill the disk on the first run.

### Requirements

Debian/Ubuntu/Kali.... host with the following packages installed:

```binfmt-support qemu qemu-user-static debootstrap kpartx lvm2 dosfstools```

### Usage

Optionally, replace id_rsa.pub file with a link to your ssh public key (most likely ~/.ssh/id_rsa.pub) if you want to log into the RPi with your keypair.

```sudo ./build_image-XXXX.sh ```

You can pass block_device (/dev/mmcblk0) to create the image directly on a card, or specify image_file you would like to create. If neither is given, an image file called rpi_basic_jessie_$(date).img will be created. You can write this image to a card using dd or other tools.

root and pi password is ```raspberry```

Support generation of Debian or Ubuntu with armhf or armel (no arm64 yet). Note: Ubuntu discontinued support for armel in 2013.

Only works on a full linux kernel with a Debian-based system....do not bother trying on WSL --> does not work.
