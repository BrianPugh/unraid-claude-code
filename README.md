# Claude Code Unraid Plugin

![Claude Code Unraid Plugin](assets/banner.jpg)

Installs [Claude Code](https://github.com/anthropics/claude-code) CLI on Unraid.

## Install

### Graphic Installation

1. Navigate to your Unraid instance's web UI
2. Click the "Plugins" menu item
3. Click the "Install Plugin" tab
4. In the URL field below "Enter URL of remote plugin file or local plugin file", input the URL `https://raw.githubusercontent.com/brianpugh/unraid-claude-code/main/claude-code.plg`
5. Press the "Install" button.

### CLI

In your Unraid terminal window:

```bash
plugin install https://raw.githubusercontent.com/brianpugh/unraid-claude-code/main/claude-code.plg
```

## Usage

Open the Unraid terminal and run:

```bash
claude
```

Authentication and settings persist across reboots automatically. Configure the appdata path via **Settings > Utilities > Claude Code**.

## Requirements

- Unraid 6.12.0+
- Array started, or appdata on an [Unassigned Devices](https://forums.unraid.net/topic/92462-unassigned-devices/) mount
- Internet connection (first install only)

## Troubleshooting

Check the install log:

```bash
cat /var/log/claude-code-install.log
```

Manually re-run the installer:

```bash
/usr/local/emhttp/plugins/claude-code/scripts/install-claude.sh
```

## Development

```bash
# Serve plugin locally
cd /path/to/unraid-claude-code
python3 -m http.server 8080

# On Unraid terminal - install
plugin install http://YOUR_DEV_IP:8080/claude-code.plg

# Reinstall after changes
plugin remove claude-code.plg && plugin install http://YOUR_DEV_IP:8080/claude-code.plg
```

### Releasing

This plugin uses date-based versioning (`YYYY.MM.DD`) per Unraid plugin conventions.

```bash
# Update version to today's date, commit, and tag
bump-my-version replace --new-version 2025.12.01

# Push with tags
git push && git push --tags
```

The release updates version strings in `claude-code.plg` automatically via `.bumpversion.toml`.
