# Arch Linux Quick Setup
###### Source: Luke Smith Youtube

- Make bootdisk `dd if=<INPUT_FIle> of=<OUTPUT_DEVICE> status="progress"`
- Device setup
```
wifi-menu
timedatectl set-ntp true
```
- Check devices connected
```
lsblk
blkid or cat /dev/disk/by-uuid
```
- Format disk
```
Alternate: cfdisk /dev/sdb
fdisk -l
fdisk /dev/sdb
    d - delete partition
    n - new partition
    p - primary partition, e - extended partition
    1-4 - for 4 primary partitions
    +200M (200MB) hitting Enter will take full drive
    w - write changes to disk
```
- Make filesystem
```
mkfs.ext4 /dev/sdb1
#mkswap /dev/sdb2
#swapon /dev/sdb2
```
- Mount filesystem
```
mkdir /mnt/boot and /mnt/home subdirs
mount /dev/sdb3 /mnt
#mount /dev/sdb1 /mnt/boot
#mount /dev/sdb4 /mnt/home
```
- Install Archlinux
```
pacstrap /mnt base base-devel vim
```
- Generate fstab
```
genfstab -U /mnt - with UUID check if ok then do next
genfstab -U /mnt >> /mnt/etc/fstab
```
- Install Bootloader
```
arch-chroot /mnt
pacman -S grub-bios
grub-install - -target=i386-pc /dev/sdb
#mkinitcpio -p linux
grub-mkconfig -o /boot/grub/grub.cfg
```
- Setup user
```
passwd
```
- OS Setup
```
vim /etc/locale.gen - /en_US line need to be uncommented then run
locale-gen
vim /etc/locale.conf type the following
LANG=en-US.UTF-8

ln -sf /usr/share/zoneinfo/America/Phoenix /etc/localtime
echo <name> > /etc/hostname OR vim /etc/hostname - type the name and save
```
- Network Manager (optional)
```
pacman -S networkmanager
systemctl enable NetworkManager
```
- Exit shell, unmount and Reboot to system
```
exit
umount -R /mnt # recursive unmount all
reboot
```
- Provide user with device management priveledges and sudo
```
useradd -m -G wheel -s /bin/bash <username>
passwd <username>
visudo and uncomment wheel ALL=(ALL) ALL
```
- Xwindows and driver installation
```
pacman -S xorg-server xorg-apps xorg-xinit
pacman -S xf86-video-intel (/amdgpu/nouveau/vesa (generic driver))
```
- Window Manager options
```
i3wm #Preferred
gdm, gnome, gnome-extra
lxdm, lxde or lxde-gtk3
other DM: lightdm, slim, xorg-xdm
other DE: cinnamon, mate, mate-gtk3, xfce4
other DE apps: nemo-fileroller, mate-extra, xfce4-goodies

systemctl start lxdm.service
systemctl enable lxdm.service
```
- Reboot and sync clock
```
reboot

hwclock --systohc --utc
