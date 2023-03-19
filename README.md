# arch_unl0kr
Getting unl0kr working to help decrypt tablets and other touchscreen devices running x86_64 bit Arch Linux

Mostly copied from https://github.com/ShapeShifter499/osk-sdl_arch, adjusted to fit unl0kr, thank you ShapeShifter499 for showing me how it can be done :)

unl0kr main project, code, and bug reports can be found at
https://gitlab.com/cherrypicker/unl0kr/

issues regarding how this package works can be filed here

issues with unl0kr itself can be brought up at
https://gitlab.com/cherrypicker/unl0kr/

# Warning

I have little idea what I am doing and thou should be warned if you have even less Idea what you are doing. This package should not be used for day to day unlocking without a backup boot partitin please use a secondary boot partition for trying this out.

Also please use a Boot partition with at least 2GB size, as one boot image and one fallback image take up nearly 500MB per Kernel version installed

If you have more of an idea what you are doing, please feel free to contribute :)

# Installation
```
makepkg -si
```
Make sure unl0kr works on your system by trying it in another tty with `sudo unl0kr` first

# Configuration

Make sure unl0kr is installed to your system and then add unl0kr to your `/etc/mkinitcpio.conf` hooks. `unl0kr` should be inserted before the `filesystems` hook but after `udev` or `systemd` hook (only tested wih udev thus far). Optionally include the `keyboard` and `keymap` hooks if your device has a detachable keyboard or if you sometimes want to plug in a USB or OTG keyboard for passphrase input (not tested without).
