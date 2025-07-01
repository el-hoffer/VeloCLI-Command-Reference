#	--edge_cluster_table

##	Description
Dumps the edge cluster mapping table showing the association of VeloCloud Edges (VCEs) to their respective clusters.

##	Arguments (optional)
This command takes no arguments.

##	Example usage
```
example_com:velocli> debug --edge_cluster_table
VCE-ID                                                            ClusterId  Dir
8a8601b2-0086-4d06-a22f-5edefc37d339   891413b5-4fd7-417f-8efc-102aeb579df8  OUT
```

##	Field descriptions
| Column    | Description |
|-----------|-------------|
| VCE-ID    | Logical ID of the assigned VeloCloud Edge cluster member. |
| ClusterId | Logical ID of the destination cluster. |
| Dir       | Direction in which the tunnel was initiated (`IN` or `OUT`). |