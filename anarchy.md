## Packages

- imagemagick
- cups
- openssh
- vsftpd
- wget

## Setups post-install
- swapfile
- plymouth: hook in mkinitcpio && regenerate initramfs
- neovim plugins install
- tlp
- systemctl: set-default multi-user-target; enable nordvpn.service
- sudo mandb
- crontab install
- clean installed packages
- nmdm-git: setup polkit permissions for NM (wiki) + sctl disable nm-wait-online.service
- soulseek backup import
- unbound: enable service, cp unbound.conf from stuff/etc; set as system resolver (bookmarks, wiki), and lock the .conf file.
- ./gtypist-exercises.sh
- compile ungoogled-chromium and install extensions
- keepassxc import database && sync with chromium extension
- DVD Ripping: install whipper-git WITH <'python-discid'# for calculating Musicbrainz ids, until they fix it upstream
