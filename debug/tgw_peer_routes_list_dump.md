# --tgw_peer_routes_list_dump [[all | prefix] [all | segment-id]]

## Description
This command dumps the list of TGW (Transit Gateway) Connect Peer Routes known by the VeloCloud Edge. TGW peer routes are used for peering with an AWS Transit Gateway.

## Arguments
The command requires two positional arguments:

| Argument     | Description                                                                                                                               |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `all`        | When used as the first argument, displays routes for all prefixes. When used as the second argument, displays routes for all segment IDs. If no arguments are provided, `all` is assumed for both. |
| `prefix`     | As the first argument, specifies a network prefix (e.g., `192.168.1.0/24` or `2001:db8::/32`) to filter the TGW peer routes.                 |
| `segment-id` | As the second argument, specifies a segment ID (e.g., `1`, `0`) to filter the TGW peer routes.                                            |

## Example usage

```
example_com:velocli> debug --tgw_peer_routes_list_dump all 1
Address                              NSD Logical ID  Intf  SEG
169.254.22.2   ca89004f-dd25-41ba-8c90-58d404a9eb1f  nvs0    1
169.254.22.3   ca89004f-dd25-41ba-8c90-58d404a9eb1f  nvs0    1
```
## Field descriptions
| Column | Description |
|---|---|
| `Address`  | TGW peer address |
| `NSD Logical ID` | Logical ID of the NSD used to establish the GRE tunnel to the TGW Connect Peer |
| `Intf` | NSD interface name |
| `SEG` | Numerical segment ID |