# dotfiles

My dotfiles controlled by GNU stow following [this way](https://farseerfc.me/using-gnu-stow-to-manage-your-dotfiles.html)

## 代理设置
使用 WSLProxy.sh 可以将 WSL 自动配置代理的命令追加到 .com/zsh/.zshrc 中
其他系统不要使用，否则会出现代理错误

## Requirements

```bash
sudo pacman -S diff-so-fancy exa ripgrep git-extras
```

```bash
cargo install git-brws
```

## Installing user configuration files

```
stow zsh
```

This will symlink the .zshrc file to ~/.zshrc.

## Installing root configuration files

```bash
sudo stow -t / pacman
```

This will symlink the pacman.conf file to /etc/pacman.conf.

Make sure the file doesn't already exist or a symlink cannot be made.

## Special cases

Systemd configurations already exist and should not be deleted to allow symlinking a folder so if you want to install systemd-root use the following commands.

```bash
sudo stow -t /etc/systemd/ -d systemd-root user
```

The timers and services cannot be stowed because systemd cannot enable symlinked unit files. Copy them manually to /etc/systemd/system
