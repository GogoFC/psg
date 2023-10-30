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

Pool `zroot` uses partition number `2` from each of the `/dev/ada0` and `/dev/ada1` Disks. 

![zroot partitions](/images/zroot-partitions.png)

zfs quota 


## Datasets

`zfs list` will list all ZFS Datasets.

```sh
➜  ~ zfs list
NAME                                           USED  AVAIL     REFER  MOUNTPOINT
fantom-pool                                   1.37T  3.96T       96K  /fantom-pool
fantom-pool/backups                           1.36T  3.96T      104K  /fantom-pool/backups
fantom-pool/backups/guacamole                 3.52G  3.96T      104K  /fantom-pool/backups/guacamole
fantom-pool/backups/guacamole/disk0           3.52G  3.96T     3.52G  -
fantom-pool/backups/nextcloud-psg             1.35T  3.96T      112K  /fantom-pool/backups/nextcloud-psg
fantom-pool/backups/nextcloud-psg/disk0       1.35T  3.96T     1.35T  -
fantom-pool/backups/xubuntu                   8.86G  3.96T      112K  /fantom-pool/backups/xubuntu
fantom-pool/backups/xubuntu/disk0             8.86G  3.96T     8.86G  -
fantom-pool/vm                                7.63G  3.96T      104K  /fantom-pool/vm
fantom-pool/vm/keep-awake                     2.42G  3.96T      112K  /fantom-pool/vm/keep-awake
fantom-pool/vm/keep-awake/disk0               2.42G  3.96T     2.42G  -
fantom-pool/vm/seafile                        5.20G  3.96T      112K  /fantom-pool/vm/seafile
fantom-pool/vm/seafile/disk0                  5.20G  3.96T     5.20G  -
zroot                                         1.59T  1.92T       96K  /zroot
zroot/ROOT                                    2.60G  1.92T       96K  none
zroot/ROOT/13.2-RELEASE-p1_2023-09-17_100242     8K  1.92T     2.00G  /
zroot/ROOT/13.2-RELEASE_2023-06-30_142817        8K  1.92T     1.85G  /
zroot/ROOT/default                            2.60G  1.92T     2.02G  /
zroot/ROOT/fresh                                 8K  1.92T     1.68G  /
zroot/ROOT/upgraded                              8K  1.92T     1.89G  /
zroot/ROOT/upgrading-os                          8K  1.92T     1.74G  /
zroot/tmp                                      172K  1.92T      172K  /tmp
zroot/usr                                      201M  1.92T       96K  /usr
zroot/usr/home                                 201M  1.92T      201M  /usr/home
zroot/usr/ports                                 96K  1.92T       96K  /usr/ports
zroot/usr/src                                   96K  1.92T       96K  /usr/src
zroot/var                                     10.8M  1.92T       96K  /var
zroot/var/audit                                 96K  1.92T       96K  /var/audit
zroot/var/crash                                 96K  1.92T       96K  /var/crash
zroot/var/log                                 1.44M  1.92T     1.44M  /var/log
zroot/var/mail                                9.04M  1.92T     9.04M  /var/mail
zroot/var/tmp                                   96K  1.92T       96K  /var/tmp
zroot/vm                                      1.58T  1.92T     14.4G  /zroot/vm
zroot/vm/guacamole                            4.97G  1.92T      120K  /zroot/vm/guacamole
zroot/vm/guacamole/disk0                      4.97G  1.92T     3.31G  -
zroot/vm/nextcloud-psg                        1.55T  1.92T      120K  /zroot/vm/nextcloud-psg
zroot/vm/nextcloud-psg/disk0                  1.55T  1.92T     1.42T  -
zroot/vm/ubuntu-template                      5.03G  1.92T      104K  /zroot/vm/ubuntu-template
zroot/vm/ubuntu-template/disk0                5.03G  1.92T     5.03G  -
zroot/vm/xubuntu                              14.0G  1.92T      120K  /zroot/vm/xubuntu
zroot/vm/xubuntu/disk0                        14.0G  1.92T     9.69G  -
➜  ~ 
```

## Virtual Machine Datasets

Dataset for VM's is `zroot/vm` mounted on `/zroot/vm`.

Each VM has two datasets. One for VM config files and one for the Disk.

List of all VM's datasets:

```sh
➜  ~ zfs list -r zroot/vm
NAME                             USED  AVAIL     REFER  MOUNTPOINT
zroot/vm                        1.59T  1.92T     14.4G  /zroot/vm
zroot/vm/guacamole              4.97G  1.92T      120K  /zroot/vm/guacamole
zroot/vm/guacamole/disk0        4.97G  1.92T     3.31G  -
zroot/vm/nextcloud-psg          1.55T  1.92T      120K  /zroot/vm/nextcloud-psg
zroot/vm/nextcloud-psg/disk0    1.55T  1.92T     1.42T  -
zroot/vm/ubuntu-template        5.03G  1.92T      104K  /zroot/vm/ubuntu-template
zroot/vm/ubuntu-template/disk0  5.03G  1.92T     5.03G  -
zroot/vm/xubuntu                14.0G  1.92T      120K  /zroot/vm/xubuntu
zroot/vm/xubuntu/disk0          14.0G  1.92T     9.69G  -
➜  ~ 
```
Another dataset for VM's is `fantom-pool/vm` but it is not used for production.
It only has one VM running for keeping the USB Disks awake.

```sh
➜  ~ zfs list -r fantom-pool/vm
NAME                              USED  AVAIL     REFER  MOUNTPOINT
fantom-pool/vm                   7.63G  3.96T      104K  /fantom-pool/vm
fantom-pool/vm/keep-awake        2.42G  3.96T      112K  /fantom-pool/vm/keep-awake
fantom-pool/vm/keep-awake/disk0  2.42G  3.96T     2.42G  -
fantom-pool/vm/seafile           5.20G  3.96T      112K  /fantom-pool/vm/seafile
fantom-pool/vm/seafile/disk0     5.20G  3.96T     5.20G  -
➜  ~ 
```