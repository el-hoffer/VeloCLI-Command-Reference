#	--cluster_static_routes [[all | prefix] [all | segment-id] [all | v4 | v6]]

##	Description
Displays the static routes configured for a VeloCloud Edge cluster.

##  Arguments (optional)
| Argument     | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| `all`        | Shows all cluster static routes (default if no arguments are specified).    |
| `prefix`     | Filters the output to display routes matching a specific IP prefix.         |
| `segment-id` | Filters the output to display routes belonging to a specific segment ID.    |
| `v4`         | Displays only IPv4 cluster static routes.                                   |
| `v6`         | Displays only IPv6 cluster static routes.                                   |

If no arguments are provided, the command defaults to displaying all cluster static routes for all segments and both IPv4 and IPv6.

##  Example usage
```
example_com:velocli> debug --cluster_static_routes
Address          Netmask       Type  Gateway                           Next Hop ID                         Dst LogicalId  Metric  Preference  Flags   Vlan  Intf   MTU  SEG
80.1.3.0   255.255.255.0  edge2edge      any  0e045e96-2b89-4799-86f2-d7f1fc8466f9  0e045e96-2b89-4799-86f2-d7f1fc8466f9       0           0    DSR  65535   any  1500    0
80.1.2.0   255.255.255.0  edge2edge      any  0e045e96-2b89-4799-86f2-d7f1fc8466f9  0e045e96-2b89-4799-86f2-d7f1fc8466f9       0           0    DSR  65535   any  1500    0
P - PG, D - DCE, L - LAN SR, C - Connected, O - External, W - WAN SR, S - SecureEligible, R - Remote, s - self, r - recursive, H - HA, m - Management, v - ViaVeloCloud, A - RouterAdvertisement, c - CWS, a - RAS
```

##  Field descriptions
| Column        | Description                                                                                                |
|---------------|------------------------------------------------------------------------------------------------------------|
| Address       | The destination IP address for the static route.                                                           |
| Netmask       | The subnet mask for the destination IP address.                                                            |
| Type          | The type of the route. (i.e. N/A for local, edge2edge, etc.). |
| Gateway       | The gateway IP address or interface for the route (`any` for overlay routes).                              |
| Next Hop ID   | The logical ID of the next hop device or entity.                                                           |
| Dst LogicalId | The logical ID of the destination.                                                                         |
| Metric        | The metric value associated with the route, used in route selection.                                       |
| Preference    | The administrative distance or preference value for the route. Lower values are preferred.       |
| Flags         | Various flags indicating the properties or origin of the route. See the legend below for details.          |
| Vlan          | The VLAN ID associated with the route, if applicable.                                                      |
| Intf          | The destination interface of the route (`any` for overlay routes).                                         |
| MTU           | The Maximum Transmission Unit for the path associated with this route.                                     |
| SEG           | The Segment ID to which this route belongs.                                                                |

**Flags Legend:**
*   **P**: PG (Partner Gateway)
*   **D**: DCE (Hub edge routes)
*   **L**: LAN SR (LAN Static Route)
*   **C**: Connected (Directly connected network)
*   **O**: External OSPF route
*   **W**: WAN SR (WAN Static Route)
*   **S**: SecureEligible (Eligible for secure VeloCloud paths)
*   **R**: Remote (Route learned from a remote VeloCloud peer)
*   **s**: self (Route originated by the local Edge)
*   **r**: recursive (Recursive route, points to another route for resolution)
*   **H**: HA (High Availability related route)
*   **m**: Management (Management interface route)
*   **v**: ViaVeloCloud (cloud gateway route)
*   **A**: RouterAdvertisement (Learned via IPv6 Router Advertisement)
*   **c**: CWS (Cloud Web Security)
*   **a**: RAS (Remote Access Service)