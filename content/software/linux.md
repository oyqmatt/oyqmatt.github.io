---
title: "Linux"
date: 2023-06-10T02:00:03+08:00
weight: 1
---

## Permissions

#### Sometimes run into permission issues, e.g. insufficient permissions for /dev/tty*

```bash
# Check current groups
groups
```
```bash
# Add current user to dialout
sudo usermod -aG dialout $USER #restart after
```

#### Set file permissions

```bash
# Make file excutable
sudo chmod +x <file>
```

***

## Common CLI
```bash
route -n
```

***

## Bash scripting

#### Bash header
```bash
#!/bin/bash
```

