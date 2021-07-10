# dotfiles

My dotfiles controlled by GNU stow following [this way](https://farseerfc.me/using-gnu-stow-to-manage-your-dotfiles.html)

## Requirements

```bash
sudo pacman -S diff-so-fancy exa ripgrep git-extras
```

```bash
cargo install git-brws
```

## Installing user configuration files

stow zsh

This will symlink the .zshrc file to ~/.zshrc.

## Installing root configuration files

sudo stow -t / pacman

This will symlink the pacman.conf file to /etc/pacman.conf.

Make sure the file doesn't already exist or a symlink cannot be made.

## Special cases

Systemd configurations already exist and should not be deleted to allow symlinking a folder so if you want to install systemd-root use the following commands.

sudo stow -t /etc/systemd/ -d systemd-root user

The timers and services cannot be stowed because systemd cannot enable symlinked unit files. Copy them manually to /etc/systemd/system
