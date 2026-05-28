# Frequently Asked Questions

## General

### Which Fedora versions are supported?
The guide is tested on Fedora 42+. Most steps work on earlier versions too, but package names or commands may differ.

### Can I use this on other distributions?
The guide is Fedora-specific (uses `dnf`, `rpm`, etc.). The concepts apply to other distros, but commands will differ.

### Do I need to follow all steps?
No. Pick the sections relevant to you. System updates and repositories are recommended for everyone.

## Repositories

### What is RPM Fusion?
A third-party repository providing software that Fedora can't ship by default (due to licensing): media codecs, NVIDIA drivers, etc.

### Do I need both free and non-free?
- **free**: Open-source software (recommended for everyone)
- **non-free**: Proprietary software (needed for NVIDIA drivers, some codecs)

## Multimedia

### Why do I need FFmpeg?
Many media players and applications depend on FFmpeg for audio/video processing. Without it, some formats won't play.

### What is hardware video acceleration?
Using your GPU to decode/encode video, reducing CPU usage and improving battery life on laptops.

## Flatpak

### Flatpak vs DNF?
- **DNF**: System packages (fast, native)
- **Flatpak**: Sandboxed applications (more secure, always up-to-date)

Both can coexist. Use DNF for system tools and Flatpak for desktop applications.

## GNOME

### What is Extension Manager?
A GUI app for managing GNOME Shell extensions. Install it via Flatpak:
```bash
flatpak install flathub com.mattjakeman.ExtensionManager
```

## Troubleshooting

### DNF is slow
Try enabling fastest mirror:
```bash
echo 'fastestmirror=1' | sudo tee -a /etc/dnf/dnf.conf
```

### RPM Fusion installation failed
Ensure your system is updated first:
```bash
sudo dnf update -y
```

---

**Last Updated**: 2026-05-25
