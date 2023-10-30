# ZFS

## Zpool Status

Check status of ZFS pools by running command `zpool status`.

There are two ZFS pools:
- `fantom-pool`
- `zroot`

![zpool status](/images/zpool-status.png)

ZFS pool named `fantom-pool` is the backup pool made of two USB Fantom Drives `da0` and `da1` in a mirror config.

ZFS pool named `zroot` is the main pool where OS is installed.  The ZFS pool consists of two disk partitions `ada0p2` and `ada1p2` in a ZFS mirror config. 

## Disk partitions.

Pool `zroot` uses partition `2` from each Disk `/dev/ada0` and `/dev/ada1`. 

![zroot partitions](/images/zroot-partitions.png)

