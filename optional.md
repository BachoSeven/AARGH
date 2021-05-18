- tauon(amazing music player) :
```
A,tauon-music-box,"is a modern streamlined music player."
```
- Installing `mpdris2`, `mpv-mpris-git` and `mconnect-git` to connect to my smartphone;
- Installing `katcr` (jackett CLI interface) (need to add jackett API to katcr.ini)
- cups(+avahi-daemon for network printers with IPP everywhere), jacket, nordvpn: enable services on demand so not to clutter boot. For the `nordvpnd` service, from version 3.8.8 onwards, we ~~also need to create~~ have to be in the `nordvpn` group.
- enable jacket in qbittorrent(update search engines + add jacket API; also, add indexers to jackett)
- install `annepro2-tools-git` in order to compile the annepro2_tools binary with pacman
- Install:
  ```
,samba,"is the SMB fileserver."
A,wsdd,"Is a Web Service Discovery Daemon for SMB."
  ```
for Samba support.
- weechat(+plugins):
  - installation:
  ,weechat,"is the IRC client."
  A,weechat-edit-git,"is the matrix client for Weechat."
  A,weechat-matrix-git,"is the matrix client for Weechat."
  A,weechat-notify-send,"is the matrix client for Weechat."
  A,weechat-vimode-git,"is the matrix client for Weechat."
  - configuration:
    - weechat-plugins autoloading at startup: `ln -s /usr/share/weechat/python/weechat-matrix.py -t ~/.config/weechat/python/autoload`; `ln -s /usr/lib/weechat/python/notify_send.py -t $XDG_CONFIG_HOME/weechat/python/autoload`; `ln -s /usr/lib/weechat/python/vimode.py -t $XDG_CONFIG_HOME/weechat/python/autoload`; `ln -s /usr/lib/weechat/python/edit.py -t $XDG_CONFIG_HOME/weechat/python/autoload`
    - bootstrap weechat with https://wiki.archlinux.org/index.php/WeeChat; and also from https://weechat.org/files/doc/stable/weechat_quickstart.en.html (some stuff might be
      already set by weechat.conf from dotfiles repo).
