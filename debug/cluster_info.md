#	--cluster_info

##	Description
Displays information about the VeloCloud Edge's clustering status. Clustering is typically used for High Availability (HA) configurations, where two Edges operate as a redundant pair to ensure network continuity. This command provides insights into the current state of such a cluster, if configured.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
The following example shows the output when clustering is not enabled on the Edge:
```
example_com:velocli> debug --cluster_info
{
  "Error": "Clustering disabled"
}

example_com:velocli>
```
If clustering were enabled, the output would provide details about the cluster's state, members, and other relevant HA information.

##  Field descriptions
The output is in JSON format. The fields displayed will vary depending on whether clustering is enabled and the current state of the cluster.
| Field | Description |
|---|---|
| Error | If present, this field indicates an error condition or a specific status, such as "Clustering disabled" if the HA feature is not active or configured on the Edge. |
| *(other fields)* | When clustering is enabled and operational, various other fields will be present. These can include, but are not limited to: cluster ID, role (e.g., active, standby), peer information, state, last state change, and synchronization status. The specific set of fields provides a comprehensive overview of the HA cluster's health and configuration. |