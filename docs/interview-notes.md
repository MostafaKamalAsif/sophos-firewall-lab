# Interview Notes

Short answers based on what I actually did in this project.

**1. What did you build?**
A virtual company network with a Sophos Firewall between a Windows 11 client and the internet. LAN and WAN are separate zones, and the firewall provides DHCP, DNS, NAT and firewall rules.

**2. Why did you use a client VM instead of your own laptop?**
Routing my physical laptop through the firewall would have changed its network settings. A client VM on a host-only network lets me test safely and keeps the real network untouched.

**3. How does the client reach the internet?**
Client to Port1 (LAN), the LAN to WAN firewall rule accepts the traffic, NAT masquerades the client's private IP behind the WAN IP, then traffic leaves through Port2.

**4. What does the Drop all rule do?**
Firewall rules are checked from top to bottom. Traffic that matches no earlier rule is dropped. This is a default-deny design.

**5. Why did your custom rule have to be at the top?**
The default LAN to WAN rule accepts everything. A rule placed below it would never be reached, so a more specific rule must come first.

**6. Why a MAC host and not an IP address?**
The client gets its address from DHCP, so the IP can change and another computer could inherit it. A MAC address identifies the device. The limitation is that a copied VM may get a new MAC and the object needs updating.

**7. How did you troubleshoot the internet problem?**
Layer by layer. The client could reach the firewall, so LAN and DHCP were fine. Pinging 8.8.8.8 needs no DNS and still failed, so DNS was not the cause. The firewall could not reach its WAN gateway either, which pointed to the VMware NAT service. Restarting it fixed the problem.

**8. How did you verify your ICMP rule worked?**
Ping to the internet timed out while browsing and DNS still worked, the rule's traffic counter increased, and the Drop entry appeared in the firewall log.

**9. What would you improve next?**
Add web filtering, application control and IPS, then VPN access, and document each with logs as evidence.
