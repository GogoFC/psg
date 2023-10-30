# Server Overview - Dell Power Edge R240

### Operating System: 
- [FreeBSD](https://www.freebsd.org/)

### Hypervisor: 
- [bhyve](https://bhyve.org/)





| ZFS pools |  |
|  --  |  --  | 
| `zroot` | OS pool |
| `fantom-pool`  | Backup pool |


| Virtual machines  |   |
|  --  |  --  |
| `nextcloud-psg` | Nextcloud server production VM |
| `guacamole`  | Remote Desktop access |
| `xubuntu`  |  Ubuntu with Desktop Environment |

![drawing](/images/server-overview.png)

