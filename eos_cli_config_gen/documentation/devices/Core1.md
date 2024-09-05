# Core1

## Table of Contents

- [Interfaces](#interfaces)
  - [Ethernet Interfaces](#ethernet-interfaces)
  - [Loopback Interfaces](#loopback-interfaces)
- [Routing](#routing)
  - [IP Routing](#ip-routing)
  - [Router OSPF](#router-ospf)

## Interfaces

### Ethernet Interfaces

#### Ethernet Interfaces Summary

##### L2

| Interface | Description | Mode | VLANs | Native VLAN | Trunk Group | Channel-Group |
| --------- | ----------- | ---- | ----- | ----------- | ----------- | ------------- |

*Inherited from Port-Channel Interface

##### IPv4

| Interface | Description | Type | Channel Group | IP Address | VRF |  MTU | Shutdown | ACL In | ACL Out |
| --------- | ----------- | -----| ------------- | ---------- | ----| ---- | -------- | ------ | ------- |
| Ethernet1 | - | routed | - | 10.220.0.1/30 | default | 1500 | - | - | - |
| Ethernet2 | - | routed | - | 10.220.0.5/30 | default | 1500 | - | - | - |
| Ethernet3 | - | routed | - | 10.220.0.9/30 | default | 1500 | - | - | - |

#### Ethernet Interfaces Device Configuration

```eos
!
interface Ethernet1
   mtu 1500
   no switchport
   ip address 10.220.0.1/30
   ip ospf network point-to-point
   ip ospf area 0
!
interface Ethernet2
   mtu 1500
   no switchport
   ip address 10.220.0.5/30
   ip ospf network point-to-point
   ip ospf area 0
!
interface Ethernet3
   mtu 1500
   no switchport
   ip address 10.220.0.9/30
   ip ospf network point-to-point
   ip ospf area 0
```

### Loopback Interfaces

#### Loopback Interfaces Summary

##### IPv4

| Interface | Description | VRF | IP Address |
| --------- | ----------- | --- | ---------- |
| Loopback0 | - | default | 11.11.11.11/32 |

##### IPv6

| Interface | Description | VRF | IPv6 Address |
| --------- | ----------- | --- | ------------ |
| Loopback0 | - | default | - |

#### Loopback Interfaces Device Configuration

```eos
!
interface Loopback0
   ip address 11.11.11.11/32
```

## Routing

### IP Routing

#### IP Routing Summary

| VRF | Routing Enabled |
| --- | --------------- |
| default | True |

#### IP Routing Device Configuration

```eos
!
ip routing
```

### Router OSPF

#### Router OSPF Summary

| Process ID | Router ID | Default Passive Interface | No Passive Interface | BFD | Max LSA | Default Information Originate | Log Adjacency Changes Detail | Auto Cost Reference Bandwidth | Maximum Paths | MPLS LDP Sync Default | Distribute List In |
| ---------- | --------- | ------------------------- | -------------------- | --- | ------- | ----------------------------- | ---------------------------- | ----------------------------- | ------------- | --------------------- | ------------------ |
| 10 | 11.11.11.11 | disabled |- | disabled | default | disabled | disabled | - | - | - | - |

#### OSPF Interfaces

| Interface | Area | Cost | Point To Point |
| -------- | -------- | -------- | -------- |
| Ethernet1 | 0 | - | True |
| Ethernet2 | 0 | - | True |
| Ethernet3 | 0 | - | True |

#### Router OSPF Device Configuration

```eos
!
router ospf 10
   router-id 11.11.11.11
```
