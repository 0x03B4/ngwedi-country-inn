
# Design Revisions

During implementation, three aspects of the original Milestone 1 design required adjustment, two due to limitations discovered in Cisco Packet Tracer, and one due to a gap identified through testing.

## 1. EtherChannel Placement

The Cisco 2911 router's native GigabitEthernet interfaces do not support the `channel-group` command required to form an EtherChannel. The command was rejected with `% Invalid input detected` when applied to the router's physical interface, despite the same command working correctly on a 2960 switch. This is a genuine platform limitation, since lower-end router platforms without dedicated switch modules do not support EtherChannel on their native interfaces, on both real hardware and in Packet Tracer.

The original design (Milestone 1, Section 3.2) placed EtherChannel on the link between the switch and the router. Since the router cannot participate in an EtherChannel bundle, the design was revised to include a second switch. EtherChannel is now implemented between the two switches, the Core Switch and the Access Switch, while the router continues to perform inter-VLAN routing via router-on-a-stick, connected to the Core Switch through a single trunk link.

The switch-to-switch link remains the busiest point in the network, as all end-device traffic for every VLAN must pass through it en route to the router. Bundling this link with EtherChannel still provides the same intended benefits, increased bandwidth and redundancy against a single cable failure, just relocated to a link capable of supporting it.

## 2. Access Point SSID Configuration

The original design specified a single access point per cluster, each broadcasting two SSIDs, one per VLAN, to minimise hardware while maintaining VLAN separation. However, the access point models available in Packet Tracer (AP-PT, AP-PT-A, AP-PT-AC, AP-PT-N) only support a single SSID per device.

Each of the two access points was assigned to a single VLAN instead, one dedicated to Guest Wifi (VLAN 10) and one dedicated to General Staff (VLAN 20). This preserves the original two-AP physical design and coverage reasoning of one AP per cluster, with the only change being that dual-SSID broadcasting was not achievable within Packet Tracer's available device capabilities.

## 3. IT / Management Access Clarification

Milestone 1 established that IT/Management has administrative access to all VLANs, but did not specify whether other zones could initiate contact with IT in return. This was tested directly during implementation, which also surfaced two related issues worth documenting.

The first issue was a typo in the Guest and General Staff access control lists, where the destination wildcard mask did not correctly cover the full internal address range, allowing General Staff to reach IT when it should have been blocked. This was identified through full connectivity testing and corrected by rebuilding the affected access control lists with the correct destination range.

The second issue was a behavioural detail of access control lists rather than an error: since access control lists are stateless, a reply to a ping is treated as a new, separate packet rather than part of the original request. This meant that although IT could send a request to Guest Wifi or General Staff, the reply from those zones was itself blocked by their own access control list, causing the ping to fail even though IT's access was never explicitly restricted.

Having confirmed this, a decision was made to clarify IT's access in both directions. Front Desk and HR, as trusted internal staff functions, are permitted to reach IT directly, for example to request support, while Guest Wifi and General Staff, being untrusted or non-critical zones, remain fully blocked from reaching IT, consistent with their isolation from all other internal zones. The Front Desk and HR access control lists were updated accordingly, explicitly denying only their restricted peer zones rather than denying all internal traffic, allowing IT to remain reachable.

This means Milestone 1's statement that IT has administrative access to all VLANs does not fully hold for Guest Wifi and General Staff specifically. While IT's own interface has no restrictions and can send traffic to any zone, pings from IT to Guest Wifi and General Staff fail, because the reply from those zones is blocked by their own access control lists before it can return to IT. Permitting this traffic to allow IT's replies through would, by necessity, also permit Guest Wifi and General Staff to initiate contact with IT directly, undermining the isolation that is central to their design. Resolving this properly would require reflexive or stateful access control lists, which track the state of a connection and only permit replies to traffic that was genuinely initiated from the trusted side.

Given this trade-off, isolation was prioritised over full administrative reachability for these two zones specifically. IT/Management retains full access to Front Desk, HR, and Finance, as these are trusted internal zones. Guest Wifi and General Staff remain fully isolated, including from IT, since allowing IT to reach them would require loosening the same rule that keeps them isolated from every other zone. In practice, management of the two access points serving these zones can still be performed through their own local configuration interface, without relying on network-level access from IT's VLAN.