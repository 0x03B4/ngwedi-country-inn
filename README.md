This repository contains the network design, packet tracer simulation and technical documentation
for an organization called Ngwedi Country Inn, based in Kimberley.

Project ID: CMPG325-2026-056<br>
Client ID: CLI-056<br>
Industry: Hospitality<br>

## Project documentation

#### Milestone 1
- [Client Requirements](documentation/milestone-1/client-requirements.md)
- [IP Addressing](documentation/milestone-1/ip-addressing.md)
- [Physical Topology](documentation/milestone-1/physical-topology.md)
- [Logical Topology](documentation/milestone-1/logical-topology.md)
- Diagrams:
- [Physical Topology Diagram](topologies/physical_topology.png)
- [Logical Topology Diagram](topologies/logical_topology.png)

#### Milestone 2
- [Design Revisions](documentation/milestone-2/design-revision.md)
- [Implementation Summary](documentation/milestone-2/implementation.md)
- [Testing Evidence](documentation/milestone-2/testing.md)
- Diagrams:
- [Revised Physical Topology Diagram](topologies/physical_topology_revised.png)
- [Revised Logical Topology Diagram](topologies/logical_topology_revised.png)
- [Packet Tracer File](packet_tracer/ngwedi-country-inn.pkt)
- Screenshots:
- Network Configuration
- [VLAN Assignment](screenshots/milestone-2/vlan-brief.png)
- [EtherChannel Status](screenshots/milestone-2/etherchannel-summary.png)
- [Router Sub-interfaces](screenshots/milestone-2/router-subinterfaces.png)
- [Access Control Lists](screenshots/milestone-2/access-lists.png)
- [DHCP - Guest Wifi](screenshots/milestone-2/dhcp-guest.png)
- [DHCP - General Staff](screenshots/milestone-2/dhcp-staff.png)
- [Full Topology Build](screenshots/milestone-2/topology-overview.png)
- Connectivity Testing
- [Ping Test - Guest Wifi](screenshots/ping-tests/guest.png)
- [Ping Test - General Staff](screenshots/ping-tests/general-staff.png)
- [Ping Test - Front Desk](screenshots/ping-tests/front-desk.png)
- [Ping Test - HR / Admin](screenshots/ping-tests/hr-admin.png)
- [Ping Test - Finance](screenshots/ping-tests/finance.png)
- [Ping Test - IT / Management](screenshots/ping-tests/it-management.png)

#### Final Submission
- [Additional Testing](documentation/final-submission/additional-testing.md)
- Screenshots:
  - Network Isolation & Security:
    - [Access Control Lists After Isolation Tests](screenshots/final-submission/access-lists-after-isolation-tests.png)
    - [Ping Test - Front Desk to Guest Wifi and General Staff](screenshots/final-submission/front-desk-to-guest-staff.png)
    - [Ping Test - HR / Admin to Guest Wifi and General Staff](screenshots/final-submission/hr-to-guest-staff.png)
    - [Ping Test - Finance to Guest Wifi and General Staff](screenshots/final-submission/finance-to-guest-staff.png)
  - DNS Resolution:
    - [DNS Service Configuration](screenshots/final-submission/dns-service.png)
    - [DNS Resolution Test](screenshots/final-submission/dns-resolution.png)
  - NAT Verification:
    - [NAT Configuration](screenshots/final-submission/nat-config.png)
    - [NAT Verification Test](screenshots/final-submission/nat-verification.png)
  - EtherChannel Redundancy & Failover:
    - [EtherChannel Failover - Link Down](screenshots/final-submission/etherchannel-failover-down.png)
    - [EtherChannel Failover - Link Restored](screenshots/final-submission/etherchannel-failover-restored.png)

<br>
<br>

[Physical and Logical Topology Source (.drawio)](topologies/Physical-and-Logical-Topologies.drawio)