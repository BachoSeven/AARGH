## INSTALL

- AUR

## SETUP

- Set env variable to customize dotbare location:
``` sh
export DOTBARE_DIR="$HOME/.cfg"
export DOTBARE_TREE="$HOME"
DOTBARE_BACKUP=$HOME/.local/share/dotbare
```

- Give dotbare your remote URL and let it handle the rest (with ssh & cloning submodules at checkout):
`dotbare finit -u https://github.com/kazhala/dotfiles.git -s`
