#	--add_routes [path to input routes json]

##	Description
This command allows a user to inject Border Gateway Protocol routes directly into the VeloCloud Edge's Routing Information Base (RIB) and subsequently into the Forwarding Information Base (FIB). The routes to be added are specified in a JSON formatted file. This functionality is intended for debugging, testing specific routing scenarios, or simulating BGP learned routes without requiring an active BGP peering session in non-production environments.

##	Arguments
| Argument | Description |
|---|---|
| `[path to input routes json]` | **Required.** The full filesystem path to a JSON file containing the definitions of the BGP routes to be added. The file must be accessible by the VeloCloud Edge. |

## JSON File Format
The input JSON file must contain an array of route objects. Each object in the array represents a single route and should define its attributes as follows:

```json
{
    "routes": [
        {
            "next_hop_id": "14eef8f6-5ff3-41d9-a625-474a5e6c6e38",
            "dst_id": "14eef8f6-5ff3-41d9-a625-474a5e6c6e38",
            "segment_id": 1,
            "network_addr": "10.132.0.0",
            "netmask": "255.255.255.248"
        },
        {
            "next_hop_id": "14eef8f6-5ff3-41d9-a625-474a5e6c6e38",
            "dst_id": "14eef8f6-5ff3-41d9-a625-474a5e6c6e38",
            "segment_id": 1,
            "network_addr": "10.132.0.8",
            "netmask": "255.255.255.248"
        }
    ]
}
```

##	Example Usage
To add BGP routes defined in a file named `my_custom_routes.json` located in the `/tmp/` directory on the VeloCloud Edge:
```
example_com:velocli> debug --add_routes /tmp/my_custom_routes.json
```

##	Field Descriptions
This command does not produce any output.