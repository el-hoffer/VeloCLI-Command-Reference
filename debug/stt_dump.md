#	--stt_dump [all | <transit_log_id>]

##	Description
This command dumps SoR Transit Tracking (STT) entries. STT entries provide information about the state and characteristics of hub cluster interconnect transit nodes.  Outputs are similar to those of the `--sor_dump` command, however this offers the ability to filter based on specific transit nodes as opposed to the destination node.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | Displays all entries in the Secure Tunnel Table. This is often the default behavior if no argument is specified. |
| `<transit_log_id>` | Filters the output to display STT entries associated with a specific transit node. This allows for targeted troubleshooting of particular paths. |

##  Example usage
```
example_com:velocli> debug --stt_dump
Entr_ID            Transit_ID        Node_ID        Cluster     Profile_ID  Reachable  Metric  Uturn                  ToC                  ToU
4d56b0e0-32a0   891413b5-4fd7  8d9d0de3-3913  891413b5-4fd7  dd24577d-a953          Y       2      Y  2025-06-30T15:38:22  2025-06-30T15:38:22
4d56b0e0-32a0   891413b5-4fd7  3294602a-5a69  891413b5-4fd7  dd24577d-a953          Y       2      Y  2025-06-30T15:38:22  2025-06-30T15:38:22
4d56b0e0-32a0   891413b5-4fd7  14f68955-b788  891413b5-4fd7  dd24577d-a953          Y       2      Y  2025-06-30T15:38:28  2025-06-30T15:38:28
4d56b0e0-32a0   e1330e2d-632c  82354916-b421  2e56aa7a-6f8b  00000000-0000          Y       1      N  2025-06-30T15:38:23  2025-06-30T15:38:23
4d56b0e0-32a0   e1330e2d-632c  3294602a-5a69  2e56aa7a-6f8b  00000000-0000          Y       1      N  2025-06-30T15:38:23  2025-06-30T15:38:23
4d56b0e0-32a0   e1330e2d-632c  8d9d0de3-3913  2e56aa7a-6f8b  00000000-0000          Y       1      N  2025-06-30T15:38:23  2025-06-30T15:38:23
```

##  Field descriptions
| Column | Description |
|---|---|
| `Entr_ID` | Logical ID of the enterprise. |
| `Transit_ID` | Transit Identifier: An identifier for the transit node associated with this entry. This can correlate with the `<transit_log_id>` argument. |
| `Node_ID` | Logical ID of the destination VeloCloud peer Edge. |
| `Cluster` | Logical ID of the cluster through which the node is reached (may be the local cluster of the edge on which the command is run for direct nodes). |
| `Profile_ID` | The configuration profile ID associated with the relayed peer node (not required for direct nodes as information for those is exchanged in peer to peer VCMP messaging). |
| `Reachable` | Reachability Status: A boolean (True/False) or similar indicator showing whether the peer node is currently considered reachable. |
| `Metric` | Path Metric indicating the overlay hop count.  Values start at `1` for directly connected routes and are incremented by the number of intermediate hubs/clusters.  From a routing standpoint, when multiple paths are all either Direct or Relayed, the metric is used as a tie breaker with lower metrics being preferred. |
| `Uturn` | Indicates whether relaying clusters require intra-cluster hops (U-Turn through the LAN) to reach the destination node. |
| `ToC` | Time of Creation: Timestamp indicating when this SoR entry was created.  From a routing standpoint if both direct/relayed and metric flags are identical, the time of creation is used as a tie breaker with the first learned entry being the most preferred. |
| `ToU` | Time of Update: Timestamp indicating when this SoR entry was last updated. |