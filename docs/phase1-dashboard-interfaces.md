# Phase 1: Dashboard and Interface Verification

## Goal
Understand the Sophos Control Center and confirm the interface configuration before changing anything.

## What I did
- Logged in to the web admin at `https://192.168.50.2:4444`.
- Reviewed the Control Center: system health (CPU, memory, uptime), firewall health check, traffic insight and threat response widgets.
- Opened Configure > Network > Interfaces to verify zones and IP addresses.

## Result

| Interface | Zone | IP address | Type | Status |
|---|---|---|---|---|
| Port1 | LAN | 192.168.50.2/24 | Static | Connected, 1000 Mbps Full Duplex |
| Port2 | WAN | 192.168.118.130/24 | DHCP | Connected, 1000 Mbps Full Duplex |
| GuestAP | WiFi | 10.255.0.1/24 | Static | Unplugged (default, not used in this lab) |

## What I learned
- The dashboard shows health at a glance, but IP details live under Network > Interfaces.
- The browser shows "Not secure" because the firewall uses a self-signed certificate.
- Always verify the current state before changing a firewall.
- The firmware on the dashboard (SFOS 22.0.3 MR-3) was newer than my notes, so I updated my documentation.

## Screenshots
`01-control-center.png`, `02-interfaces.png`
