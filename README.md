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

## Agents

Pulsaride drives the coding agent you already use. Heron does not own or store your provider credentials: each agent signs in with its own method, and runs confined (project files only, network limited to what you approve).

Open the **Agent Hub** (right panel) and click **Connect** on an agent. Pulsaride then:
1. installs it if needed — it shows the official command and runs it in its terminal after you agree;
2. shows what the agent will be allowed to do (files, network) and asks for your approval;
3. runs a short confined test (asks the agent to reply "OK", nothing from your project is sent; it may use a little of your quota).

The agent is **Ready** only if it actually answered. Then pick it in the composer with **Select**.

| Agent | Provider | How Pulsaride runs it |
|---|---|---|
| Claude Code | Anthropic | ACP adapter `claude-agent-acp` |
| Codex | OpenAI | ACP adapter `codex-acp` (ChatGPT sign-in or API key) |
| OpenCode | Multiple providers | native ACP: `opencode acp` |

**Another agent?** Any agent that speaks the [Agent Client Protocol](https://agentclientprotocol.com) works: **+ Add custom ACP agent**, then give its name, executable and arguments (launched directly, never through a shell). It is shown as *Local · Unverified* until you trust it.

**OpenCode and network access:** OpenCode can use several providers, so no domain is allowed in advance. Each provider domain (for example `api.anthropic.com`) is allowed the first time OpenCode needs it, after you approve it.

## Feedback and bugs

Open an [issue](https://github.com/pulsaride/pulsaride/issues) with your distribution, the output of `pulsaride doctor`, and the steps to reproduce.

## License

Copyright © Pulsaride. All rights reserved. The binaries are provided free of charge for evaluation, without warranty. Redistribution and modification are not permitted.
