# Den1zzfiles

A zero-touch, fully automated bootstrap installer and dotfiles repository for my personal Linux environment.

Target Environment: **CachyOS x86_64** (Wayland)

## 🚀 Quick Install

To install the complete environment directly from GitHub, run the following command in your terminal:

```bash
curl -fsSL https://raw.githubusercontent.com/Den1zzDev/Den1zzfiles/main/install.sh | bash
```

### 🔍 Dry-Run Mode (Recommended First Step)

You can run the installer in dry-run mode to see exactly what mutating commands (package installations, symlink creations) would be executed, without actually changing anything on your system:

```bash
curl -fsSL https://raw.githubusercontent.com/Den1zzDev/Den1zzfiles/main/install.sh | bash -s -- --dry-run
```

## ⚠️ Security Warning

**Never blindly pipe scripts from the internet directly into your shell.**

Always inspect the raw code before executing the curl command. You can review the `install.sh` script here:
[https://raw.githubusercontent.com/Den1zzDev/Den1zzfiles/main/install.sh](https://raw.githubusercontent.com/Den1zzDev/Den1zzfiles/main/install.sh)

> **Note:** The `install.sh` script is heavily automated (AI-generated) to bootstrap the environment. As noted in the script's header, it is currently "vibe-coded" and will be refactored when time permits. Proceed with caution.

## 🛠️ Included Configurations

This repository tracks and manages the configurations for the following stack:

*   **Window Manager:** Niri (with split modular configs)
*   **Shell:** Fish (with Atuin, zoxide, fzf integrations)
*   **Prompt:** Starship (Catppuccin styling)
*   **Terminal Environment:** Ghostty
*   **Editor:** Zed / Micro
*   **UI/Theming:** Noctalia Shell, GTK 3.0/4.0
*   **CLI Utilities:** eza, bat, ripgrep, fd, dust, btop, uutils-coreutils

## 📋 Post-Installation (Manual Steps)

The `install.sh` handles the heavy lifting, including package installation (native and AUR) and idempotent FHS-compliant symlinking. However, some tasks cannot be automated.

Please refer to the [MANUAL_STEPS.md](MANUAL_STEPS.md) for post-installation tasks, such as browser logins, theme generation steps, SSH/GPG key restoration, and Docker group configuration.
