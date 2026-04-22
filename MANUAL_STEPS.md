# Manual Configuration Steps

This document outlines the post-installation tasks required to complete your system configuration, which cannot or should not be fully automated by `install.sh`.

## 1. Browser Logins & App Authentication
* **Web Browsers:** Log into your preferred browsers (Firefox/Chrome) to synchronize your extensions, bookmarks, and passwords.
* **GitHub CLI:** Authenticate your GitHub account manually.
  ```bash
  gh auth login
  ```
* **Zed Editor:** Log in to your Zed account if you use their collaboration or AI features.

## 2. Noctalia Shell / Missing AUR Packages
The install script attempts to install `noctalia` via your AUR helper. If Noctalia Shell is not yet available in the AUR or requires building from a specific private repository, you must clone and build it manually.
* Ensure the target output is placed in your `$PATH` or update the autostart configurations in `.config/niri/cfg/autostart.kdl`.

## 3. Theme Generation & Appearance
While your Catppuccin themes (Mocha/Frappé) are explicitly mapped in Fish and other configs, some GUI tools might require a manual toggle:
* **GTK Themes:** `install.sh` symlinked `~/.config/gtk-3.0` and `~/.config/gtk-4.0`. You may still need to use `nwg-look` or `dconf-editor` to fully apply the theme if Wayland/Niri doesn't pick it up automatically on the first boot.
* **Ghostty:** Launch `ghostty` and ensure its rendering matches your expected config. Ghostty configurations are typically stored in `~/.config/ghostty/config`, which was not present in the dotfiles repository at the time of the initial audit. You may need to create this configuration manually or sync it from elsewhere.

## 4. SSH & GPG Keys
For security reasons, your private keys are not tracked in this dotfiles repository.
* Restore your `~/.ssh` and `~/.gnupg` directories from your secure backup or hardware token.
* Fix permissions:
  ```bash
  chmod 700 ~/.ssh
  chmod 600 ~/.ssh/id_rsa
  chmod 644 ~/.ssh/id_rsa.pub
  ```

## 5. Docker Permissions
While `install.sh` installed Docker, you may need to add your user to the `docker` group to run it without `sudo/run0` if the post-install hooks didn't do it.
```bash
sudo usermod -aG docker $USER
newgrp docker
```
Enable the Docker service:
```bash
sudo systemctl enable --now docker
```

## 6. Restart Your Session
For Niri to load properly, and for your default shell change to take effect, completely log out of your current session (or reboot your computer) and select the **Niri** session from your display manager.
