# Phase 4: Firewall Rules and NAT

## Goal
Understand which rules give clients internet access, then create and test a custom rule.

## Default firewall rules

| # | Rule | Source to Destination | Action |
|---|---|---|---|
| 1 | Auto added firewall policy for MTA | Any to Any (SMTP) | Accept |
| 2 | #Default_Network_Policy | LAN to WAN, any service | Accept |
| 3 | Drop all | Any to Any | Drop |

Rules are matched from top to bottom. Traffic that matches nothing is dropped by the last rule (default deny).

## NAT
`#NAT_Default_Network_Policy` (linked to firewall rule 2) masquerades client traffic behind the WAN IP. It showed hundreds of hits after the client started browsing.

## Custom rule: block ICMP from one client
1. Created a MAC host object `Client-PC1-MAC`. A MAC-based object is used instead of an IP because the client gets its address from DHCP and the IP can change.
2. Created firewall rule `Block_ICMP_Client-PC1`:

| Setting | Value |
|---|---|
| Action | Drop |
| Position | Top |
| Source | LAN, Client-PC1-MAC |
| Destination | WAN, any |
| Service | ICMP |
| Logging | Enabled |

The rule must sit above the default LAN to WAN accept rule, otherwise traffic is accepted before it is evaluated.

## Test result

| Test | Result |
|---|---|
| ping 8.8.8.8 | Blocked (timed out) |
| ping 192.168.50.2 | Works |
| Browsing and DNS | Work |

The Drop entry was confirmed in the firewall log.

## Screenshots
`10-firewall-rules.png`, `11-nat-rules.png`, `12-system-services.png`, `13-custom-rule-icmp.png`, `14-ping-blocked.png`, `15-firewall-log-drop.png`
