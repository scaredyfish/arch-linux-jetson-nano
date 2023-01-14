# arch-linux-jetson-nano
PKGBUILD files and other bits and pieces to get Arch Linux running on Jetson Nano 

This is a work in progress, mostly made for my own notes, I cannot guarantee it won't brick your nano

nvidia doesn't provide a public url for the .deb files, but they can be found in the driver package found here: https://developer.nvidia.com/embedded/linux-tegra-r3273

Rough steps to get arch booting on nano are:

On a host PC (currently only tested on Ubuntu)

- Download the generic Arch armv8 distribution from: https://archlinuxarm.org/platforms/armv8/generic
- Download the Jetson Nano driver package https://developer.nvidia.com/embedded/linux-tegra-r3273
- extract the driver package, then extract the Arch distribution into ``Linux_for_Tegra/rootfs``
- ``mkdir rootfs/boot/extlinux.conf``
- ``sudo cp bootloader/extlinux.conf rootfs/boot/extlinux/extlinux.conf``
- put your nano into recovery mode (either via jumper, or via ``sudo reboot --force forced-recovery`` if you already have ubuntu running)
- run ``./nvflash.sh <board> mmcblk0p1`` where <board> is the name of one of jetson-nano*.conf (minus the .conf), or ``./nvautoflash.sh`` to autodetect the board. 

Once the flashing is done, you should be able to reboot into Arch, at which point just follow the Arch installation guide https://wiki.archlinux.org/title/installation_guide



