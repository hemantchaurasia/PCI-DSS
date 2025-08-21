# PCI-DSS

## How to define the correct scope for a penetration test on network segmentations in a PCI DSS environment?

PCI DSS Guidance

Requirement 11.4.5 (PCI DSS v4.0): You must perform segmentation penetration testing at least every 12 months and after any changes to segmentation controls.

The objective: prove that non-CDE systems cannot access the CDE through the network segmentation controls you’ve implemented.

🛠 Steps to Define Scope
1. Identify the CDE

Document all systems and networks where cardholder data is stored, processed, or transmitted.

Include connected systems providing security services (e.g., authentication, logging, monitoring).

2. Identify Connected Networks

Map all in-scope and out-of-scope segments:

CDE VLANs / subnets

Management networks

Corporate IT networks (e.g., office LAN, Wi-Fi)

DMZs, third-party connections, and remote access entry points

3. Define Segmentation Controls

Firewalls, routers, ACLs, SDN rules, microsegmentation policies

Jump servers, bastion hosts, and VPN concentrators

Any network isolation technology used to enforce segmentation

4. Determine Test Points

Choose representative systems from each non-CDE segment that has any path toward the CDE.

Include:

Adjacent subnets (closest to CDE, highest risk)

Remote subnets (e.g., corporate, wireless, vendor, cloud)

Management networks (often overlooked but high risk)

5. Define Attack Paths

Pen testers should attempt to:

Bypass firewalls/ACLs to reach CDE hosts

Exploit weak services on border systems

Pivot laterally (multi-hop attacks from out-of-scope → CDE)

Test allowed ports (e.g., if DNS, RDP, SSH, SNMP are allowed, ensure they are restricted/secured)

6. Confirm Effectiveness

Success = No unauthorized access from out-of-scope to CDE.

Evidence = Documented test results showing blocked access attempts.

Eexample:

“The segmentation penetration test will assess the effectiveness of firewalls, ACLs, and VLAN configurations preventing unauthorized access from non-CDE networks (corporate LAN, wireless, vendor VPN, management VLANs, and DMZ) into the CDE. Representative hosts will be selected from each out-of-scope segment to simulate attacks, and testing will include direct and indirect access attempts, lateral movement, and service-specific bypass techniques.”

Note: 
1. Keep the scope broad enough to cover all non-CDE segments with potential connectivity, but targeted enough to be testable (you don’t need to test every host, just representative ones).
