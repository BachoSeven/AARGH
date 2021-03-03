# Replace tabs with spaces(vimium):
``` sh
1,$s/\t/ /g
```

# crontab:
``` sh
@hourly		DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/desk >/dev/null 2>&1
@hourly		DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/checkup >/dev/null 2>&1
*/5 * * * *	DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/cronbat >/dev/null 2>&1
*/30 * * * *	XAUTHORITY=/run/user/$(id -u $USER)/Xauthority DISPLAY=:0 ~/.local/bin/cron/feedup >/dev/null 2>&1
30 16 * * *	~/.local/bin/scripts/bmbkp ~/.config/browser/bkp/bm/bm.html && ~/.local/bin/scripts/histbkp ~/.config/browser/bkp/hist/hist.html && cd ~/.config/browser/bkp && drive push -no-prompt hist/hist.html bm/bm.html
*/2 * * * *	/usr/bin/mailsync
```

# Bluetooth headphones autoconnect
`/etc/pulse/default.pa`:
## automatically switch to newly-connected devices
`load-module module-switch-on-connect`

# Give users in the wheel group permission to use sudo
`echo "%wheel ALL=(ALL) ALL" > /mnt/etc/sudoers.d/01_wheel_all`
