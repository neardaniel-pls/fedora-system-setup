# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## [1.1.0] - 2026-06-12

### Changed
- Updated version references from Fedora 42+ to Fedora 44+
- Fixed RPM Fusion URL to use mirrors.rpmfusion.org (consistent across all docs)
- Standardized multimedia codec installation with `groupupdate` commands
- Standardized group commands to use `groupupdate` consistently
- Updated GNOME version references to GNOME 50
- Updated DNF slow performance FAQ tip for DNF5 (`max_parallel_downloads` instead of deprecated `fastestmirror`)
- Updated license copyright year to 2025-2026
- Updated bug report template environment examples for Fedora 44

### Added
- Quick Commands section at the top of the main setup guide for experienced users

### Removed
- Merged `docs/guides/fedora-setup-guide.md` into main setup guide (eliminated conflicting commands)

## [1.0.0] - 2026-05-25

### Added
- Comprehensive Fedora post-installation guide
- System updates and package management
- Flatpak/Flathub setup
- RPM Fusion repository configuration (free and non-free)
- Multimedia codec installation
- FFmpeg and hardware video acceleration
- GNOME Extensions and Tweaks setup
- System customization (display, sound, power, appearance)
