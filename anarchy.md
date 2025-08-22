## Packages to be installed through Anarchy (or else)

- Kernel: Zen-Linux
- openssh
- zsh
- networkmanager [can be installed through archinstall]
- Grub(with efibootmgr and os-prober if needed) [can be installed through archinstall], or setup limine(already in progs.csv), with Root UUID and usual kernel cli[for instance,
  chroot into install and switch to limine].

## AARGH
``` sh
curl -O https://raw.githubusercontent.com/BachoSeven/AARGH/master/aargh.sh
# Install chaotic packages: https://aur.chaotic.cx/
sudo sh aargh.sh
```

## SSH
- For now, this is done semi-automatically with a pastebin before installing from github.

## Setups post-install
### Main
- **swapfile**: ~/slsk/resources/Linux/SwapCommands.sh
- `crontab -e`
- `mkclean` installed packages (plus i.e. `grub` if using `limine`)
- Install `mpd-light-pulse-ffmpeg` (my package); substitute `nodejs` with `nodejs-lts-hydrogen` or the most recent LTS available; octave: compile `openblas-lapack` to replace the default blas implementation (optional).
- nmdm-git: setup polkit permissions for NM (info in sysdots repo) + disable `NetworkManager-wait-online.service`
- unbound: `sudo unbound-control-setup`, enable service, cp unbound.conf from stuff/etc; set as system resolver (archwiki), and lock the resolv.conf file(`sudo chattr +i /etc/resolv.conf`).
- nbfc: enable --now service; `nbfc config -a "Asus Zenbook UX310UAK"`(or else); `nbfc status -s` to check.
- plymouth: hook in mkinitcpio[included in sysdots but needs to be checked manually] && regenerate initramfs; copy `sysdots`'s `watermark.png` to `/usr/share/plymouth/themes/spinner/watermark.png`.
- copy stuff to /etc and /root (using sysdots, better manual..) (disables systemd-homed.service amongst other things; might have to disable it first.)
- ./add-gtypist-exercises.sh
- psd (enable `psd.service` as user after copying sudoers file)
- configure rescrobbled (put api in config) and mpdscribble (goes in /etc) (user service too)
- crontab (enable `cronie.service`):
  ``` sh
  @hourly		DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/checkup >/dev/null 2>&1
  */5 * * * *	DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u $USER)/bus ~/.local/bin/cron/cronbat >/dev/null 2>&1
  */30 * * * *	~/.local/bin/cron/feedup >/dev/null 2>&1
  30 16 * * *	~/.local/bin/scripts/bmbkp ~/.config/browser/bkp/bm/bm.html && ~/.local/bin/scripts/histbkp ~/.config/browser/bkp/hist/hist.html && cd ~/.config/browser/bkp && ~/.local/bin/scripts/txtbkp && drive push -no-prompt hist/hist.html bm/bm.html bm/plain hist/plain
  */2 * * * *	/usr/bin/mailsync >/dev/null 2>&1
  ```
### Extra
- w3m: copy .cgi scripts(see README)
- nicotine+ backup import
- spotify: download `Fluent`'s css, ini, assets and js, then `sudo chmod 777 /opt/spotify; sudo chmod 777 /opt/spotify/Apps -R` and then `spicetify backup apply enable-devtool`
- configure Ungoogled-chromium.
- keepassxc import database && sync with chromium extension
- gpg: import keys; ~~change sockets~~:
    <!-- Questa roba è commentata perché non serve davvero, funziona anche senzsa spostare i file dei socket nella directory con l'hash. -->
 <!-- "Note that this currently does not work out-of-the-box using systemd user units and socket-based activation, since the socket directory changes based on the hash of -->
 <!-- $GNUPGHOME. You can get the new socket directory using gpgconf --dry-run --create-socketdir, and have to modify the systemd user units to listen on the correct sockets -->
 <!-- accordingly." -->
 <!-- Sockets to change(5)[all with systemctl --user edit --full]: gpg-agent.socket, gpg-agent-extra.socket, gpg-agent-browser.socket, gpg-agent-ssh.socket, and dirmngr.socket. -->
 <!-- Syntax to change them (sysu edit): `ListenStream=%t/gnupg/d."${HASH}"/S."${socketname}"` -->
 <!-- Example vim substitute command `%s/gnupg\//&d\.babif6xw6skmb8ps84qeyyam\//g` -->
 <!-- Finally, do `gpgconf --create-socketdir` and reboot (hopefully it works). -->
- mutt-wizard: Just add accounts normally, and then, BEFORE SYNCING, comment out "Flatten" rows in MBSYNCRC (and then remove ~/.urlview) [also, deduplicate muttrc and mbsyncrc and
  msmtp/config files... might be worth removing the relevant lines beforehand]; migrate abook contacts.
  - for mail.dm.unipi.it: use `--cacert CERTIFICATE` for `curl` command in `mw`, where the certificate is obtained through `openssl s_client -showcerts -servername student.dm.unipi.it -connect student.dm.unipi.it:993 2>&1 < /dev/null | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' | sed -ne '1,/-END CERTIFICATE-/p' > student.dm.unipi.it.pem` + add certificates in `mbsynrc` and `msmtp`'s configs.
