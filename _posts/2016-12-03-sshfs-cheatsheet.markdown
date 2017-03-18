---
layout: post
title: Sshfs cheatsheet
subtitle: ""
tags: sshfs tips
---

Mount a remote directory:
```bash
sshfs login@machine:/path/to/source/code /path/to/mountpoint
```

Unmount:
```bash
fusermount -u /path/to/mountpoint/
```

Force unmount (sudo or as root)
```bash
umount -l /path/to/mountpoint
```
