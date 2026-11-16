# Network Diagram

Save the lab diagram here as `lab-topology.png` (draw.io, Visio or Paint) and copy it to `screenshots/00-network-diagram.png`.

```
Windows 11 Client VM  (DHCP: 192.168.50.100-200)
          |
       VMnet2 (host-only)
          |
Sophos Port1  - LAN - 192.168.50.2/24 (static)
Sophos Port2  - WAN - 192.168.118.x/24 (DHCP from VMware NAT)
          |
       VMnet8 (NAT, gateway 192.168.118.2)
          |
       Internet
```
