Based on 5ilver's charmbian script, but modified to install Ubuntu focal instead.

For best results, use tasksel to install mate desktop.

What works:
* WiFi configured using nmcli
* Touchpad
* Lots of other stuff

What doesn't work:
* Sound
* Probably a bunch of other stuff I haven't investigated
* Brightness control on keyboard hotkeys (it works with the slider in the GUI)

to do: 
* Choice to install Ubuntu with Mate or Debian with Fluxbox
* Incorporate archbk script to automate install from ChromeOS -> Arch USB -> Ubuntu/Debian on internal storage including set up user account
* Get sound working (maybe using alsa dotfiles from ChromeOS itself)
* Try to incorporate the GalliumOS Touchpad driver


FEEL FREE TO USE THIS FOR WHATEVER YOU LIKE. LET ME KNOW IF YOU KNOW HOW TO FIX SOUND.

////////////////////////////////////////////////////////////////

ORIGINAL README BELOW

////////////////////////////////////////////////////////////////

charmbian

Debian Buster install script for samsung arm chromebooks. Designed to be run ON the target device from an arch boot stick created from https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2. Copy charbian.sh to partition 2 when creating the stick, or get it some other way after you've booted into the usb environment. You will need to use CTRL+u at the dev mode screen, and you cannot boot from the blue usb3 port.

To run, just 'bash charmbian.sh', then select your wifi, enter the target device path (/dev/mmcblk0 for internal emmc), and hurry up and wait. 

The magic

The magic part is just a honking debootstrap command to build a usable debian root from upstream sources using the arch kernel and modules to get you off of google's udders. It then does a few useful tweaks to make the system usable on first boot.


But what does it dooooooo?

* Partitions your device
* Copies arch kernel and modules
* Grabs debootstrap
* Debootstraps a debian system
* Puts a nice trackpad config in place (broken, but it's a *really* nice config)
* Disables DPMS in xorg (broken)
* Sleep hacks in ACPI to disable KB/mouse wake when lid is closed
* Sets up a WPA wifi connection with wpa_passphrase(broken)
* Boots to a minimal fluxbox graphical env
