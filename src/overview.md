# Server Overview - Dell Power Edge R240


Operating System: FreeBSD

ZFS pools: 

- `zroot` - OS pool
- `fantom-pool` - backup pool

Hypervisor: bhyve

Virtual machines:

- `nextcloud-psg` - Nextcloud server production VM
- `guacamole` - Remote desktop access
- `xubuntu` - Ubuntu with Desktop Environment

```sh
➜  ~ sudo vm list
NAME             DATASTORE  LOADER  CPU  MEMORY  VNC           AUTO     STATE
guacamole        default    uefi    2    4G      0.0.0.0:5901  Yes [2]  Running (1637)
nextcloud-psg    default    uefi    2    16G     0.0.0.0:5900  Yes [1]  Running (63958)
ubuntu-template  default    uefi    2    4G      -             No       Stopped
xubuntu          default    uefi    2    8G      0.0.0.0:5903  Yes [4]  Running (86966)
keep-awake       fantom     uefi    1    2G      0.0.0.0:5902  Yes [3]  Running (1943)
seafile          fantom     uefi    2    8G      -             No       Stopped
➜  ~ 
```

![drawing](/images/server-overview.png)


