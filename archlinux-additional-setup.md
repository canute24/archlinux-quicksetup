# Arch Linux Additional Setup:
### Hardware Config:
##### Source: https://wiki.archlinux.org/index.php/Wireless_network_configuration
Check Hardware
```shell
lspci -l
lsusb
dmesg | grep wifi
dmesg | grep firmware
```
Configure network:
```shell
ip link
ip link set wlp3s0 up
rfkill list
rfkill unblock wifi
ip link show wlp3s0
iw dev interface scan | less #if error then firmware missing
wifi-menu
```
Setup CPU Frequency Scaling:
##### Source: https://wiki.archlinux.org/index.php/CPU_frequency_scaling
```shell
cpupower frequency-info # config file is in /etc/default/cpupower, config read by shell is /usr/lib/systemd/scripts/cpupower
cpupower frequency-set -g powersave # setting governor in this case powersave
cpupower frequency-set -f clock_freq # units are GHz or MHz
```
Other frequency scaling drivers / daemons:
- i7z
- thermald.service

### WIFI CONFIG: 
###### Source: https://wiki.archlinux.org/index.php/WPA_supplicant

FAST START: (Doesn't work with sudo)
```
wpa_passphrase MYSSID passphrase
wpa_supplicant -B -i interface -c <(wpa_passphrase MYSSID passphrase)
dhcpd <interface>
```
SLOW START:
#### File: /etc/wpa_supplicant/wpa_supplicant.conf
```shell
ctrl_interface=/run/wpa_supplicant
update_config=1
```
WPA Config:
```shell
wpa_supplicant -B -i interface -c /etc/wpa_supplicant/wpa_supplicant.conf
wpa_cli
> scan
> scan_results
> add_network
0
> set_network 0 ssid "MYSSID"
> set_network 0 psk "passphrase"
> enable_network 0
<2>CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (reauth) [id=0 id_str=]
>save_config
dhcpd <interface>/
```
SYSTEM CONFIG:
##### Souce: https://wiki.archlinux.org/index.php/General_recommendations
```
install ntfs-3g
cp /etc/fstab ~/home/fstab.bak # Create backup before editing

mkdir /mnt/garage
/dev/sda2 /mnt/garage ntfs-3g defaults,locale=en_US.utf8 0 0
mkdir /mnt/valut
/dev/sda4 /mnt/valut vfat iocharset=utf8,umask=000 0 0
```
https://wiki.archlinux.org/index.php/Users_and_groups
https://wiki.archlinux.org/index.php/Sudo
```
useradd -m -G wheel <USERNAME>
passwd <USERNAME>
visudo /etc/sudoers #uncomment %wheel      ALL=(ALL) ALL
setleds -D +num #numlock on

systemctl enable tmp.mount
systemctl start tmp.mount
https://unix.stackexchange.com/questions/352042/systemd-backed-tmpfs-how-to-specify-tmp-size-manually
tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1777,size=256M 0 0

/var/cache
/var/games
/var/log/apt

systemctl list-unit-files
systemctl list-units #types are .server .mount .device or .socket

systemctl list-unit-files –type=service
systemctl start name.service
systemctl stop name.service
systemctl restart name.service
systemctl reload name.service
systemctl status name.service

systemd-analyze
systemd-analyze-blame

ls -l /dev/disk/by-uuid
fdisk -l
cfdisk
df -h /tmp
du -sh /*
xdiskusage OR ncdu
cat /proc/cpuinfo
man -f foo > whatis command
man -k foo
alias rm -vI and rmdir -vI

Ctrl+Alt+F1/1
ps -elf
kill PID
killall PROCESS_NAME
pkill -15 Xorg
killall5
unzip <> -d /tmp
tar zxf some_software.tar.gz
tar -jxf some_software.tar.bz2

top
htop
powertop

https://wiki.archlinux.org/index.php/Xinit
xorg-xinit will install xinit
startx used to run xinit which reads ~/.xinitrc if not available then /etc/X11/xinit/xinitrc # Appending & at the end of the program will put it in the background
```
