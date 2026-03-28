# Fedora 42+ Initial Setup Guide

A comprehensive post-installation guide for setting up Fedora 42 and later versions with all essential configurations, repositories, drivers, and applications.

---

## Table of Contents

1. [System Updates](#system-updates)
2. [Enable Flatpak Support](#enable-flatpak-support)
3. [Enable Third-Party Repositories](#enable-third-party-repositories)
4. [Multimedia Support](#multimedia-support)
5. [GNOME Extensions & Tweaks](#gnome-extensions--tweaks)
6. [System Customization](#system-customization)

---

## System Updates

Start by ensuring your system is fully up to date with the latest security patches and software.

### Update System
```bash
sudo dnf upgrade
```

### Firmware Updates (if supported)
If your system supports firmware updates through LVFS:

```bash
sudo fwupdmgr refresh --force
sudo fwupdmgr get-devices      # Lists devices with available updates
sudo fwupdmgr get-updates      # Fetches list of available updates
sudo fwupdmgr update
```

### Reboot
After completing updates, reboot your system:
```bash
sudo reboot
```

---

## Enable Flatpak Support

Flatpak provides access to a wider range of applications. Fedora may not include all non-free flatpaks by default.

### Add Flathub Repository
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

---

## Enable Third-Party Repositories

### RPM Fusion (Free & Non-Free)

RPM Fusion provides access to additional software that Fedora doesn't include by default, including Steam, Discord, and multimedia codecs.

```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

### Install app-stream metadata
```bash
sudo dnf group upgrade core
sudo dnf group install core
```

### Update System and Reboot
```bash
sudo dnf -y update
sudo reboot
```

---

## Multimedia Support

### Switch to Full FFmpeg
```bash
sudo dnf swap 'ffmpeg-free' 'ffmpeg' --allowerasing
```

### Install Media Codecs
```bash
sudo dnf install libavcodec-freeworld
```

### Hardware Video Acceleration

Enable hardware video decoding with VA-API to reduce CPU load and improve battery life:

```bash
sudo dnf install ffmpeg-libs libva libva-utils
```

---

## GNOME Extensions & Tweaks

### Install GNOME Tweaks

Search for "tweaks" in GNOME Software store and install "GNOME Tweaks" (also available as `gnome-tweaks` package).

```bash
sudo dnf install gnome-tweaks
```

### Install Extension Manager

Extension Manager provides an easy-to-use GUI for browsing, installing, and managing GNOME extensions. Install from GNOME Software or:

```bash
flatpak install flathub com.mattjakeman.ExtensionManager
```

### Recommended GNOME Extensions

Install these extensions via Extension Manager or the GNOME Extensions website:

#### Essential Extensions

- **Dash to Dock** - Persistent dock on your desktop with customizable appearance and behavior
- **AppIndicator and KStatusNotifierItem Support** - Enables system tray icon support for applications that use app indicators

---

## System Customization

### Open Settings

Access the Settings application to customize your system:
- Search for "Settings"
- Customize the following sections:

#### Display Settings
- Adjust screen resolution and refresh rate
- Configure scaling for high-DPI displays (recommended 200% for 4K)
- Arrange multiple displays if needed

#### Sound Settings
- Select output device and configure surround sound
- **Disable Alert Sound**: Scroll down and set "Alert Sound" to "None" (removes annoying notification sounds)

#### Power Settings
- Choose power plan (Balanced or Power Saver)
- Adjust screen blank timeout
- Configure automatic suspend behavior
- Set power button behavior

#### Wi-Fi & Network Settings
- Connect to networks
- Configure static IP addresses if needed
- Manage DNS settings

#### Appearance
- Enable Dark Mode (recommended)
- Customize accent colors
- Set wallpaper

#### Multitasking
- Configure workspace behavior
- Choose between dynamic or fixed workspaces

### Organize Applications

Group related applications in your application menu for better organization:

1. Open the Applications menu
2. Find applications you want to group
3. Click and drag one application over another
4. Name the group appropriately (e.g., "Office", "Media", "Development")
5. Continue adding related applications to the group

---

## Troubleshooting

### Flatpak apps don't appear after installation

Run `flatpak update` to refresh the app database, then log out and back in. If the issue persists, verify the Flathub remote is configured:

```bash
flatpak remotes
```

If Flathub is missing, re-add it using the command in the [Enable Flatpak Support](#enable-flatpak-support) section.

### `fwupdmgr` shows no devices or updates

Not all hardware supports firmware updates via LVFS. You can check which devices are supported:

```bash
fwupdmgr get-devices
```

If no devices with updatable firmware are listed, your hardware may not support LVFS firmware updates. This is not an error.

### GNOME Extensions don't work after update

GNOME extensions may break after a major GNOME version update. Check for extension updates in Extension Manager, or visit the [GNOME Extensions website](https://extensions.gnome.org/) for updated versions. Some extensions may need to be replaced if they are no longer maintained.

### RPM Fusion packages not found after installation

If `dnf` can't find packages from RPM Fusion, the repository metadata may not have loaded correctly. Try reinstalling the repositories and refreshing:

```bash
sudo dnf group upgrade core
sudo dnf clean all
sudo dnf makecache
```

### Hardware video acceleration not working

Verify VA-API is available for your GPU:

```bash
 vainfo
```

If this returns an error, your GPU driver may not support VA-API, or you may need additional driver packages (e.g., `mesa-va-drivers` for AMD/Intel, or `libva-nvidia-driver` for NVIDIA).

---

## Useful Resources

- **Fedora Project**: https://fedoraproject.org/
- **Flathub**: https://flathub.com
- **RPM Fusion**: https://rpmfusion.org/
- **GNOME Extensions**: https://extensions.gnome.org/
- **Learn Linux TV**: https://www.youtube.com/watch?v=GoCPO_If7kY
- **Fedora Post-Install Guide (GitHub)**: https://github.com/devangshekhawat/Fedora-Post-Install-Guide
- **Fedora 42 Post-Install (YouTube)**: https://www.youtube.com/watch?v=nXUbnfMz65w