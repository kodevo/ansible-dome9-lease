# Ansible Role: dome9-lease

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-kodevo.dome9--lease-blue.svg)](https://galaxy.ansible.com/kodevo/dome9-lease/)
![Build Status](https://travis-ci.org/kodevo/ansible-dome9-lease.svg?branch=master)

Acquires a [Dome9](https://dome9.com) dynamic access lease via API v2.

## Requirements

None

## Role Variables

**dome9_lease**: A dictionary configuration for the lease to acquire.

* name (string) - The name of the lease.
* region (string) - AWS region of the security group: 'us_east_1', 'us_west_1', 'eu_west_1', 'ap_southeast_1', 'ap_northeast_1', 'us_west_2', 'sa_east_1', 'az_1_region_a_geo_1', 'az_2_region_a_geo_1', 'az_3_region_a_geo_1', 'ap_southeast_2', 'mellanox_region', 'us_gov_west_1', 'eu_central_1', 'ap_northeast_2'.
* sg (string) - AWS security group name (e.g. sg-123abc).
* ip (string) - Target IP of the lease.
* length (string) - Lease duration time in Timespan format, for example for 5 hours "5:0:0".
* protocol (string) - Internet protocol suite: 'HOPOPT', 'ICMP', 'IGMP', 'GGP', 'IPV4', 'ST', 'TCP', 'CBT', 'EGP', 'IGP', 'BBN_RCC_MON', 'NVP2', 'PUP', 'ARGUS', 'EMCON', 'XNET', 'CHAOS', 'UDP', 'MUX', 'DCN_MEAS', 'HMP', 'PRM', 'XNS_IDP', 'TRUNK1', 'TRUNK2', 'LEAF1', 'LEAF2', 'RDP', 'IRTP', 'ISO_TP4', 'NETBLT', 'MFE_NSP', 'MERIT_INP', 'DCCP', 'ThreePC', 'IDPR', 'XTP', 'DDP', 'IDPR_CMTP', 'TPplusplus', 'IL', 'IPV6', 'SDRP', 'IPV6_ROUTE', 'IPV6_FRAG', 'IDRP', 'RSVP', 'GRE', 'DSR', 'BNA', 'ESP', 'AH', 'I_NLSP', 'SWIPE', 'NARP', 'MOBILE', 'TLSP', 'SKIP', 'IPV6_ICMP', 'IPV6_NONXT', 'IPV6_OPTS', 'CFTP', 'SAT_EXPAK', 'KRYPTOLAN', 'RVD', 'IPPC', 'SAT_MON', 'VISA', 'IPCV', 'CPNX', 'CPHB', 'WSN', 'PVP', 'BR_SAT_MON', 'SUN_ND', 'WB_MON', 'WB_EXPAK', 'ISO_IP', 'VMTP', 'SECURE_VMTP', 'VINES', 'TTP', 'NSFNET_IGP', 'DGP', 'TCF', 'EIGRP', 'OSPFIGP', 'SPRITE_RPC', 'LARP', 'MTP', 'AX25', 'IPIP', 'MICP', 'SCC_SP', 'ETHERIP', 'ENCAP', 'GMTP', 'IFMP', 'PNNI', 'PIM', 'ARIS', 'SCPS', 'QNX', 'AN', 'IPCOMP', 'SNP', 'COMPAQ_PEER', 'IPX_IN_IP', 'VRRP', 'PGM', 'L2TP', 'DDX', 'IATP', 'STP', 'SRP', 'UTI', 'SMP', 'SM', 'PTP', 'ISIS', 'FIRE', 'CRTP', 'CRUDP', 'SSCOPMCE', 'IPLT', 'SPS', 'PIPE', 'SCTP', 'FC', 'RSVP_E2E_IGNORE', 'MOBILITY_HEADER', 'UDPLITE', 'MPLS_IN_IP', 'MANET', 'HIP', 'SHIM6', 'WESP', 'ROHC', 'ALL'.
* port_from and port_to (int) - Port range.
* note (string) - A comment for the lease displayed in dome9.

```
dome9_lease:
  action: acquire
  name: ssh
  region: us_east_1
  sg: sg-123abc
  length: 0:5:0
  protocol: TCP
  port_from: 22
  port_to: 22
  note: Temporary Access to Perform Maintenance Updates
```

##### See Also
* [Dome9 v2 API Documentation](https://github.com/Dome9/V2_API#aws-lease-create)

## Dome9 API Error Responses

The following are known error responses and possible solutions:

**500** Internal Server Error
* `Cannot Create Lease - No such AWS service`: The requested protocol and port range must be defined for the security group.

## Dependencies

None

## License

Apache 2

## Author Information

* [kodevo](https://github.com/kodevo) | [www](http://www.kodevo.com)
* [nslevkoff](https://github.com/nslevkoff)
