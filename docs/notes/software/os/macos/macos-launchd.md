---
alias: macOS Launch Daemons
---

# macOS launchd

- https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/CreatingLaunchdJobs.html

**Troubleshoot plist**: `plutil -lint ~/Library/LaunchAgents/com.ollama.service.plist`

## Commands

### Find an agent

```shell
sudo find /Library/LaunchAgents /Library/LaunchDaemons /System/Library/LaunchAgents /System/Library/LaunchDaemons -name "*whisperserver*"
```

## Stop

```shell
sudo launchctl stop com.system.whisperserver
```

### Start

```shell
sudo launchctl stop com.system.whisperserver
```

### Status

```shell
sudo launchctl print system/com.system.whisperserver
```
