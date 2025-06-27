#	--dce_edge [v4 | v6 | all]

##	Description
Displays a list of hub edges configured on an edge along with details about WAN overlay connectivity.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `v4` | Display only IPv4 address information for the DCE edges. |
| `v6` | Display only IPv6 address information for the DCE edges. |
| `all` | Display both IPv4 and IPv6 address information (if available) for the DCE edges. This is the default behavior if no argument is specified. |

##  Example usage
```
example_com:velocli> debug --dce_edge
DCE LogicalId                                                                   V4 Address  V6 Address  Peer Tun Pref  Private  Type  VCMP Port  IKE Port  NAT-t Port  MPLS Network
891413b5-4fd7-417f-8efc-102aeb579df8:e4562bf3-6489-44ca-9c75-235729a152a1   20.118.207.159    NotAvlbl             V4       no   DCE       2426       500        4500             0
2e56aa7a-6f8b-4802-a2d1-3be3f97387ae:e1330e2d-632c-40af-8e54-64544ac41647   18.224.248.106    NotAvlbl             V4       no   DCE       2426       500        4500             0
```

##  Field descriptions
| Column | Description |
|---|---|
| DCE LogicalId | The unique logical identifier of the remote DCE. |
| V4 Address | The IPv4 address of the remote DCE link. |
| V6 Address | The IPv6 address of the remote DCE link. |
| Peer Tun Pref | Peer Tunnel Preference. Indicates whether IPv4 or IPv6 is configured as preferred for establishing tunnels to this peer. |
| Private | Indicates if the DCE is on a private network or uses private IP addressing. |
| Type | The type or role of the DCE. |
| VCMP Port | The VeloCloud Management Protocol (VCMP) port number used by the DCE for management communications. |
| IKE Port | The Internet Key Exchange (IKE) port number used by the DCE for establishing IPSec tunnels. |
| NAT-t Port | The NAT Traversal port number used by the DCE for IPSec tunnels when Network Address Translation (NAT) is detected. |
| MPLS Network | Identifier or information related to an MPLS network associated with the DCE, if applicable. |