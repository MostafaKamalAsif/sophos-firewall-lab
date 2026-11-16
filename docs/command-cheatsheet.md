# Command and Menu Cheat Sheet

## Windows client (Command Prompt)

| Command | Purpose |
|---|---|
| `ipconfig /all` | Show IP, gateway, DNS, MAC address |
| `ipconfig /release` then `ipconfig /renew` | Request new DHCP settings |
| `ping 192.168.50.2` | Test client to firewall |
| `ping 8.8.8.8` | Test internet without DNS |
| `nslookup google.com` | Test DNS |

## Sophos web admin paths

| Task | Path |
|---|---|
| Dashboard | Monitor & analyze > Control center |
| Interfaces and zones | Configure > Network > Interfaces |
| DNS / DHCP | Configure > Network > DNS / DHCP |
| Gateways | Configure > Routing > Gateways |
| Firewall and NAT rules | Protect > Rules and policies |
| Host objects | System > Hosts and services |
| Service status | Configure > System services > Services |
| Ping and lookup tools | Monitor & analyze > Diagnostics > Tools |
| Logs | Log viewer (top right) |

## Windows host

| Action | How |
|---|---|
| Restart VMware NAT/DHCP service | `Win + R`, `services.msc`, right-click the service, Restart |
