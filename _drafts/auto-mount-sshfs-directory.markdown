---
title: "Mounting automatically an ssh directory"
subtitle: "Leveraging AutoFS and sshFS"
tags: sshfs
---

sshfs autofs 

```/etc/auto.master```

```
/media/net   /etc/auto.sshfs  uid=1000,gid=1000,--timeout=30,--ghost
```


```/etc/auto.sshfs```

```
Musique -fstype=fuse,rw,nodev,nonempty,allow_other,reconnect,uid=1000,gid=1000,max_read=65536,compression=yes,auto_cache,no_check_root,kernel_cache :sshfs\#root@kodi\:/var/media/sdcl1-ata-WDC_WD10EADS-11M/Musique
```
