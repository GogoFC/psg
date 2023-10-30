# Server Overview - Dell Power Edge R240

### : 
- 
| Operating System  | FreeBSD |

### ZFS pools: 
- `zroot` - OS pool
- `fantom-pool` - backup pool

### Hypervisor: 
- bhyve



![drawing](/images/server-overview.png)



| Virtual machines |    |
|  --  |  --  |
| `nextcloud-psg` | Nextcloud server production VM |
| `guacamole`  | Remote Desktop access |
| `xubuntu`  |  Ubuntu with Desktop Environment |
