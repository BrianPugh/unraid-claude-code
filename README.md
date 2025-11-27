# Claude Code Unraid Plugin

Installs [Claude Code](https://github.com/anthropics/claude-code) CLI on Unraid.

## Install

```bash
plugin install https://raw.githubusercontent.com/brianpugh/unraid-claude-code/main/claude-code.plg
```

## Usage

```bash
claude
```

Credentials are automatically saved to your appdata folder via symlink.

## How It Works

- Installs Node.js + Claude Code on boot (RAM-based)
- Symlinks `~/.claude/` to appdata folder on array (default: `/mnt/user/appdata/claude-code/.claude`)
- Configurable via web UI: **Settings → Utilities → Claude Code**

## Requirements

- Unraid 6.12.0+
- Array must be started (for appdata storage)
- Internet connection

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
