# Fedora Setup Guide

Quick reference for the Fedora post-installation setup. For the full guide, see [`setup/fedora_initial_setup.md`](../../setup/fedora_initial_setup.md).

## Quick Reference

### System Update
```bash
sudo dnf update -y
sudo dnf upgrade -y
```

### RPM Fusion
```bash
sudo dnf install -y \
  https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

### Flathub
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

### Multimedia Codecs
```bash
sudo dnf groupupdate core
sudo dnf groupupdate multimedia
sudo dnf groupupdate sound-and-video
```

### FFmpeg
```bash
sudo dnf install ffmpeg
```

## Full Guide

For detailed explanations and additional steps, see [`setup/fedora_initial_setup.md`](../../setup/fedora_initial_setup.md).

---

[Back to Documentation](../README.md)
