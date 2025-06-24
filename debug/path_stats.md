#	--path_stats

##	Description
List all of the tunnels with other SDWAN edges and gateways

##  Arguments
None

##  Example usage
```
example_com:velocli> debug --path_stats
Interface   VLAN  prio8021P      PeerName                           PublicIpAddr           PeerIpAddr  TunnelingMode     Version  Path State  RxState  TxState  AvgLatencyRx  AvgLatencyTx  RxJitter  TxJitter  lossRx  lossTx  MeasuredRateRx  MeasuredRateTx  dynamicBwRx  dynamicBwTx  RemoteRx  HeartbeatIntervalMs   MTU  Dynamic  Dir  Overhead  DynAbort  LocalGateway
GE5         NONE       NONE    vcg88-ord1                          75.231.53.240        216.221.27.88        DEFAULT  3728705529      ACTIVE   STABLE   STABLE            11            22       2.5       1.0     0.0     0.0          185455           21342       185455        21342     21342                  100  1408       No  OUT         0         1             1
GE6         NONE       NONE    vcg88-ord1  2602:4b:a8c4:9d00:a2ad:9957:8555:890b  2605:a7c0:1:301::88        DEFAULT  2488699796      ACTIVE   STABLE   STABLE            14            13       0.0       0.0     0.0     0.0           38952           19009        38952        19009     19009                  100  1408       No  OUT         0         1             1
GE5         NONE       NONE     AzurevWAN                          75.231.53.240        20.46.246.159        DEFAULT  3805857946      ACTIVE   STABLE   STABLE            18            18       1.5       9.0     0.0     0.0          185455           21342      1509400        21342   3621845                  500  1408       No  OUT         0         1             0
GE6         NONE       NONE     AzurevWAN                         75.168.196.157        20.46.246.159        DEFAULT  2473060710      ACTIVE   STABLE   STABLE            16            15       0.0       0.0     0.0     0.0           38952           19009      1509400        19009   3621845                  100  1408       No  OUT         0         1             0
GE5         NONE       NONE    vcg44-dfw1                          75.231.53.240        216.221.31.44        DEFAULT   420843191      ACTIVE   STABLE   STABLE            20            31       1.5       6.0     0.0     0.0          185455           21342       185455        21342     21342                  500  1408       No  OUT         0         1             0
GE6         NONE       NONE    vcg44-dfw1  2602:4b:a8c4:9d00:a2ad:9957:8555:890b  2605:a7c0:3:301::44        DEFAULT  2493654468      ACTIVE   STABLE   STABLE            22            21       0.0       0.0     0.0     0.0           38952           19009        38952        19009     19009                  500  1408       No  OUT         0         1             0
GE5         NONE       NONE  ARS-Branch-1                          75.231.53.240        40.122.238.58        DEFAULT  3245973656      ACTIVE   STABLE   STABLE             0             0       0.0       0.0     0.0     0.0          185455           21342      1182716        21342   2194236                  100  1408      Yes   IN         0         1             0
GE6         NONE       NONE  ARS-Branch-1                         75.168.196.157        40.122.238.58        DEFAULT  3245972410      ACTIVE   STABLE   STABLE             0             0       0.0       0.0     0.0     0.0           38952           19009      1182716        19009   2194236                  100  1408      Yes   IN         0         1             0

```

##  Field descriptions
| Column | Description |
|---|---|
| Interface | Edge interface on which the tunnel is established |
| VLAN | 802.1Q VLAN tag configured either on the parent inteface or as a "custom VLAN" in the optional configuration section of a user defined overlay  |
| prio8021P | 802.1p PCP value set on ethernet frames leaving the interface.  This capability is disabled at the VCO level by default so will generally be "NONE" |
| PeerName | Friendly name of the peer edge or gateway  |
| PublicIpAddr | Routable IP address of the edge interface on which the tunnel is built (can differ from the configured interface IP in cases of public links where the edge sits behind a NAT device) |
| PeerIpAddr | Routable IP address of the peer edge or gateway to which the tunnel is built |
| TunnelingMode |  |
| Version | Version number assigned to the path upon successful establishment of the tunnel with peer |
| Path State | Current status of the path (ACTIVE, HOTSTANDBY_IDLE, HOTSTANDBY_UP, or BACKUP) |
| RxState | Performance status of the path from peer to edge (UNKNOWN, STABLE, UNSTABLE, QUIET, INITIAL, or STANDBY) |
| TxState | Performance status of the path from edge to peer (UNKNOWN, STABLE, UNSTABLE, QUIET, INITIAL, or STANDBY) |
| AvgLatencyRx | Average one way latency from peer to edge in milliseconds |
| AvgLatencyTx | Average one way latency from edge to peer in milliseconds |
| RxJitter | One way jitter as measured from peer to edge |
| TxJitter | One way jitter as measured from edge to peer |
| lossRx | Percentage of one-way packet loss measured from peer to edge |
| lossTx | Percentage of one-way packet loss measured from peer to edge |
| MeasuredRateRx | Tunnel throughput negotiated from peer to edge in kbps |
| MeasuredRateTx | Tunnel throughput negotiated from edge to peer in kbps |
| dynamicBwRx | Useable bandwidth from peer to edge as detected by Dynamic Bandwidth Adjustment |
| dynamicBwTx | Useable bandwidth from edge to peer as detected by Dynamic Bandwidth Adjustment |
| RemoteRx | Measured RX bandwidth on the best path of he peer edge's link |
| HeartbeatIntervalMs | Interval in milliseconds at which heartbeat probes will be sent to the peer in the absence of user traffic |
| MTU | MTU used for the tunnel, derived as described in the [Tunnel Overhead and MTU](https://techdocs.broadcom.com/us/en/vmware-sde/velocloud-sase/vmware-velocloud-sd-wan/6-2/sd-wan-administration-guide/overview-3-admin/tunnel-overhead-and-mtu-admin.html) section of the admin guide. |
| Dynamic | Indicates whether a tunnel is dynamic (Yes) or static (No) |
| Dir | Direction in which the tunnel was initiated (OUT if tunnel was initiated by the local edge, IN if the peer initiated the tunnel) |
| Overhead | Overhead bytes configured on the link to account for additional encapsulation applied by upstream WAN devices |
| DynAbort | Value of '0' indicates that Dynamic Bandwidth Adjustment is enabled for the link.  Value of '1' indicates that Dynamic Bandwidth Adjustment is disabled for the link. |
| LocalGateway | Value of '1' indicates that the peer is the edges primary gateway. Value is '0' for other edges/gateways |
