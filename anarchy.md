## Packages to be installed through Anarchy (or else)

- Kernel: Zen-Linux
- openssh
- zsh
- networkmanager [can be installed through archinstall]
- wget [installed by archinstall-minimal]
- Grub(with efibootmgr and os-prober if needed) [can be installed through archinstall], or setup limine(already in progs.csv), with Root UUID and usual kernel cli.

## AARGH
``` sh
wget https://raw.githubusercontent.com/BachoSeven/AARGH/master/aargh.sh
# Install chaotic packages: https://aur.chaotic.cx/
sudo sh aargh.sh
```

## SSH
- For now, this is done semi-automatically with a pastebin before installing from github.


## Setups post-install
- **Dotbare** (see dotbare.md)
- **swapfile**
- copy stuff from /etc (using sysdots, TODO) (disables systemd-homed.service amongst other things; might have to disable it first.)
- plymouth: hook in mkinitcpio && regenerate initramfs; `sudo cp /usr/share/plymouth/arch-logo.png /usr/share/plymouth/themes/spinner/watermark.png`
- crontab install
- `mkclean` installed packages (plus i.e. `grub` if using `limine`)
- nmdm-git: setup polkit permissions for NM (info in sysdots repo) + sctl disable nm-wait-online.service
- soulseek backup import
- unbound: enable service, cp unbound.conf from stuff/etc; set as system resolver (archwiki), and lock the resolv.conf file(`sudo chattr +i /etc/resolv.conf`). (and disable
  systemd-resolved(?))
- ./add-gtypist-exercises.sh
- configure Ungoogled-chromium.
- keepassxc import database && sync with chromium extension
- start pkgstats.timer
- disable redshift and dunst(--user) services (both work better when started from xprofile).
- w3m: copy .cgi scripts(see README)
- put ~/tmp/web-stuff/unified+gambling+fakenews_hosts in /etc/hosts
- mutt-wizard: Just add accounts normally, and then, BEFORE SYNCING, comment out "Flatten" rows in MBSYNCRC (and then remove ~/.urlview)
- spotify: `sudo chmod 777 /opt/spotify; sudo chmod 777 /opt/spotify/Apps -R` and then `spicetify backup apply`
- octave: compile `openblas-lapack` to replace the default blas implementation.
- gpg: import keys; ~~change sockets~~:
         <!-- "Note that this currently does not work out-of-the-box using systemd user units and socket-based activation, since the socket directory changes based on the hash of -->
         <!-- $GNUPGHOME. You can get the new socket directory using gpgconf --dry-run --create-socketdir, and have to modify the systemd user units to listen on the correct sockets -->
         <!-- accordingly." -->
 <!-- Sockets to change(5)[all with systemctl --user edit --full]: gpg-agent.socket, gpg-agent-extra.socket, gpg-agent-browser.socket, gpg-agent-ssh.socket, and dirmngr.socket. -->
 <!-- Syntax to change them (sysu edit): `ListenStream=%t/gnupg/d."${HASH}"/S."${socketname}"` -->
 <!-- Example vim substitute command `gnupg\//&d\.babif6xw6skmb8ps84qeyyam\//g` -->

## Services (done through aargh, here for reference)
- nbfc: enable --now service; `nbfc config -a "Asus Zenbook UX310UAK"`(done through sysdots repo); `nbfc status -s` to check.
- enable intel-undervolt service
