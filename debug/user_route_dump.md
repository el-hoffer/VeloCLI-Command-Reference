#	--user_route_dump [all|segment] [all|v4|v6] [all|prefix] [all|preferred]

##	Description
Displays user-configured routes, primarily intended for remote diagnostic purposes. This command allows for filtering the route dump based on segment, IP version (IPv4 or IPv6), specific network prefixes, and route preference. When filtering by preference, selecting `preferred` will show only the best reachable route, or the first unreachable route if none are reachable. Selecting `all` for preference will display all routes matching the other filters. This command is often used in remote diagnostic procedures to inspect the routing table.

##  Arguments (optional)
If an argument is not specified, it defaults to `all`.

| Argument Description | Position | Values | Default | Details |
|---|---|---|---|---|
| Segment filter | 1st | `all` \| `segment-id` | `all` | Specifies the segment for which to display routes. Use `all` for all segments or provide a specific segment ID. |
| IP version filter | 2nd | `all` \| `v4` \| `v6` | `all` | Filters routes by IP version. `all` for both IPv4 and IPv6, `v4` for IPv4 only, `v6` for IPv6 only. |
| Prefix filter | 3rd | `all` \| `prefix` | `all` | Filters routes by a specific network prefix (e.g., `192.168.1.0/24`). Use `all` to display routes for all prefixes. |
| Preference filter | 4th | `all` \| `preferred` | `all` | Determines which routes to display based on their preference and reachability: <br> - `all`: Dumps all routes matching the other filters. <br> - `preferred`: Dumps only the best reachable route. If no reachable routes exist for a given prefix, the first unreachable route is dumped. |

##  Example usage
The following example shows how to invoke the command without any specific filters, which will default to displaying all routes for all segments, IP versions, and prefixes.
```
example_com:velocli> debug --user_route_dump 1 all 10.55.55.1 all
{
  "segment": [
    {
      "id": 1,
      "name": "Lab",
      "routes": [
        {
          "addr": "10.55.55.1",
          "cost": 100,
          "dst_id": "3294602a-5a69-4694-a7d2-811aff737faa",
          "dst_name": "vNET Peer Test",
          "lost_reason": "LR_NO_ELECTION",
          "netmask": "255.255.255.255",
          "next_hop": "Cloud VPN",
          "nh_id": "3294602a-5a69-4694-a7d2-811aff737faa",
          "nh_name": "vNET Peer Test",
          "order": 0,
          "preference": 0,
          "reachable": 1,
          "rt_reachable_reason": "PR_REACHABLE",
          "segment_id": 1,
          "type": "Edge"
        },
        {
          "addr": "10.55.55.1",
          "cost": 100,
          "dst_id": "ca89004f-dd25-41ba-8c90-58d404a9eb1f",
          "dst_name": "N/A",
          "lost_reason": "LR_CONN_STATIC_VS_NSD_BGP",
          "netmask": "255.255.255.255",
          "next_hop": "Cloud VPN",
          "nh_id": "ca89004f-dd25-41ba-8c90-58d404a9eb1f",
          "nh_name": "N/A",
          "order": 0,
          "preference": 1000000,
          "reachable": 1,
          "rt_reachable_reason": "PR_REACHABLE",
          "segment_id": 1,
          "type": "Non-VeloCloud Site"
        }
      ]
    }
  ]
}
```

##  Field descriptions
The output is in JSON format, structured as follows:

| Field     | Description                                                                                                                                                                                             |
|-----------|-----------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `segment` | An array of segment objects, where each object represents a configured network segment on the VeloCloud Edge.  |
| `id`      | The numerical identifier of the segment. For example, `0` typically represents the "Global Segment".  |
| `name`    | The descriptive name of the segment (e.g., "Global Segment", "Corporate Segment").   |
| `routes`  | An array of route objects specific to this segment. Each route object contains detailed information about the route. |
| `addr`  | IP prefix of the route entry |
| `cost` | Calculated cost of the route (lower is more preferred) |
| `dst_id` | UUID of the destination peer edge, gateway, or NSD |
| `dst_name` | Friendly name of the destination peer (`N/A` for LAN and NSD via edge routes) |
| `lost_reason` | Reason for route being preferred or not (`LR_NO_ELECTION` indicates that the route is preferred, otherwise the reason code indicates why it lost the election process) |
| `netmask` | Subnet mask of the prefix |
| `next_hop` | Next hop specified by the route (destination interface for LAN routes, or overlay route type i.e. `Cloud VPN` or `Cloud Gateway`) |
| `nh_id` | UUID of the next hop peer or NSD (`N/A` for LAN routes) |
| `nh_name` | Friendly name of the next hop peer edge or gateway (`N/A` for LAN and NSD routes) |
| `order` | Route order flag value |
| `preference` | Route preference value (lower values are more preferred) |
| `reachable` | Reachable flag of `1` when the route is reachable or `0` for routes marked unreachable. |
| `rt_reachable_reason` | Reason flag indicating why a route is reachable or unreachable |
| `segment_id` | Numeric ID of the segment in which the route exists |
| `type` | Route type flag (i.e. `Edge`, `Non-VeloCloud Site`, `Static`, `Connected`, etc.) |
