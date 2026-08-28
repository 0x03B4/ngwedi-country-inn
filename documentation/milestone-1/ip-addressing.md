
# IP Addressing| /27 | 32 | 10.27.0.64 - 10.27.0.95 | 30 |
| Front Desk | /28 | 16 | 10.27.0.96 - 10.27.0.111 | 14 |
| HR / Admin | /28 | 16 | 10.27.0.112 - 10.27.0.127 | 14 |
| Finance | /28 | 16 | 10.27.0.128 - 10.27.0.143 | 14 |
| IT / Management | /28 | 16 | 10.27.0.144 - 10.27.0.159 | 14 |


Subnet sizes were determined using Variable Length Subnet Masking (VLSM) to assign each zone a subnet sized to its estimated device count from section 1.3, rather than a single fixed subnet size for all zones. Subnets were allocated from largest to smallest to ensure that blocks align cleanly without gaps or overlapping address ranges, with each subsequent subnet beginning immediately after the previous one ends.


## Gateway and VLAN Assignment

| Zone | VLAN ID | Network Address | Gateway | Broadcast |
|---|---|---|---|---|
| Guest Wifi | 10 | 10.27.0.0 | 10.27.0.1 | 10.27.0.63 |
| General Staff | 20 | 10.27.0.64 | 10.27.0.65 | 10.27.0.95 |
| Front Desk | 30 | 10.27.0.96 | 10.27.0.97 | 10.27.0.111 |
| HR / Admin | 40 | 10.27.0.112 | 10.27.0.113 | 10.27.0.127 |
| Finance | 50 | 10.27.0.128 | 10.27.0.129 | 10.27.0.143 |
| IT / Management | 60 | 10.27.0.144 | 10.27.0.145 | 10.27.0.159 |

Naming the VLANs in ranges of 10 was chosen as per the industry convention of accommodating future VLANs that might need to be inserted between other VLANs without renaming. VLAN 1 was avoided since it is the default VLAN on Cisco devices and it is used for switch management traffic.


## Address Assignment Method

| Zone | Assignment Method | Reason |
|---|---|---|
| Guest Wifi | DHCP | Varying and non-constant devices, no need to track individual devices. |
| General Staff | DHCP | Non-critical devices, they come and go. |
| Front Desk | Static | Known and critical devices |
| HR / Admin | Static | Known and critical devices |
| Finance | Static | Known and critical devices |
| IT / Management | Static | Known and critical devices |
