# Assigning-ports-and-creating-VLANS
### Introduction
Existing network address = 192.168.45.0 /24

Departments and the number of hosts (in descending order):
- PRODUCTION - 80 hosts
- IT - 50 hosts
- MARKETING - 40 hosts
- ACCOUNTING - 25 hosts
- HR - 15 hosts

### Assigning network addresses for each department
### 1 PRODUCTION - needs 80 hosts
- Usable hosts = 2⁷ – 2 = 128 – 2 = 126 usable hosts
- Network address: 192.168.45.0/25
- IP range: 192.168.45.0 – 192.168.45.127
- Usable hosts: 192.168.45.1 – 192.168.45.126
- Broadcast address: 192.168.45.127

### 2 IT - needs 50 hosts
- Usable hosts = 2⁶ – 2 = 64 – 2 = 62 usable hosts
- Next available: 192.168.45.128/26
- IP range: 192.168.45.128 – 192.168.45.191
- Usable hosts: 192.168.45.129 – 192.168.45.190
- Broadcast: 192.168.45.191

### 3 MARKETING - needs 40 hosts
- Usable hosts = 2⁶ – 2 = 62 usable hosts
- Next available: 192.168.45.192/26
- IP range: 192.168.45.192 – 192.168.45.255
- Usable hosts: 192.168.45.193 – 192.168.45.254
- Broadcast: 192.168.45.255

We cannot fit Accounting and HR which need two /27 blocks in 192.168.45.0/24 because it’s already consumed. Therefore, we would need an additional network (another /24) for Accounting and HR.

### 4 ACCOUNTING - needs 25 hosts
- Usable hosts = 2⁵ – 2 = 32 – 2 = 30 usable hosts
- Network: 192.168.46.0/27
- Range: 192.168.46.0 – 192.168.46.31
- Usable hosts: 192.168.46.1 – 192.168.46.30
- Broadcast: 192.168.46.31

### 5 HR - needs 15 hosts
- Usable hosts = 2⁵ – 2 = 30 usable hosts
- Network: 192.168.46.32/27
- Range: 192.168.46.32 – 192.168.46.63
- Usable hosts: 192.168.46.33 – 192.168.46.62
- Broadcast: 192.168.46.63

## Subnet Allocation Table

| Department  | VLAN Name   | VLAN No. | Required Hosts | Network Address | CIDR | Subnet Mask       |
|-------------|-------------|----------|----------------|-----------------|------|-------------------|
| Production  | VLAN_10     | 10       | 80             | 192.168.45.0    | /25  | 255.255.255.128   |
| IT          | VLAN_20     | 20       | 50             | 192.168.45.128  | /26  | 255.255.255.192   |
| Marketing   | VLAN_30     | 30       | 40             | 192.168.45.192  | /26  | 255.255.255.192   |
| Accounting  | VLAN_40     | 40       | 25             | 192.168.46.0    | /27  | 255.255.255.224   |
| HR          | VLAN_50     | 50       | 15             | 192.168.46.32   | /27  | 255.255.255.224   |


