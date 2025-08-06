#	--de2e_print [v4 | v6 | all]

##	Description
Dumps the list of VeloCloud Edge IDs (VCEIDs) that have active dynamic edge-to-edge (DE2E) tunnels with the local Edge. This command provides details about these direct tunnels, including peer information and traffic statistics. DE2E allows Edges to dynamically build tunnels to other peer Edges when applicable user traffic is detected.

##	Arguments (optional)
| Argument | Description |
|---|---|
| `v4` | Display DE2E tunnels established using IPv4. |
| `v6` | Display DE2E tunnels established using IPv6. |
| None or `all` | Display all DE2E tunnels, regardless of IP version (both IPv4 and IPv6). |

##	Example Usage
```
example_com:velocli> debug --de2e_print
{'debug': 'de2e_dump', 'ipversion': 0}
Peer                                       Name  Initiator      Now  Last Update  Rx Bytes  Rx Bytes Last  Tx Bytes  Tx Bytes Last
82354916-b421-4c48-b3b5-6e0a06795804   Home-620          1  5442380      5442372         0              0         0              0

```

##	Field Descriptions
| Column | Description |
|---|---|
| `Peer` | The logical ID of the remote VeloCloud Edge participating in the DE2E tunnel. |
| `Name` | The configured name of the remote VeloCloud Edge. |
| `Initiator` | Indicates whether the local Edge initiated the DE2E tunnel to this peer (1 = yes, 0 = no). |
| `Now` | Current timestamp indicating the number of seconds of uptime for the edge. |
| `Last Update` | Timestamp of the last tunnel state change for this DE2E tunnel. |
| `Rx Bytes` | Total number of bytes received from the peer over this DE2E tunnel since it was established or since counters were last reset. |
| `Rx Bytes Last` | Number of bytes received from the peer during the last measurement or reporting interval. |
| `Tx Bytes` | Total number of bytes transmitted to the peer over this DE2E tunnel since it was established or since counters were last reset. |
| `Tx Bytes Last` | Number of bytes transmitted to the peer during the last measurement or reporting interval. |