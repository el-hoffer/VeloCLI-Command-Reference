#	--sor_dump [all | <node_id>]

##	Description
The `debug --sor_dump` command is used to display entries from the Source of Reachability (SoR) table in edges where the Hub/Cluster Interconnect feature is enabled. The SoR maintains state information about various nodes and paths within the VeloCloud SD-WAN fabric. This information is crucial for routing decisions and understanding the topology from the perspective of the VeloCloud Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | Displays all entries in the SoR table. This is the default behavior if no argument is specified. |
| `<node_id>` | Displays SoR entries specifically related to the given Node ID. The Node ID refers to another VeloCloud Edge. |

##  Example usage
```
example_com:velocli> debug --sor_dump
Entr_ID               Node_ID        Transit        Cluster     Profile_ID  D/R  Reachable  Metric  Uturn                  ToC                  ToU  Uturn_Transit_Count
4d56b0e0-32a0   8d9d0de3-3913  e1330e2d-632c  2e56aa7a-6f8b  00000000-0000    D          Y       1      N  2025-06-30T15:38:23  2025-06-30T15:38:23                    0
4d56b0e0-32a0   8d9d0de3-3913  891413b5-4fd7  891413b5-4fd7  dd24577d-a953    R          Y       2      Y  2025-06-30T15:38:22  2025-06-30T15:38:22                    2
4d56b0e0-32a0   82354916-b421  e1330e2d-632c  2e56aa7a-6f8b  00000000-0000    D          Y       1      N  2025-06-30T15:38:23  2025-06-30T15:38:23                    0
4d56b0e0-32a0   14f68955-b788  891413b5-4fd7  891413b5-4fd7  dd24577d-a953    R          Y       2      Y  2025-06-30T15:38:28  2025-06-30T15:38:28                    2
4d56b0e0-32a0   3294602a-5a69  e1330e2d-632c  2e56aa7a-6f8b  00000000-0000    D          Y       1      N  2025-06-30T15:38:23  2025-06-30T15:38:23                    0
4d56b0e0-32a0   3294602a-5a69  891413b5-4fd7  891413b5-4fd7  dd24577d-a953    R          Y       2      Y  2025-06-30T15:38:22  2025-06-30T15:38:22                    2
```

##  Field descriptions
| Column | Description |
|---|---|
| Entr_ID | Logical ID of the enterprise. |
| Node_ID | Logical ID of the destination VeloCloud peer Edge. |
| Transit | Logical ID of the transit node |
| Cluster | Logical ID of the cluster through which the node is reached (may be the local cluster of the edge on which the command is run for direct nodes). |
| Profile_ID | The configuration profile ID associated with the relayed peer node (not required for direct nodes as information for those is exchanged in peer to peer VCMP messaging). |
| D/R | Direct/Relayed: Indicates if the originating node is directly connected via the overlay or reached via intermediate relaying node(s).  From a routing standpoint direct paths are more preferred than relayed. |
| Reachable | Reachability Status: A boolean (True/False) or similar indicator showing whether the peer node is currently considered reachable. |
| Metric | Path Metric indicating the overlay hop count.  Values start at `1` for directly connected routes and are incremented by the number of intermediate hubs/clusters.  From a routing standpoint, when multiple paths are all either Direct or Relayed, the metric is used as a tie breaker with lower metrics being preferred. |
| Uturn | Indicates whether relaying clusters require intra-cluster hops (U-Turn through the LAN) to reach the destination node. |
| ToC | Time of Creation: Timestamp indicating when this SoR entry was created.  From a routing standpoint if both direct/relayed and metric flags are identical, the time of creation is used as a tie breaker with the first learned entry being the most preferred. |
| ToU | Time of Update: Timestamp indicating when this SoR entry was last updated. |
| Uturn_Transit_Count | Count of intra-cluster U-Turns in path to the destination node. |