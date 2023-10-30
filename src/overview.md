# Server Overview - Dell Power Edge R240

### Operating System: 
- [FreeBSD](https://www.freebsd.org/)

### Hypervisor: 
- [bhyve](https://bhyve.org/)



| ZFS pools |  |
|  --  |  --  | 
| `zroot` | OS pool |
| `fantom-pool`  | Backup pool |


![drawing](/images/server-overview.png)





| Virtual machines  |   |
|  --  |  --  |
| `nextcloud-psg` | Nextcloud Server production VM |
| `guacamole`  | [Apache Guacamole](https://guacamole.apache.org/) Remote Desktop access |
| `xubuntu`  |  Ubuntu with Desktop Environment |

