# Session Manager for Claude CLI

A Windows app to browse, tag and resume your [Claude Code](https://claude.com/claude-code) CLI sessions: a searchable
session list with tags and filters, descriptions, links between sessions, collections, follow-up dates with a calendar,
and resuming a session in Windows Terminal.

This repository holds the installers only; the source code is kept elsewhere.

## Install

1. Install the **.NET Desktop Runtime 10 (x64)**, if you don't have it yet:

   ```
   winget install Microsoft.DotNet.DesktopRuntime.10
   ```

   or download it from <https://dotnet.microsoft.com/download/dotnet/10.0>. The installer refuses to install without it.

2. Download `SessionManagerForClaudeCli-<version>.msi` from the latest
   [release](https://github.com/TerenceBE/session-manager-for-claude-cli/releases/latest) and run it.

The app installs for all users in `Program Files\Session Manager for Claude CLI`, with a Start menu shortcut. A newer
installer replaces an older version; uninstall it from Windows' Installed apps.

### "Unknown publisher"

The installer is not code signed, so Windows shows "Unknown publisher", and SmartScreen may warn that it protected your
PC (choose "More info", then "Run anyway"). Each release lists the SHA-256 of its installer, so you can check the file:

```
Get-FileHash .\SessionManagerForClaudeCli-<version>.msi
```

### Silent install

```
msiexec /i SessionManagerForClaudeCli-<version>.msi /quiet
```

## Requirements

- Windows 10 or 11, x64
- .NET Desktop Runtime 10 (x64)
- Claude Code CLI (`claude`) on the PATH, and Windows Terminal to resume sessions

## Your data

Your tags, descriptions and settings are kept in `%LOCALAPPDATA%\Session Manager for Claude CLI`, your collection
templates in `%APPDATA%\Session Manager for Claude CLI` (Settings > Data opens both). Installing, upgrading and
uninstalling never touch them. The app reads your Claude sessions from `%USERPROFILE%\.claude\projects` (or
`%CLAUDE_CONFIG_DIR%\projects`) and never changes them.
