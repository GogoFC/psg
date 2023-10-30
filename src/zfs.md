# ZFS

## Zpool Status

Check status of ZFS pools by running command `zpool status`.


![zpool status](/images/zpool-status.png)

ZFS pool named `fantom-pool` is the backup pool made of two USB Fantom Drives `da0` and `da1` in a mirror config.

ZFS pool named `zroot` is the main pool where OS is installed consisting of two internal Disks `ada0` and `ada1` in a mirror config. The ZFS pool consists of disk partitions `ada0p2` and `ada1p2`.

## Disk partitions.

Pool `zroot` uses partition `2` on each Disk. 

![zroot partitions](/images/zroot-partitions.png)

