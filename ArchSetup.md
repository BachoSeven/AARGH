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
@hourly		/usr/bin/update-gh-hosts
0 * * * *	DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/desk >/dev/null 2>&1
0 * * * *	DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/checkup >/dev/null 2>&1
*/5 * * * *	DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/cronbat >/dev/null 2>&1
*/30 * * * *	DISPLAY=:0 ~/.local/bin/cron/feedup >/dev/null 2>&1
30 16 * * *	~/.local/bin/scripts/bmbkp ~/.config/browser/bkp/bm/bm.html && ~/.local/bin/scripts/histbkp ~/.config/browser/bkp/hist/hist.html && cd ~/.config/browser/bkp && drive push -no-prompt hist/hist.html bm/bm.html
*/2 * * * *	/usr/bin/mailsync
```

# Bluetooth headphones autoconnect
`/etc/pulse/default.pa`:
## automatically switch to newly-connected devices
`load-module module-switch-on-connect`

# Give users in the wheel group permission to use sudo
`echo "%wheel ALL=(ALL) ALL" > /mnt/etc/sudoers.d/01_wheel_all`
