# vim(se proprio):
``` sh
{
mkdir -p "$XDG_DATA_HOME"/vim/{undo,swap,backup}
	"$XDG_CONFIG_HOME"/vim/vimrc
set undodir=$XDG_DATA_HOME/vim/undo
set directory=$XDG_DATA_HOME/vim/swap
set backupdir=$XDG_DATA_HOME/vim/backup
set viewdir=$XDG_DATA_HOME/vim/view
set viminfo+='1000,n$XDG_DATA_HOME/vim/viminfo
set runtimepath=$XDG_CONFIG_HOME/vim,$VIMRUNTIME,$XDG_CONFIG_HOME/vim/after
	~/.profile
export VIMINIT='if !has('nvim') | source "$XDG_CONFIG_HOME/vim/vimrc" | endif'
}
```

# Replace tabs with spaces(vimium):
``` sh
1,$s/\t/ /g
```

# crontab:
``` sh
*/2 * * * * /usr/bin/mailsync >/dev/null 2>&1
*/5 * * * * export DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus; export DISPLAY=:0; . ~/.profile; ~/.local/bin/cron/cronbat
*/10 * * * * /bin/rm -rf ~/.java ~/.macromedia ~/.adobe ~/mconnect ~/.local/state ~/.mozilla ~/.pulse-cookie ~/.steampath
*/30 * * * * export DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus; export DISPLAY=:0; . ~/.profile; ~/.local/bin/cron/feedup
00 * * * *  export DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus; export DISPLAY=:0; . ~/.profile; ~/.local/bin/cron/chekup
```

# Bluetooth headphones autoconnect
`/etc/pulse/default.pa`
# automatically switch to newly-connected devices
`load-module module-switch-on-connect`

# xkcd
https://github.com/itsron717/XKCD

## Ripped off https://github.com/GloverDonovan/dotfiles/tree/master/.archlinux/install-scripts
# Enable colors in pacman by uncommenting the Color line.
`sed -i '/Color/s/^#//g' /mnt/etc/pacman.conf`
# Show package upgrades as a list
`sed -i '/VerbosePkgLists/s/^#//g' /mnt/etc/pacman.conf`
# Give users in the wheel group permission to use sudo
`echo "%wheel ALL=(ALL) ALL" > /mnt/etc/sudoers.d/01_wheel_all`
