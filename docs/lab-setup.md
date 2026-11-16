# Lab Setup Guide

How to rebuild this lab. All values below are the ones used in this project.

## 1. VMware virtual networks

Open **Edit > Virtual Network Editor** in VMware Workstation. Do not use **Restore Defaults**, because it resets every virtual network.

| Network | Type | Subnet | Use |
|---|---|---|---|
| VMnet2 | Host-only | 192.168.50.0/24 | Lab LAN |
| VMnet8 | NAT | 192.168.118.0/24 | Internet access |

VMware NAT gateway: 192.168.118.2.

## 2. Sophos Firewall VM

Two network adapters:

| Sophos port | VMware network | Zone |
|---|---|---|
| Port1 | VMnet2 | LAN |
| Port2 | VMnet8 | WAN |

- Port1 static IP: 192.168.50.2/24
- Port2: DHCP from VMware NAT
- Web admin: `https://192.168.50.2:4444` (HTTPS admin access must be allowed on the LAN zone)

## 3. Client VM

- Windows 11 VM with **one** adapter set to **Custom: VMnet2**.
- Network settings: obtain IP and DNS automatically (from `LAN_DHCP`).

## 4. Sophos configuration

1. **DHCP:** create `LAN_DHCP` on Port1, range 192.168.50.100 to 192.168.50.200, gateway and DNS 192.168.50.2.
2. **DNS:** upstream servers 8.8.8.8 and 1.1.1.1.
3. **Firewall and NAT:** default LAN to WAN rule and masquerade NAT rule give internet access.

## 5. Verify

From the client:

```
ipconfig /all
ping 192.168.50.2
ping 8.8.8.8
nslookup google.com
```

If the client reaches the firewall but not the internet, check the WAN gateway status in Sophos (Routing > Gateways) and the VMware NAT Service on the host. See [troubleshooting](troubleshooting/wan-gateway-down.md).
