# Troubleshooting: No Internet from the Client

## Symptom
The client could ping the firewall (192.168.50.2) but not 8.8.8.8, and `nslookup google.com` timed out.

## Diagnosis (layer by layer)

| Step | Test | Result | Conclusion |
|---|---|---|---|
| 1 | Client ping 192.168.50.2 | Success | LAN and client config are fine |
| 2 | Client ping 8.8.8.8 | Failed | Problem is beyond the LAN (DNS is not involved in this test) |
| 3 | Firewall ping 8.8.8.8 (Diagnostics > Tools) | Failed | The firewall itself has no internet |
| 4 | Firewall ping 192.168.118.2 | Failed | WAN gateway unreachable |
| 5 | Routing > Gateways | Status red | Confirms the gateway is down |

## Root cause
The VMware NAT service on the host was not passing traffic, even though it showed as Running.

## Fix
Restarted **VMware NAT Service** and **VMware DHCP Service** in the host's `services.msc`. The gateway turned green and the client regained internet access.

## Lesson
Test one layer at a time (client, firewall, gateway, internet) to find where the path breaks. A service showing "Running" does not guarantee it works.

## Screenshots
`07-client-failed-ping.png`, `09-gateway-green.png`
