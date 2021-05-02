# Syslinux Guide: Make bootable USB drives from ISO's

SYSLINUX automatically searches for the syslinux.cfg file in the following order:
```
/boot/syslinux/syslinux.cfg
/syslinux/syslinux.cfg
/syslinux.cfg
```
- vesamenu.c32 from “com32\menu” (optional – creates a fancier menu with splash image. See Create Custom Grub4Dos, GRUB and Syslinux Compatible Splash Images for using splash images with vesamenu.c32)
- reboot.c32 from “com32\modules” (required – adds an option to reboot the computer)
- menu.c32 from “com32\menu” (required – displays the basic Syslinux menu shown below)
- memdisk from “memdisk” (required – kernel to boot floppy images, disk images and some ISOs)

###### Source: https://cects.com/multi-boot-usb-with-syslinux-and-grub4dos/
```
#!syslinux.cfg
#PROMPT = one (1) displays the prompt only, zero (0) will not display the prompt
#TIMEOUT = Time to wait to autoboot in 1/10 secs. zero (0) disables the timeout 
#ONTIMEOUT = The menu item to boot on timeout.
#F1 help.txt = User defined help text file loaded if F1 pressed while menu is displayed

TIMEOUT 600
PROMPT 0
#MENU BACKGROUND /backgroundimages/your_image_here.png
DEFAULT menu.c32
MENU TITLE MULTI-BOOT USB
ONTIMEOUT 3

#Display help screen when F1 pressed on Syslinux Menu Screen
F1 help.txt

LABEL 1
MENU LABEL Reboot
TEXT HELP
Restart the computer.
ENDTEXT
COM32 reboot.c32

LABEL 2
MENU LABEL Reboot USB
TEXT HELP
Reboot the USB
ENDTEXT
localboot 0x80

LABEL 3
MENU LABEL Boot WinME Floppy Image
KERNEL memdisk
APPEND initrd=/winmec/WINME.IMG

LABEL 4
MENU LABEL Boot Puppy Linux 4.31
MENU DEFAULT
KERNEL /puppy/vmlinuz
APPEND initrd=/puppy/initrd.gz pmedia=usbflash psubdir=puppy
```
