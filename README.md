# Pulsaride

A task-centred IDE for working with coding agents you can trust: agents run confined (no network, isolated files), every change comes back as a reviewable diff with verifiable proof.

**Preview release — Linux x86-64 only.** Windows and macOS builds are not available yet.

## Download

| Format | Link |
|---|---|
| Debian / Ubuntu package | [pulsaride-linux-amd64.deb](https://github.com/pulsaride/pulsaride/releases/latest/download/pulsaride-linux-amd64.deb) |
| AppImage (single file) | [Pulsaride-linux-x86_64.AppImage](https://github.com/pulsaride/pulsaride/releases/latest/download/Pulsaride-linux-x86_64.AppImage) |
| Archive (no admin rights) | [pulsaride-linux-x86_64.tar.gz](https://github.com/pulsaride/pulsaride/releases/latest/download/pulsaride-linux-x86_64.tar.gz) |
| Checksums | [SHA256SUMS](https://github.com/pulsaride/pulsaride/releases/latest/download/SHA256SUMS) |

All versions: [Releases](https://github.com/pulsaride/pulsaride/releases).

## Requirements

- Linux x86-64 with **glibc 2.39 or newer** (Ubuntu 24.04 or equivalent).
- `git` and `bubblewrap` (agent confinement; the `.deb` installs it, otherwise `sudo apt install bubblewrap`).
- X11 libraries: libx11, libx11-xcb, libxcursor, libxi, libxcb, libxkbcommon-x11.
- To delegate tasks to an agent: [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and signed in with your own account.

## Install

Verify the download first: `sha256sum -c SHA256SUMS --ignore-missing`

**Debian / Ubuntu**

    sudo apt install ./pulsaride-linux-amd64.deb

**AppImage**

    chmod +x Pulsaride-linux-x86_64.AppImage
    ./Pulsaride-linux-x86_64.AppImage --repo /path/to/your/project

Without FUSE: `APPIMAGE_EXTRACT_AND_RUN=1 ./Pulsaride-linux-x86_64.AppImage`

**Archive (installs into ~/.local)**

    tar xzf pulsaride-linux-x86_64.tar.gz
    cd pulsaride-*-x86_64-linux
    ./install.sh        # ./uninstall.sh to remove (your data is kept)

Then check your setup: `pulsaride doctor`

## Feedback and bugs

Open an [issue](https://github.com/pulsaride/pulsaride/issues) with your distribution, the output of `pulsaride doctor`, and the steps to reproduce.

## License

Copyright © Pulsaride. All rights reserved. The binaries are provided free of charge for evaluation, without warranty. Redistribution and modification are not permitted.
