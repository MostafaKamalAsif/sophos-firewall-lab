# Phase 2: Windows 11 Client VM

## Goal
Add a client machine that behaves like an employee computer behind the firewall.

## What I did
- Set the client VM network adapter to **Custom: VMnet2** only (no NAT or bridged adapter), so all traffic must pass through Sophos.
- Configured a temporary static IP: 192.168.50.10/24, gateway 192.168.50.2, DNS 192.168.50.2.
- Verified with `ipconfig` and `ping 192.168.50.2`.

## Result
The client can reach the firewall LAN interface.

## Screenshots
`03-vmware-adapter-vmnet2.png`, `04-client-ipconfig-ping.png`
