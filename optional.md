- add ALHP: put

    [core-x86-64-v3]
    Include = /etc/pacman.d/alhp-mirrorlist

    [extra-x86-64-v3]
    Include = /etc/pacman.d/alhp-mirrorlist

    [community-x86-64-v3]
    Include = /etc/pacman.d/alhp-mirrorlist

  at the top of pacman.conf repos, and run `sudo pacman -Syyuu`.
- `xournalpp`, for graphics tablets.
- Installing `mpdris2`, `mpv-mpris-git` and `mconnect-git` to connect to my smartphone;
- `mathematica`
- cups(+avahi-daemon for network printers with IPP everywhere), jacket, nordvpn: enable services on demand so not to clutter boot. For the `nordvpnd` service, from version 3.8.8 onwards, we also have to be in the `nordvpn` group.
- enable jacket in qbittorrent(update search engines + add jacket API; also, add indexers to jackett)
- compile `blissify-git` for mpd smart playlist generation
- install `annepro2-tools-git-bin` for quick annepro2 firmware flashing
- if on an SSD which supports it (probably, `hdparm -I /dev/sdX | grep TRIM`), enable `fstrim.timer` for longevity.
- put ~/stuff/web-stuff/lists/unified+gambling+fakenews_hosts in /etc/hosts
- `katcr` (jackett CLI interface) (need to add jackett API to katcr.ini)
- Install:
  ```
,samba,"is the SMB fileserver."
A,wsdd,"Is a Web Service Discovery Daemon for SMB."
  ```
for Samba support.
- tauon(amazing music player) :
```
A,tauon-music-box,"is a modern streamlined music player."
```
- deadbeef:
  - deadbeef
  - deadbeef-mpris2-plugin
  - deadbeef-plugin-headerbar-gtk3-git
  - deadbeef-plugin-spectrogram-gtk3-git
  - deadbeef-plugin-waveform-gtk3-git
- `whatscli`
- `jackett-bin` (torrent scraper)
- IRC:
  - `catgirl`
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
- surfer (il pacchetto sta in algebra2)
