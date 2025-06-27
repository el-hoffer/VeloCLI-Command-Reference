#	--show_edge_wss_conf

##	Description
Displays the current Web Security Service (WSS) configuration for the VeloCloud Edge. WSS is used for PoP to PoP integration at the VeloCloud Gateway with Cloud Security Services (CSS), such as Symantec, for securing internet-bound traffic. This command allows administrators to verify the WSS settings applied to the Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| None | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --show_edge_wss_conf
[
  {
    "location": {
      "logicalId": "00000000-0000-0000-0000-000000000000",
      "vni": 12555342
    },
    "logicalId": "aaefbda9-116b-471f-8afc-db0842da729",
    "name": "Symantec WSS Test",
    "segmentId": 0
  }
]
```

##  Field descriptions
| Column | Description |
|---|---|
| `location.logicalId` | UUID of the of the WSS gateway PoP |
| `location.vni` | Geneve VNI used in gateway handoff to the WSS provider. |
| `logicalId` | UUID of the WSS SSE instance |
| `name` | Name of the WSS SSE instance |
| `segmentId` | Segment in which the WSS instance is configured |