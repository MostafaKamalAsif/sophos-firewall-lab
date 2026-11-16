# Phase 3: DHCP and DNS

## Goal
Let clients receive network settings automatically, like in a real company.

## Findings
- DNS servers on the firewall: 8.8.8.8 (primary), 1.1.1.1 (secondary).
- Only `guestAccess_DHCP` existed, so the LAN had no DHCP server.

## What I did
Created a DHCP server on Port1:

| Setting | Value |
|---|---|
| Name | LAN_DHCP |
| Interface | Port1 |
| IP range | 192.168.50.100 - 192.168.50.200 |
| Subnet mask | 255.255.255.0 |
| Gateway | 192.168.50.2 |
| DNS | 192.168.50.2 |

The range starts at .100 to keep lower addresses free for static devices (servers, printers).

## Result
After switching the client to automatic settings, it received 192.168.50.100 with DNS 192.168.50.2.

## Screenshots
`05-dhcp-server-lan.png`, `06-client-dhcp-ipconfig-all.png`
