## Packages

- imagemagick
- openssh
- wget

## Stuff
- `zsh`
- install efibootmgr if needed...
- same for os-prober
- use Grub:)
- activate touchpad, dhcpd(i think) to activate ip at startup, networkmanager, wifi stuff, pppoe(ethernet), also bluez stuff if asked.

### SSH [TODO]
- this needs to be done "manually" with a pastebin before installing from github...

## AARGH
``` sh
wget https://raw.githubusercontent.com/BachoSeven/AARGH/master/aargh.sh
sudo sh aargh.sh (if gh PAT is alright)
```

## Setups post-install
- **Dotbare** (see dotbare.md)
- remove asciidoc(used to install xsv docs)
- swapfile
- copy stuff from /etc (disables systemd-homed.service amongst other things; might have to disable it first.)
- plymouth: hook in mkinitcpio && regenerate initramfs; `sudo cp /usr/share/plymouth/arch-logo.png /usr/share/plymouth/themes/spinner/watermark.png`
- tlp activation
- systemctl: set-default multi-user-target; enable nordvpn.service
- sudo mandb
- crontab install
- clean installed packages
- nmdm-git: setup polkit permissions for NM (wiki) + sctl disable nm-wait-online.service
- soulseek backup import
- unbound: enable service, cp unbound.conf from stuff/etc; set as system resolver (bookmarks, wiki), and lock the .conf file.
- ./gtypist-exercises.sh
- check keys from `https://lonewolf.pedrohlc.com/chaotic-aur/`.
- install ungoogled-chromium from Chaotic AUR && configure it.
- keepassxc import database && sync with chromium extension
- DVD Ripping: install whipper-git WITH <'python-discid'# for calculating Musicbrainz ids, until they fix it upstream
- weechat-plugins autoloading at startup: `ln -s /usr/share/weechat/python/weechat-matrix.py -t ~/.weechat/python/autoload`; `ln -s /usr/lib/weechat/python/notify_send.py -t $XDG_CONFIG_HOME/weechat/python/autoload`; `ln -s /usr/lib/weechat/python/vimode.py -t $XDG_CONFIG_HOME/weechat/python/autoload`; `ln -s /usr/lib/weechat/python/edit.py -t $XDG_CONFIG_HOME/weechat/python/autoload`
- bootstrap weechat with https://wiki.archlinux.org/index.php/WeeChat; and also from https://weechat.org/files/doc/stable/weechat_quickstart.en.html
- enable intel-undervolt service
