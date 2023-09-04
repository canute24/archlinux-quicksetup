https://www.youtube.com/watch?v=MFMYs1O1yCY
i3 Migration guide swaywm

Core utils and alternatives:
https://wiki.archlinux.org/title/Core_utilities
https://wiki.archlinux.org/title/List_of_applications

system:
permissions		: opendoas [cmd] sudo replacement which is smaller and more secure
fuzzy finder	: broot [cmd] searches is layers is faster
file manager	: lf [tui] no actions defined these will need to be scripted
				: fff [tui] shrinked down version of nnn (bash)
				: zzfm [gui] shrinked down version of spacefm
				: dragon [cmd+gui] utility to connect terminal file managers with gui apps
trash mgmt		: trash-cli [cmd] freedesktop standard cli trash bin (python3)
launcher		: dmenu / rofi / wofi [gui]
statusbar		: polybar [gui] works well with i3
				: waybar [gui] for hyperland
wm				: sway [gui] i3 config compatible for wayland
				: hyperland [gui] fast gpu accelerated compositor (wm term in wayland) for wayland
				: i3-gaps-rounded [gui] rounded windows
lock screen		: i3lock-color [gui] colorful lockscreen should not be installed with i3lock
login manager	: sddm [gui] lightweight login manager fom kde with no dependencies]
hotkey			: sxhkd (simple hotkey daemon) [cmd]
system info		: btop [tui]
				: mission center [gui] similar to win taskmgr
				: radeontop [tui] gpu monitor
				: bomn [tui] netwok monitor
				: wavemon [tui] wireless monitor
power cfg		: powertop [tui]
wallpaper		: feh [cmd]
				: xwallpaper [???]
				: nitrogen [cmd+gui]
wallpcoloextract: pywal [cmd]
screenshot		: grim [cmd]
				: scrot [cmd]
system tray		: trayer [gui]
notifications	: notify [???]
				: dunst [gui]
bluetooth		: bluez [???] bluetooth stack
shell			: zsh [cmd] bash compatible / configurable / addons
terminal		: xterm [cmd] default option for many tools
				: kitty [gui]
				: alacritty [gui] gpu accelerated
				: urxvt [gui] has a deamon to make it run fast
				: st [gui] fast but no scrollback history etc multiple patches require manual adjustment
terminal muxer	: tmux [tui]
				: screen [tui] GNU
ftp server		: uftpd [cmd] simple tftp and ftp server
				: rclone [cmd] swiss army knife of fs once booted into os
file opener		: xdg-open [cmd] freedesktop standard
				: mimeo
wireless switch : rfkill [cmd]
bluetooth mgmt	: bluez [cmd]
wireless		: wpa_supplicant / iwd (smaller, faster, modern replacement) [cmd]
				: networkmanager [cmd] convenience features such as network autoconnect and notifications etc
				: conmanctl [cmd] wifi connection
bootmanager		: systemd-boot [cmd] / manual: efibootmgr [cmd]]

Optional:
polkit			: lxsession [goi] permission monitoring
automouting		: udiskie> udisks2 [gui] automouting disks on access
window info		: xprop [gui]
				: sprox [gui]
disk usage		: ncdu [tui]
				: gdu [tui]
disk format		: cfdisk [tui]

applications:
duplicate finder: rmlint [cmd] creates scripts to delete duplicate
file copy		: rsync [cmd]
FUSE			: rclone [cmd] mount cloud filesystesm
Notification	: ntfy [cmd] deployable server for notificaitons
ssh client		: mosh [cmd] better ssh connections which doesn't easily diconnect like openssh
